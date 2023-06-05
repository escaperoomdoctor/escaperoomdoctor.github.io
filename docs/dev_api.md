# QUEEN API for developers

This article describes the interface for interacting with the QUEEN system.

## Connecting to the Queen Room

Connection to the _Queen Room_ system is carried out through a regular TCP socket, i.e. _Queen Room_ opens a listening socket (by default on _0.0.0.0:4444_) and waits for subscribers to connect.
The address _0.0.0.0:4444_ can be changed in the project properties (project -> server).
It is possible to connect to the Queen Room using a regular terminal, for example, [PuTTY](https://www.putty.org) with "Raw" socket parameters.
In general, you can connect to _Queen Room_ using any program using a command management interface with an open format: the input is a string command, and the output is an XML document.  

!> For the correct operation of the _PuTTY_ terminal, it is advisable to check the "Implicit CR in every LF" checkbox in the "Terminal" settings.

The general format of pseudocode commands looks like this: `getsmth` or `setsmth`. The server responds to any commands as follows:

```xml
<response type='getsmth' id='id' status='ok/error' time='HH:MM:SS.MS'>TEXT</response>
```

- **type** - repeats the request;
- **id** - request identifier;
- **status** - status of the request, if successful, the request is equal to `ok`, and in case of an error - `error`;
- **time** - if the script is running, then this is the time of the script in the format HH:MM:SS.MS (hours, minutes, seconds and tenths of a second), if the script is not running or the request does not imply a time in the response, then either not specified, or `-`.
- **TEXT** - contains either the error string if `status='error'` or the result of the response itself if `status='ok'`.

The identifier is set at the very beginning of the request in square brackets. For example, if the command `[2467]getstates` (get the current states of the electronics) is given, then in response to such a command _Queen Room_ will set the attribute `id='2467'`.
If there is no request identifier in the command, for example, just `getstates`, then _Queen Room_ will set `id='undefined'`.  

## Get static states (STATIC)

Here will be listed commands that receive data from _Queen Room_ without performing any control actions.
These commands will henceforth be called **STATIC** and must be called once when establishing a connection with _Queen Room_, as they return the same result.

### Getting the file structure

Format: `getfs [filter]`

Command examples:

| Example                        | Description              |
|--------------------------------|--------------------------|
| **getfs** \*.\*                | get the entire file tree |
| **getfs** \*.mp3,\*.wav,\*.ogg | get all sound files      |
| **getfs** \*.mef               | get all macro effects    |

In response to this command, _Queen Room_ will send a tree of files and directories relative to the location of _Queen Room_ and deeper in XML format.
Answer example: 

```xml
<response type='getfs' status='ok'>  
  <folder name='.'>  
    <folder name='macroeffects'>  
      <file name='lose.mef'/>  
      <file name='tune.mef'/>  
      <file name='win.mef'/>  
    </folder>  
    <folder name='media'>  
      <folder name='img'>  
      </folder>  
      <folder name='snd'>  
        <file name='sound check.mp3'/>  
      </folder>  
    </folder>  
    <folder name='scenarios'>  
      <file name='scenario.xml'/>  
    </folder>  
    <file name='room.xml'/>  
    <file name='queen_room'/>  
  </folder>  
</response>  
```

The entire file tree is represented as a structure of folders (the `<folder>` tag) and files (the `<file>` tag). Nesting of `<folder>` tags defines the hierarchy of folders.

### Getting the room description file room.xml

Format: `getroom`

Command examples:

| Example     | Description       |
|-------------|-------------------|
| **getroom** | get room.xml file |


In response to this command, _Queen Room_ will send _room.xml_ in XML format, attaching _room.xml_ to the `<response>` tag:

```xml
<response type='getroom' status='ok'>
    <...room.xml...>
</response>
```

### Getting the script tree

Format: `getscripts`

Command examples:

| Example        | Description     |
|----------------|-----------------|
| **getscripts** | get script tree |

In response to this command, _Queen Room_ will send a script tree in XML format:

```xml
<response type='getscripts' status='ok'>  
  <macro name='m1.mef'></macro>
  <macro name='m2.mef'></macro>
  <macro name='m3.mef'></macro>
  <macro name='m4.mef'></macro>
  <macro name='m5.mef'></macro>
  <...other_macros...>
  <scenario name='scenario_1.xml' begin='stage_1'>
    <stage name='global'></stage>
    <stage name='stage_1' next='stage_2'></stage>
    <stage name='stage_2' next='stage_3'></stage>
    <...other_stages...>
    <stage name='stage_N' next=''></stage>
  </scenario>
  <...other_scenarios...>
</response>

```

First, there is a listing of all macro effects for a given project (the `<macro>` tag). Each macro effect contains the attribute `name` - the name of the macro effect (file name without extension).
The following lists all scenarios in `<scenario>` tags. Each script contains a `name` attribute - the name of the script (the script file name without extension) and the name of the initial stage (the `begin` attribute).
Within a script, all stages are listed in `<stage>` tags, each with a name (the `name` attribute) and a pointer to the next stage (the `next` attribute).
Each stage, including the global one, contains an enumeration of context hints in `<clue>` tags, and the `macro` attribute refers to the corresponding macro effect.
Since a hint is a macro effect, technically anything can be a hint: from flashing a light and playing a sound, to complex effects with text prompts on _Queen TV_.

## Getting dynamic states (DYNAMIC)

This will list commands that receive data from _Queen Room_ without taking any control actions.
These commands will henceforth be called **DYNAMIC** and should be called periodically after establishing a connection with _Queen Room_ in order to get the current states of various objects.

### Getting a program response (ping)

Format: `ping`

Command examples:

| Example  | Description  |
|----------|--------------|
| **ping** | get feedback |

In response to this command, _Queen Room_ will send the following XML:  

```xml
<response type='ping' status='ok'></response>  
```

This command is just needed to check the connection with _Queen Room_.

### Getting the state of room objects

Format: `get [type.object.attribute]`

Command examples:

| Example                       | Description                                                                                       |
|-------------------------------|---------------------------------------------------------------------------------------------------|
| **get** din.startbutton.state | get the state of the discrete input for the button "startbutton"                                  |
| **get** out.cachelock.state   | get the state of the discrete output (relay) of the electromagnetic lock of the "cachelock" cache |
| **get** ain.photosensor.state | get the state of the analog input of the sensor "photosensor"                                     |
| **get** pwm.led.state         | get the state of brightness (PWM signal) of the lamp "led"                                        |
| **get** pwm.led.strobo        | get the state of the strobe flag (PWM signal) of the "led" lamp                                   |
| **get** uni.rfid1.state       | get state of uni-object of proximity sensor "rfid1"                                               |
| **get** var.somevar.state     | get state of variable "somevar"                                                                   |

In response to this command, _Queen Room_ will send the states of the room object in XML format, examples:  

```xml
<response type='get din.startbutton.state' status='ok'>on</response>  

<response type='get out.cachelock.state' status='ok'>off</response>

<response type='get ain.photosensor.state' status='ok'>980</response>

<response type='get pwm.led.state' status='ok'>255</response>  

<response type='get pwm.led.strobo' status='ok'>high</response>  

<response type='get uni.rfid1.state' status='ok'>236728347</response> 
```

If the command is incorrect, an error message will be sent.

### Getting the state of all room objects

Format: `getstates`

Command examples:

| Example       | Description                    |
|---------------|--------------------------------|
| **getstates** | get states of all room objects |

In response to this command, _Queen Room_ will send the states of all objects in the room in XML format: 

```xml
<response type='getstates' status='ok'>
  <item type='pwm' obj='pwm1' attr='state' value='128'/>
  <item type='out' obj='out1' attr='state' value='on'/>
  <...>
</response>
```

### Getting the state of the current mode and stage

Format: `getmode`

Command examples:

| Example     | Description                                 |
|-------------|---------------------------------------------|
| **getmode** | get the state of the current mode and stage |

In response to this command, _Queen Room_ will send the state of the current mode and stage in XML format, examples:

```xml
<response type='getmode' status='ok'>idle</response>

<response type='getmode' status='ok'>tune</response>

<response type='getmode' status='ok'>ready</response>

<response type='getmode' status='ok'>win</response>

<response type='getmode' status='ok'>lose</response>

<response type='getmode' status='ok'>godmode:stage</response>

<response type='getmode' status='ok'>playing:stage</response>

<response type='getmode' status='ok'>paused:stage</response>
```

The modes are listed above:
- **idle** - simple (quest in manual mode, script disabled);
- **tune** - recharge;
- **ready** - script readiness;
- **win** - the quest is over in a state of victory;
- **lose** - the quest ended in a state of defeat.

The following are three modes that describe the game modes through the ":" delimiter, indicating the current stage of the scenario, where
- **godmode** - god mode (time doesn't pass, but everything works);
- **playing** - normal script playback mode with reverse timer;
- **paused** - game pause mode, where everything seems to "freeze";
- **stage** - name of the current stage.

## Control commands (CONTROL)

This will list the commands that control the states of _Queen Room_. These commands will henceforth be referred to as **CONTROL**.

### Setting the value of variables and electronic objects

Format: `set [type.object.attribute] [value]`
Command examples:

| Example                               | Description                                                                                       |
|---------------------------------------|---------------------------------------------------------------------------------------------------|
| **set** din.startbutton.state **on**  | set the state of the discrete input for the button "startbutton"                                  |
| **set** out.cachelock.state **off**   | set the state of the discrete output (relay) of the electromagnetic lock of the "cachelock" cache |
| **set** ain.photosensor.state **980** | set the state of the analog input of the sensor "photosensor"                                     |
| **set** pwm.led.state **255**         | set the state of brightness (PWM signal) of the lamp "led"                                        |
| **set** pwm.led.strobo **1**          | set the state of the strobe flag (PWM signal) of the "led" lamp                                   |
| **set** uni.rfid1.state **236728347** | set the state of the uni-object of the proximity sensor "rfid1"                                   |
| **set** var.somevar.state **16500**   | set the state of the variable "somevar"                                                           |

In response to this command, _Queen Room_ will send the normal result of the command in XML format with the attribute `status='ok'` or `status='error'`.

### Scenario and transition management

Format: `setmode [name]`

Command examples:

| Example             | Description          |
|---------------------|----------------------|
| **setmode** idle    | reset scenario       |
| **setmode** tune    | switch to setup mode |
| **setmode** ready   | switch to ready mode |
| **setmode** playing | start scenario       |
| **setmode** paused  | stop scenario        |
| **setmode** godmode | switch to god mode   |
| **setmode** win     | forced victory       |
| **setmode** lose    | forced defeat        |

In response to this command, _Queen Room_ will send the standard result of the command in XML format with the attribute `status='ok'` or `status='error'`.

### Skip the current stage

Format: `skipstage`

Command examples:

| Example       | Description                |
|---------------|----------------------------|
| **skipstage** | skipping the current stage |

In response to this command, _Queen Room_ will return the normal result of the command in XML format with the attribute `status='ok'` or `status='error'`.

### Play macroeffects

Format: `play [macroeffect.mef]`

Command examples:

| Example                    | Description                          |
|----------------------------|--------------------------------------|
| **play** sarcofagoopen.mef | play macroeffect "sarcofagoopen.mef" |

In response to this command, _Queen Room_ will return the normal result of the command in XML format with the attribute `status='ok'` or `status='error'`.

### Set current language

Format: `setlanguage [name]`

Command examples:

| Example             | Description          |
|---------------------|----------------------|
| **setlanguage** rus | set Russian language |
| **setlanguage** eng | set English          |

In response to this command, _Queen Room_ will return the normal result of the command in XML format with the attribute `status='ok'` or `status='error'`.

### Set the current scenario

Format: `setscenario [name]`

Command examples:

| Example                   | Description             |
|---------------------------|-------------------------|
| **setscenario** christmas | set Christmas scenario  |
| **setscenario** children  | set children's scenario |
| **setscenario** scary     | install scary scenario  |

In response to this command, _Queen Room_ will return the normal result of the command in XML format with the attribute `status='ok'` or `status='error'`.

### Set agent name

Format: `setname name`

Command examples:

| Example             | Description      |
|---------------------|------------------|
| **setname** backend | set backend name |
| **setname** putty   | set putty name   |

In response to this command, _Queen Room_ will return the normal result of the command in XML format with the attribute `status='ok'` or `status='error'`.

### Sending a message to agents

Format: `send subscriber 'text'`

Command examples:

| Example                                 | Description                                  |
|-----------------------------------------|----------------------------------------------|
| **send** all 'hello everyone'           | send "hello everyone" to all agents          |
| **send** subscribed 'hello subscribers' | send "hello subscribers" to all subscribers  |
| **send** putty 'hello friend'           | send "hello friend" to a agent named "putty" |

!> The 'text' can contain spaces, so it must be enclosed in single quotes.
Within text, the use of single quotes is illegal.

In response to this command, _Queen Room_ will return the normal result of the command in XML format with the attribute `status='ok'` or `status='error'`.
And the target subscriber(s) will receive a message in the following format:

```xml
<response type='event:send' status='ok' time='HH:MM:SS.MS'>text</response>
```

## Getting dynamic states in event mode (EVENTS)

It is advisable to receive some states by changes, and not by constantly polling the server. To do this, you need to subscribe to the event mailing list.

Format: `subscribe`

Command examples:

| Example       | Description               |
|---------------|---------------------------|
| **subscribe** | subscribe to event stream |

In response to this command, _Queen Room_ will send the result of the command in XML format:

```xml
<response type='subscribe' status='ok'></response>  
```

There is also a command that allows you to unsubscribe from the flow of events.

Format: `unsubscribe`

| Example         | Description                           |
|-----------------|---------------------------------------|
| **unsubscribe** | unsubscribe from the stream of events |

In response to this command, _Queen Room_ will send the result of the command in XML format:

```xml
<response type='unsubscribe' status='ok'></response>  
```

The events themselves will be transmitted asynchronously to the client also in XML format:

```xml
<response type='type' status='ok' time='HH:MM:SS.MS'>text</response>
```

If the quest is running, then the time indicates the time of the quest in the format HH:MM:SS.MS; if not, then `time='-'`.
Immediately following the response to `subscribe`, initial states are sent for obvious reasons, and only then changes in the subscription context follow.

Possible events are described below.

### Changing the game mode

Possible options:

```xml
<response type='event:mode' status='ok' time='HH:MM:SS.MS'>idle</response>

<response type='event:mode' status='ok' time='HH:MM:SS.MS'>tune</response>

<response type='event:mode' status='ok' time='HH:MM:SS.MS'>ready</response>

<response type='event:mode' status='ok' time='HH:MM:SS.MS'>win</response>

<response type='event:mode' status='ok' time='HH:MM:SS.MS'>lose</response>

<response type='event:mode' status='ok' time='HH:MM:SS.MS'>godmode</response>

<response type='event:mode' status='ok' time='HH:MM:SS.MS'>playing</response>

<response type='event:mode' status='ok' time='HH:MM:SS.MS'>paused</response>
```

### Changing the script stage

Possible options:

```xml
<response type='event:stage' status='ok' time='HH:MM:SS.MS'>oldstage:newstage:reason</response>  
```

The following values are passed in the body of the message through the ":" delimiter:
- **oldstage** - name of the old stage;
- **newstage** - new stage name;
- **reason** - change reason:
  - **skip** - skip a stage;
  - **resolved** - natural solution to the puzzle.

!> On initialization, when the client connects to _Queen Room_, instead of the `oldstage:newstage:reason` format, just `newstage` is passed.

### Changing the scenario

Possible options:

```xml
<response type='event:scenario' status='ok' time='HH:MM:SS.MS'>scenario_name</response>
```

Where `scenario_name` is the script name from the `getscripts` request.

### Changing the language

Possible options:

```xml
<response type='event:language' status='ok' time='HH:MM:SS.MS'>rus</response>  

<response type='event:language' status='ok' time='HH:MM:SS.MS'>eng</response> 

<response type='event:language' status='ok' time='HH:MM:SS.MS'>esp</response>

<response type='event:language' status='ok' time='HH:MM:SS.MS'>ita</response>  
```

The name of the language is passed inside the tag.

### Notifications

Possible options:

```xml
<response type='event:reminder' status='ok' time='HH:MM:SS.MS'>text</response>  

<response type='event:json' status='ok' time='HH:MM:SS.MS'>text in json format</response>  
```

Notifications are generated when a message text in a logger bean begins with the keyword `:reminder:` or `:json:`.
And in the `text` field of the XML message, a string is inserted that follows any of the above keywords.
The `:reminder:` type is used to send a notification with a regular string, and the `:json:` keyword is used to send JSON.

For notifications with type `type='event:json'`, you need to specify a JSON object as the body of the message.
That is, if the line in logger is `:json:{"type":"http", "method":"post", "url":"targetUrl", "payload":"targetJSON"}`,
then JSON will be inserted into the `text` field of the XML message:

```json
{"type":"http", "method":"post", "url":"targetUrl", "payload":"targetJSON"}  
```

This functionality should be used to effectively link the Queen Room with web applications, in particular with the Queen Bridge component that is part of the Queen Web infrastructure.
