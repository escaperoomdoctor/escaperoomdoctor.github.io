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

Если у вас установлен SketchUp, то можете взять модель системы управления в 3D: [sketchup model](https://1drv.ms/u/s!Am_hkdn5bouS1G9334yBP5ogC4-f).

## 4. Первое включение

Далее, перед первым включением, необходимо прозвонить все провода (пп. 10.1-10.12), используя обычный мультиметр, убедиться, что все подключено верно, отсутствуют короткие замыкания в цепях:  

![multimeter](../assets/photo/multimeter_1.jpg ':size=100')

А после включения проверить напряжения на клеммах трех источников питания 24V, 12V и 5V, и убедиться, что уровень напряжений отличается от номиналов не более, чем на 5%.  

## 6. Настройка Raspberry Pi

Далее, необходимо осуществить последовательность следующих действий:  

- 6.1. установить sd-карту в raspberry pi;  
- 6.2. установить радиаторы на в raspberry pi;  
- 6.3. сам Raspberry Pi установить на плату QUEEN BOARD;
- 6.4. в соответствии с [инструкцией](rpi_image_upload) залить образ операционной системы и установить IP-адрес Raspberry Pi _192.168.100.10_;  
- 6.5. взять из облака OneDrive [проект проверки QUEEN BOARD](https://1drv.ms/f/s!Am_hkdn5bouSgRRfeMmSvNRvym_y) и скопировать его на Raspberry Pi в папку _/home/pi/queen/queen\_board_. Если папка не создана, то создать её. Общая инструкция по копированию программного обеспечения на Raspberry Pi находится [тут](rpi_soft_install).  

После всех действий подключаемся к Raspberry Pi через VNC Viewer (см. п. 5.4) с компьютера или ноутбука и работаем с программой проверки QUEEN BOARD, которая физически запущена на Raspberry Pi.  

## 7. Проверка работоспособности QUEEN BOARD

Первое, что необходимо сделать - это убедиться, что связь с QUEEN BOARD установлена. Если это не так, то ищем причину неисправности, иначе переходим к проверке каналов управления.

- 7.1. Проверка PWM: mosfet транзисторы

Берем обычную LED-ленту и подключаем ее последовательно ко всем каналам PWM от 1 до 16 (можно не прикручивать к клеммным рейкам, а просто прислонить для экономии времени):  

| Лента                                                  | Схема подключения 12VDC-PWM-CONTROL                     |
|--------------------------------------------------------|---------------------------------------------------------|
| ![](../assets/photo/white_led_strip-1.jpg ':size=300') | ![](../assets/layout/12VDC-PWM-CONTROL2.png ':size=500') |

Необходимо менять яркость по каждому из каналов PWM в программе на Raspberry Pi и убедиться, что яркость ленты также меняется от максимального до минимального.  

- 7.2. Проверка OUT: реле

Берем обычную LED-ленту и подключаем ее последовательно ко всем каналам реле от 1 до 16 (можно не прикручивать к клеммным рейкам, а просто прислонить для экономии времени):  

| Лента                                                  | Схема подключения 12VDC-RELAY-CONTROL                     |
|--------------------------------------------------------|-----------------------------------------------------------|
| ![](../assets/photo/white_led_strip-1.jpg ':size=300') | ![](../assets/layout/12VDC-RELAY-CONTROL2.png ':size=500') |

Необходимо включать и выключать каждый из каналов OUT в программе на raspberry pi и убедиться, что лента также включается и выключается. На схеме 12VDC-RELAY-CONTROL иллюстрируется подключение через нормально открытый контакт (NO), но необходимо также проверить работоспособность и нормально замкнутого контакта (NC). Делается это полностью аналогично.  


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






