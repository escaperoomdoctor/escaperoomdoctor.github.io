# Clue system editor

The clue system is a component of the _Queen Room_ management program that serves to give players clues in various forms, and this tool can also be used to manually trigger any special effects.
An important feature of this system is that it is possible to display only hints that are relevant for this stage.
Clues can be audio files, video files, as well as any sequence of actions that is described using [macroeffect](soft_studio_macro).

The list of current clues is opened using the _**Give a clue**_ button on the _Queen Room_ navigator panel::

![navigator clue](assets/screen/navigator-clue.jpg ':no-zoom')

## Clue editor interface

The clue system editor is accessed using the _**Clues editor**_ button on the toolbar:

![tools clue](assets/screen/tools-clue.jpg ':no-zoom')

The editor window is a table with six columns.
Adding new clues is done by creating new rows in this table and then changing the parameters in each of the columns.
The order of the elements in the _Queen Room_ clue list will correspond to the order of the elements in the table of the clue system editor.
The editor window looks like this:

![clue editor](assets/screen/clue-editor.jpg ':no-zoom')

The purpose of the controls located at the bottom of the editor window is shown in the table:

|                      Element                       | Description                                                               |
|:--------------------------------------------------:|---------------------------------------------------------------------------|
| ![](assets/screen/clue-editor-up.jpg ':no-zoom')   | Moves the selected line with a clue one position up in the editor table   |
| ![](assets/screen/clue-editor-down.jpg ':no-zoom') | Moves the selected line with a clue one position down in the editor table |
| ![](assets/screen/clue-editor-add.jpg ':no-zoom')  | Creates a new row in the table after the selected                         |
| ![](assets/screen/clue-editor-del.jpg ':no-zoom')  | Deletes the selected row from the table                                   |

The purpose of each of the editor fields is also presented in the table:

|    Field     | Description                                                                                                                                                                                                                                                |
|:------------:|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   **type**   | Clue type. The choice is made independently for each clue from the drop-down list. Can take the following values: _**macro**_, _**audio**_, _**send**_.                                                                                                    |
|  **object**  | The room model object (_**audio**_ for clue type _**macro**_ or _**adapter**_ for clue type _**send**_) that is affected when this clue is run . If you select the clue type _**macro**_, this field is not active.                                        |
| **command**  | The command format depends entirely on the clue type. For _**macro**_ this is a preset macroeffect, for _**audio**_ it is the path to the audio file, for _**send**_ it is a text command.                                                                 |
| **scenario** | In this field, the scenario during which this clue is active is selected from the drop-down list. If you select the _**any**_ option, the clue will be available regardless of the currently running scenario.                                             |
|  **stage**   | In this field, you select from the drop-down list the stage at which this clue will be relevant. If _**any**_ is selected in the _**scenario**_ field, then only stages with the same name from different scenarios will be present in the drop-down list. |
|  **alias**   | Text description of the clue. This description will be displayed in the _Queen Room_ interface when displaying a list of clues.                                                                                                                            |

## Features of working with different types of clues

The principle of working with the _**scenario**_, _**stage**_ and _**alias**_ fields does not depend on the clue type.
The content of the remaining fields depends on the type of clue, which is the subject of the following explanations. 

### Macro type

Using the _**macro**_ type, you can perform any [macroeffect](soft_studio_macro) containing an arbitrary sequence of actions.
After creating a new row in the clue table, in the _**type**_ field, select _**macro**_ from the drop-down list.
Then, in the _**command**_ field, select one of the existing [macroeffects](soft_studio_macro) from the drop-down list.
With the help of a macro effect, you can launch any combination of sound and video for a clue, flash a password with a light, etc.

### Audio type

This type allows you to play any audio file in _mp3_ or _wav_ formats.
The principle of launching is similar to launching an audio file using [macroeffect](soft_studio_macro).
To begin with, in the _**type**_ field, you need to select _**audio**_, then select one of the audio devices from the drop-down list in the _**object**_ field and specify the path to the audio file in the _**command**_ field.
If you want to start an audio file with a given volume level, then you should use the _**macro**_ type.

### Send type

The _**send**_ type allows you to send a text command over the network using the _**adapter**_ object.
For example, you can send the [Queen TV](soft_queen_tv) command to start a video, display an image, or display text.
After specifying the value _**send**_ in the _**type**_ field, select a specific object of the _**adapter**_ type, and enter a text command in the _**command**_ field.
