# Queen Studio Tricks

Some studio hidden tricks are described here.

## Room model editor

This chapter concerns only room model editing in the base studio window.

### Parameter hwtype variants

Parameter _hwtype_ on electrical components and adapters can be used as following...


#### DIN's hwtype

DIN object can call macroeffect when it becomes trigger high.

Format: `macro:filename.mef`

| Example                 | Description                                   |
|-------------------------|-----------------------------------------------|
| **macro**:my_macro1.mef | play my_macro1.mef when din is triggered high |


#### AIN's hwtype

AIN's hwtype can specify minumum, maximum and trigger parameters.

Format: `ain:min:max:level:range:timeout`

- **min** - the minimum range of the ain object;
- **max** - the maximum range of the ain object;
- **level** - the target value;
- **range** - the target tolerance intervals;
- **timeout** - the time tolerance, milliseconds.

_Level_, _range_ and _timeout_ can be interpreted as:
if the value of ain is more than _level - range_ and less than _level + range_ for the period of the _timeout_ milliseconds, 
ain goes to the trigger high.

| Example              | Description                                                                                                                     |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------|
| **ain**:0:500:100:20:250 | will set up ain range [0,500] and it will be triggered high if the value between 80 and 120 for the period of 250 milliseconds. |

#### PWM's hwtype

PWM's hwtype can specify minumum and maximum of pwm object.

Format: `pwm:min:max`

- **min** - the minimum range of the pwm object;
- **max** - the maximum range of the pwm object.

| Example | Description                  |
|---------|------------------------------|
| pwm:0:5 | will set up pwm range [0,5]. |


### Use queen board analog input as the digital one

Imagine, you plug a button, reed, limit switch or any active barrier sensor with states disabled/enabled to the analog input due to the digital inputs (din) were expired on the [QUEEN BOARD](queen_board).
You will have to create an ain object to handle this sensor, and you will have an uncofortable interpretation: near 0 - disabled state, near 1023 - enabled state.
QUEEN software have a feature to read analog value as digital for such cases.
For example, limit switch is connected to the analog pin 13 (i.e. using schematic AIN-PASSIVE).
Create a din object, specify board the limit switch connected to, and set it's index as A13 (or a13 - it's not case sensitive).
This will force queen_room read analog 13 input as digital, and it will take value from 13th analog input, but not digital:
values 0-511 will be interpreted as disabled state and values 512-1023 - as enabled state,
and it makes possible to use digital features like triggering for any analog input.


## Macroeffects editor

This chapter concerns only macroeffects editing.

### Option fade

_Fade_ option allows to change value of several parameters smoothly. For this moment queen allows to fade audio volume and pwm value.
To implement this create a _fade_ action in the macroeffect, select an object from the list (volume or pwm) and specify _fade_ options.

Format: `algorythm:beginvalue:endvalue:timeofchange`

- **algorythm** - algorithm by which the value changes, only linear (_lin_) change is available;
- **beginvalue** - initial value;
- **endvalue** - end value;
- **timeofchange** - the time it takes for a value to change from the initial value to the end value, milliseconds.

| Example        | Description                                           |
|----------------|-------------------------------------------------------|
| lin:0:255:3000 | change pwm value from 0 to 255 within 3 seconds <br/> |
| lin:100:50:500 | change pwm value from 100 to 50 within 0.5 seconds    |
| lin:10:75:1500 | change sound volume from 10 to 75 within 1.5 seconds  |
