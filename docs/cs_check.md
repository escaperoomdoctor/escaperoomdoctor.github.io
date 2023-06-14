# Queen Pack Installation and Test Method


This article is about how to properly set up and test equipment before packing the Queen Pack. The whole process is divided into several stages.  


## 1. Preparation of equipment from the warehouse

The first thing to do is to find all the necessary equipment in the warehouse. A list of this equipment can be found in the article about the configuration [queen pack](queen_pack). After all the equipment is found, it must be set aside separately and the setup process begins.  


## 2. Wire crimp

The Queen Pack includes both ready-made wires and those that need to be pre-crimped and prepared. These include:
- 2.2. All colored wires (points 10.1-10.12). The wires themselves can be removed from the cables or bought separately, measured, cut and crimped the ends of the wires with tips;

| Tip                                             | Tool - crimper                                |
|-------------------------------------------------|-----------------------------------------------|
| ![](../assets/photo/cable_end.jpg ':size=200')  | ![](../assets/photo/crimper.jpg ':size=200')  |

- 2.3. Patch cords (clause 9.1). If short purchased ones are used, then we do nothing, if we cook ourselves, then we need to crimp the rj45 connectors on both sides;

| rj45 connector                            | Tools                                    |
|-------------------------------------------|-----------------------------------------------|
| ![](../assets/photo/rj45.jpg ':size=200') | ![](../assets/photo/rj45tool.jpg ':size=200') |


## 3. Assembly of the control system

Next, you need to assemble all the components of the control system. It is not necessary to do this on plywood for setup, it is possible to do the wiring on a table in a horizontal plane, but it is necessary to observe the overall placement of the components to ensure that all wire lengths are suitable. You should get a diagram like this:  

| View from above                                       | 3d view                                                 |
|-------------------------------------------------------|---------------------------------------------------------|
| ![](../assets/layout/QUEEN-VIEW-FROM-ABOVE2.png ':size=300') | ![](../assets/layout/QUEEN-3D-VIEW2.png ':size=500')   |

If you have SketchUp installed, you can take a model of the control system in 3D: [sketchup model](https://1drv.ms/u/s!Am_hkdn5bouS1G9334yBP5ogC4-f).

## 4. First power on

Further, before turning on for the first time, it is necessary to ring all the wires (clauses 10.1-10.12), using a conventional multimeter, make sure that everything is connected correctly, there are no short circuits in the circuits:  

![multimeter](../assets/photo/multimeter_1.jpg ':size=100')

And after switching on, check the voltages at the terminals of the three power sources 24V, 12V and 5V, and make sure that the voltage level differs from the nominal value by no more than 5%.  

## 6. Raspberry Pi setup

Next, you need to perform the following sequence of actions:  

- 6.1. install sd card in raspberry pi;  
- 6.2. install heatsinks on raspberry pi;  
- 6.3. install Raspberry Pi on QUEEN BOARD board;
- 6.4. according to [instructions](rpi_image_upload) download the operating system image and set the Raspberry Pi IP address to _192.168.100.10_;  
- 6.5. get the [QUEEN BOARD overview project](https://1drv.ms/f/s!Am_hkdn5bouSgRRfeMmSvNRvym_y) from the OneDrive cloud  and copy it to your Raspberry Pi to _/home/pi/queen/queen\_board_ folder. If the folder is not created, then create it. General instructions for copying software to Raspberry Pi can be found [here](rpi_soft_install).  

After all the steps, we connect to the Raspberry Pi via the VNC Viewer (see section 5.4) from a computer or laptop and work with the QUEEN BOARD verification program, which is physically running on the Raspberry Pi.  

## 7. QUEEN BOARD performance test

The first thing to do is to make sure the connection to QUEEN BOARD is established. If this is not the case, then we are looking for the cause of the malfunction, otherwise we proceed to checking the control channels.

- 7.1. PWM Test: MOSFETs

We take a regular LED strip and connect it in series to all PWM channels from 1 to 16 (you can not screw it to the terminal blocks, but simply lean it to save time):  

| LED Strip Light                                        | Wiring diagram 12VDC-PWM-CONTROL                        |
|--------------------------------------------------------|---------------------------------------------------------|
| ![](../assets/photo/white_led_strip-1.jpg ':size=300') | ![](../assets/layout/12VDC-PWM-CONTROL2.png ':size=500') |

You need to change the brightness for each of the PWM channels in the Raspberry Pi software and have the ribbon brightness change from maximum to minimum as well.  

- 7.2. Test OUT: Relay

We take a regular LED strip and connect it in series to all relay channels from 1 to 16 (you can not screw it to the terminal blocks, but simply lean it to save time):  

| LED Strip Light                                        | Wiring diagram 12VDC-RELAY-CONTROL                        |
|--------------------------------------------------------|-----------------------------------------------------------|
| ![](../assets/photo/white_led_strip-1.jpg ':size=300') | ![](../assets/layout/12VDC-RELAY-CONTROL2.png ':size=500') |

You need to turn each of the OUT channels on and off in the raspberry pi software and make sure the ribbon turns on and off as well. The 12VDC-RELAY-CONTROL diagram shows a normally open (NO) connection, but the operation of a normally closed (NC) contact must also be verified. This is done in exactly the same way.


- 7.3. Проверка DIN-ADIN: дискретный вход

Берем обычный кусок провода и коммутируем минус питания последовательно ко всем каналам дискретного входа от 17 до 48 (можно не прикручивать к клеммным рейкам, а просто прислонить для экономии времени):  

| Провод                                             | Схема подключения DIN-PASSIVE                     |
|----------------------------------------------------|---------------------------------------------------|
| ![](../assets/photo/colorwires_mm.jpg ':size=300') | ![](../assets/layout/DIN-ADIN-PASSIVE2.png ':size=500') |

Необходимо убедиться, что каждый из 32-х каналов работоспособен - реагирует на приложение минуса питания, а соответствующий индикатор DIN-ADIN в программе меняет свое состояние.  

- 7.4. Проверка ADIN: аналоговый вход

Берем резистивный элемент и коммутируем его на минус питания последовательно ко всем каналам дискретного входа от 17 до 32 (можно не прикручивать к клеммным рейкам, а просто прислонить для экономии времени):  

| Провод                                             | Схема подключения AIN-PASSIVE                     |
|----------------------------------------------------|---------------------------------------------------|
| ![](../assets/photo/colorwires_mm.jpg ':size=300') | ![](../assets/layout/DIN-ADIN-PASSIVE2.png ':size=500') |

Необходимо убедиться, что каждый из 16-ти каналов работоспособен, а соответствующий индикатор AIN в программе меняет показание с 0 (или близкого к нулю значения) до значения превышающего 1000.

## 8. Проверка работоспособности источника 5V под нагрузкой

Необходимо подключить 5V LED лампу на 10-15W к шинам BUS+5VDC и BUS-VDC по схеме:  

![](../assets/layout/5VDC-POWER-SUPPLY2.png ':size=500')

Необходимо убедиться, что лампа загорелась. 

## 9. Проверка работоспособности звуковой подсистемы

Для проверки необходимо:

- 8.1. Необходимо подключить два динамика на 8 Ohm по _Варианту-1_, воспользовавшись [статьей по подключению звука](hw_plug_sound);  
- 8.2. Выставить максимальную громкость, используя перемычки на усилителе TDA7498 и ручку регулировки громкости;  
- 8.3. Используя всю ту же программу проверки QUEEN BOARD проиграть тестовый звук _sound\_check.mp3_.  

Необходимо убедиться, что звук проигрывается громко, без шумов.

## 10. Упаковка

После всех проверок необходимо произвести упаковку компонентов Queen Pack в картонную коробку, используя специальные упаковочные материалы, минимизирующие возможность повреждения содержимого при транспортировке.  






