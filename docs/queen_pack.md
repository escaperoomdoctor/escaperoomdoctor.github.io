# QUEEN pack components

Queen pack is a component pack for the further assembling and mounting the control system:  

![cs-queen](assets/layout/cs-queen_3dview2.png ':size=600')

## QUEEN Pack Configuration

| item                                     |                        photo                        | pcs | comments, requirements, models                                            |
|------------------------------------------|:---------------------------------------------------:|-----|---------------------------------------------------------------------------|
| 1. **220V**                              |                                                     |     |                                                                           |
| 1.1. circuit breaker                     | ![](assets/photo/circuit-breaker-1.jpg ':size=200') | 1   | L and N breaking, minimal requirements: 15A current                       |
| 1.2. power strip                         |   ![](assets/photo/power-strip2.jpg ':size=200') | 2   | minimal requirements: 6 sockets, 10A current                              |
| 2. **[QUEEN BOARD](queen_board)**        | ![](assets/layout/queen_board_mini2.png ':size=200') | 1   | PLC for the electronic control                                            |
| 3. **Processor module**                  |                                                     |     |                                                                           |
| 3.1. Raspberry Pi                        | ![](assets/photo/raspberry_pi_3_1.jpg ':size=200')  | 1   | exact model : raspberry pi 3 model B                                      |
| 3.2. micro-SD card                       |     ![](assets/photo/microsd-1.jpg ':size=40')      | 1   | SD-card for raspberry pi, minimal requirements: class 10, 8GB             |
| 4. **Audio system**                      |                                                     |     |                                                                           |
| 4.1. Aidio amplifier                     |      ![](assets/photo/tda7498.png ':size=200')      | 1   | exact model : TDA7498 chip based amplifier                                |
| 4.2. USB sound card                      |    ![](assets/photo/usb-audio-1.jpg ':size=100')    | 1   | exact model : creative SB play 3                                          |
| 5. **Power supply**                      |                                                     |     |                                                                           |
| 5.1. 24VDC power supply                  |    ![](assets/photo/12vdc-ps-1.jpg ':size=200')     | 1   | target: audio amplifier, minimal requirements: at least 200W              |
| 5.2. 12VDC power supply                  |    ![](assets/photo/12vdc-ps-1.jpg ':size=200')     | 1   | target: locks, light, etc, minimal requirements: at least 500W            |
| 5.3. 5VDC power supply                   |     ![](assets/photo/5vdc-ps-1.jpg ':size=200')     | 1   | target: sensors, minimal requirements: at least 30W                       |
| 7. **Ethernet switch**                   |                                                     |     |                                                                           |
| 7.1. ethernet switch                     |  ![](assets/photo/dlink-switch-1.jpg ':size=200')   | 1   | exact model : D-LINK DES-1008C/A1A                                        |
| 7.2. ethernet switch server power supply |   ![](assets/photo/acdc_adapter.jpg ':size=100')    | 1   | in box with ethernet switch                                               |
| 8. **Connectors, clamps, bus**           |                                                     |     |                                                                           |
| 8.1. ground bus                          |     ![](assets/photo/groundbus.jpg ':size=200')     | 6   | minimal requirements: 20 terminals, 50A current, copper or brass material |
| 8.2. din rail                            |    ![](assets/photo/din-rail-1.jpg ':size=200')     | 1   | generic din rail, at least 30cm length                                     |
| 8.3. clamp for the GND                   |      ![](assets/photo/clamp_1.jpg ':size=100')      | 1   |                                                                           |
| 9. **Cables**                            |                                                     |     |                                                                           |
| 9.1. rj45 patchcoords                    |    ![](assets/photo/patchcoord.jpg ':size=100')     | 2   |                                                                           |
| 9.3. minijack3.5 to 2xRCA                |   ![](assets/photo/minijack_2rca.jpg ':size=100')   | 1   |                                                                           |
| 10. **Multicolor wires**                 |                                                     |     |                                                                           |
| 10.1. Yellow wire 4mm<sup>2</sup>        |                                                     | 1   | powering +12V to the terminal bus BUS+12VDC                               |
| 10.2. Yellow wire 4mm<sup>2</sup>        |                                                     | 1   | powering +12V to the terminal bus BUS+12VDC                               |
| 10.3. Blue wire 4mm<sup>2</sup>          |                                                     | 1   | minus to the terminal bus BUS-VDC                                         |
| 10.4. Blue wire 4mm<sup>2</sup>          |                                                     | 1   | minus to the terminal bus BUS-VDC                                         |
| 10.5. Blue wire 1.5mm<sup>2</sup>        |                                                     | 1   | PWM minus extension                                                       |
| 10.6. Blue wire 1.5mm<sup>2</sup>        |                                                     | 1   | uniting a minus for 12VDC and 5VDC                                        |
| 10.7. Blue wire 1.5mm<sup>2</sup>        |                                                     | 1   | minus to the amplifier from 24VDC power supply                            |
| 10.8. Blue wire 1.5mm<sup>2</sup>        |                                                     | 1   | minus for **queen board**                                                 |
| 10.9. Yellow wire 1.5m<sup>2</sup>       |                                                     | 1   | powering +12V to the **queen board**                                      |
| 10.10. Brown wire 1.5mm<sup>2</sup>      |                                                     | 1   | powering +5V to the terminal bus BUS+5VDC                                 |
| 10.11. Brown wire 1.5mm2<sup>2</sup>     |                                                     | 1   | powering +5V to the terminal bus BUS+5VDC                                 |
| 10.12. Brown wire 1.5mm<sup>2</sup>      |                                                     | 1   | powering +24V to the amplifier from 24VDC power supply                    |
