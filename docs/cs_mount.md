# How to mount the control system

Use our [video tutorials](video_tutorials) to mount a control system.

If you have installed SketchUp you can explore QUEEN control system [sketchup model](https://1drv.ms/u/s!Am_hkdn5bouS1G9334yBP5ogC4-f) with it.  

## Recommended additional purchase list

After you receive a [queen pack](queen_pack), we recommend to purchase the following stuff:

| item                          |                      photo                      | pcs  | comments, requirements, models                                                              |
|-------------------------------|:-----------------------------------------------:|------|---------------------------------------------------------------------------------------------|
| sheet of plywood or textolite |   ![](assets/photo/plywood-1.jpg ':size=200')   | 1    | use a piece of plywood or textolite at least 630mm x 750mm to mount the queen pack items    |
| electric box                  | ![](assets/photo/electrobox-1.jpg ':size=200')  | 1    | you can optionally purchase electric box to hide the plywood or textolite, but not required |
| tapping screws                |    ![](assets/photo/screw_1.jpg ':size=50')     | much | depends on what kind of surface was chosen: plywood or textolite                            |
| multimeter                    | ![](assets/photo/multimeter_1.jpg ':size=100')  | 1    | use multimeter later to check the connections after the mount process                       |

## QUEEN Pack components locating

First place all the components on the plywood

![cs-queen_place](assets/layout/cs-queen_place2.png ':size=600')

## Wiring layout

Connect the wires of the input unit according to the diagram below  

![cs-queen_wiring](assets/layout/wireMain230v.png ':size=600')

Lay 230 volt wires and cables according to the diagram below

![cs-queen_wiring](assets/layout/wire230v.png ':size=600')

Route the GND wires according to the diagram below.

![cs-queen_wiring](assets/layout/wireGND.png ':size=600')

Route the 12 volt wires according to the diagram below

![cs-queen_wiring](assets/layout/wire12v.png ':size=600')

Route the 5 volt wires according to the diagram below

![cs-queen_wiring](assets/layout/wire5v.png ':size=600')

Route the 24 volt wires according to the diagram below

![cs-queen_wiring](assets/layout/wire24v.png ':size=600')

Connect audio cables according to the diagram below

![cs-queen_wiring](assets/layout/wiresAUDIO2.png ':size=600')

Connect the ETHERNET cable according to the diagram below.

![cs-queen_wiring](assets/layout/wireETHERNET2.png ':size=600')

To connect Queen UniSense expansion modules (not included), connect the wires according to the diagram below

![cs-queen_wiring](assets/layout/wiresRS485.png ':size=600')

## Plugging various devices

Use the following connections for plugging various devices:

| connection name       | photo                                                    | description                                                                                                                                                                        |
|-----------------------|----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 12VDC-RELAY-CONTROL   | ![](assets/layout/12VDC-RELAY-CONTROL2.png ':size=500')   | layout shows how to control 12VDC devices with a relay                                                                                                                             |
| 5VDC-RELAY-CONTROL    | ![](assets/layout/5VDC-RELAY-CONTROL2.png ':size=500')    | layout shows how to control 5VDC devices with a relay                                                                                                                              |
| VAC-RELAY-CONTROL     | ![](assets/layout/VAC-RELAY-CONTROL2.png ':size=500')     | scheme for connecting devices 110/220V to the relay                                                                                                                        |
| CIRCUIT-RELAY-CONTROL | ![](assets/layout/CIRCUIT-RELAY-CONTROL2.png ':size=500') | layout shows how to short any contact (i.e. emulating the button press) with a relay                                                                                               |
| 12VDC-PWM-CONTROL     | ![](assets/layout/12VDC-PWM-CONTROL2.png ':size=500')    | layout shows how to smooth control 12VDC devices with a PWM transistor. **Warning! maximum current is 2A per one channel (transistor), that is an equivalent 5m of the LED strip** |
| 5VDC-PWM-CONTROL      | ![](assets/layout/5VDC-PWM-CONTROL2.png ':size=500')       | layout shows how to smooth control 5VDC devices with a PWM transistor                                                                                                              |
| 12VDC-POWER-SUPPLY    | ![](assets/layout/12VDC-POWER-SUPPLY2.png ':size=500')    | layout shows how to make a static power for 12VDC devices                                                                                                                          |
| 5VDC-POWER-SUPPLY     | ![](assets/layout/5VDC-POWER-SUPPLY2.png ':size=500')     | layout shows how to make a static power for 5VDC devices                                                                                                                           |
| VAC-POWER-SUPPLY      | ![](assets/layout/VAC-POWER-SUPPLY2.png ':size=500')     | power supply circuit for 110/220V devices                                                                                                                     |
| DIN-ADIN-PASSIVE      | ![](assets/layout/DIN-ADIN-PASSIVE2.png ':size=500')           | connection diagram of sensors with dry contact and resistive elements. resistive elements are connected only to ADIN inputs                                                                                                                 |
| DIN-ADIN-ACTIVE       | ![](assets/layout/DIN-ADIN-ACTIVE2.png ':size=500')      | connection diagram of active (requiring power) sensors (type NPN) to a discrete input    |                                                                                          |                                          |

## Check the connections

Use multimeter to check the connections before you power on the control system. Also it is recommended to check 24V, 12V and 5V voltages after the power on, to be sure power supply is operable.
