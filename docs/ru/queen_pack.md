# Перечень комплектующих QUEEN Pack

QUEEN pack - это набор компонентов для дальнейшей сборки системы управления:  

![cs-queen](../assets/layout/cs-queen_3dview.jpg ':size=600')


## Состав QUEEN Pack

| Устройство                                         |                          Фото                           | к-во | Комментарии, требования, модель                               |
|----------------------------------------------------|:-------------------------------------------------------:|------|---------------------------------------------------------------|
| 1. **220V**                                        |                                                         |      |                                                               |
| 1.1. автоматический выключатель                    | ![](../assets/photo/circuit-breaker-1.jpg ':size=200')  | 1    | двухполюсный, 10A                                             |
| 1.2. сетевой фильтр                                |   ![](../assets/photo/power-strip-1.jpg ':size=200')    | 2    | 6 розеток, 10A                                                |
| 2. **[QUEEN BOARD](queen_board)**                  | ![](../assets/layout/queen_board_mini.png ':size=200')  | 1    | PLC for the electronic control                                |
| 3. **Процессорный модуль**                         |                                                         |      |                                                               |
| 3.1. Raspberry Pi                                  |  ![](../assets/photo/raspberry_pi_3_1.jpg ':size=200')  | 1    | модель: raspberry pi 3 model B                                |
| 3.2. micro-SD card                                 |      ![](../assets/photo/microsd-1.jpg ':size=40')      | 1    | SD-карта для RPI, class 10, 8GB                               |
| 3.3. RPI адаптер питания                           |  ![](../assets/photo/ac_dc_adapter_1.jpg ':size=100')   | 1    | адаптер питания для raspberry pi, 5V, 2-3A                    |
| 4. **Аудио-система**                               |                                                         |      |                                                               |
| 4.1. Усилитель звука                               |      ![](../assets/photo/tda7498.png ':size=200')       | 1    | модель: усилитель на базе чипа TDA7498                        |
| 4.2. USB звуковая карта                            |    ![](../assets/photo/usb-audio-1.jpg ':size=100')     | 1    | модель: creative SB play 3                                    |
| 5. **Источники питания**                           |                                                         |      |                                                               |
| 5.1. 24VDC                                         |     ![](../assets/photo/12vdc-ps-1.jpg ':size=200')     | 1    | требования > 200W                                             |
| 5.2. 12VDC                                         |     ![](../assets/photo/12vdc-ps-1.jpg ':size=200')     | 1    | требования > 500W                                             |
| 5.3. 5VDC                                          |     ![](../assets/photo/5vdc-ps-1.jpg ':size=200')      | 1    | требования > 30W                                              |
| 6. **Преобразователь интерфейсов serial-ethernet** |                                                         |      |                                                               |
| 6.1. serial server                                 |  ![](../assets/photo/usr-tcp232-410s.jpg ':size=200')   | 1    | модель: USR-TCP232-410S                                       |
| 6.2. serial server адаптер питания                 |    ![](../assets/photo/acdc_adapter.jpg ':size=100')    | 1    | поставляется с USR-TCP232-410S                                |
| 7. **Ethernet-коммутатор**                         |                                                         |      |                                                               |
| 7.1. ethernet switch                               |   ![](../assets/photo/dlink-switch-1.jpg ':size=200')   | 1    | модель: D-LINK DES-1008C/A1A                                  |
| 7.2. ethernet switch адаптер питания               |    ![](../assets/photo/acdc_adapter.jpg ':size=100')    | 1    | поставляется с ethernet switch                                |
| 8. **Соединители, клеммы, шины**                   |                                                         |      |                                                               |
| 8.1. шины терминальные                             |     ![](../assets/photo/groundbus.jpg ':size=200')      | 6    | требования: 20 соединений, 50A                                |
| 8.2. din-рейка                                     |     ![](../assets/photo/din-rail-1.jpg ':size=200')     | 1    | 5см                                                           |
| 8.3. клемма для GND                                |      ![](../assets/photo/clamp_1.jpg ':size=100')       | 1    |                                                               |
| 9. **Кабели**                                      |                                                         |      |                                                               |
| 9.1. rj45 патчкорды                                |     ![](../assets/photo/patchcoord.jpg ':size=100')     | 2    |                                                               |
| 9.2. serial RS232 кабель                           | ![](../assets/photo/db9m_db9f_cable_1.png ':size=100')  | 1    | поставляется с serial server                                  |
| 9.3. Mini-jack3.5 в 2xRCA                          |   ![](../assets/photo/minijack_2rca.jpg ':size=100')    | 1    |                                                               |
| 9.4. вилки для AC розеток                          |    ![](../assets/photo/vac-socket-1.jpg ':size=100')    | 3    | нужно отрезать вилку от кабеля для монтажа источников питания |
| 10. **Цветные провода**                            |                                                         |      |                                                               |
| 10.1. Желтый провод 4мм<sup>2                      |                                                         | 1    | подача +12V на терминальную шину BUS+12VDC                    |
| 10.2. Желтый провод 4мм<sup>2</sup>                |                                                         | 1    | подача +12V на терминальную шину BUS+12VDC                    |
| 10.3. Синий провод 4мм<sup>2</sup>                 |                                                         | 1    | подача минуса питания на терминальную шину BUS-VDC            |
| 10.4. Синий провод 4мм<sup>2</sup>                 |                                                         | 1    | подача минуса питания на терминальную шину BUS-VDC            |
| 10.5. Синий провод 1.5мм<sup>2</sup>               |                                                         | 1    | укрепление земли PWM                                          |
| 10.6. Синий провод 1.5мм<sup>2</sup>               |                                                         | 1    | объединение минусов источников 12VDC с 5VDC                   |
| 10.7. Синий провод 1.5мм<sup>2</sup>               |                                                         | 1    | минус питания усилителя от источника 24VDC                    |
| 10.8. Синий провод 1.5<sup>2</sup>                 |                                                         | 1    | минус питания QUEEN BOARD                                     |
| 10.9. Желтый провод 1.5мм<sup>2</sup>              |                                                         | 1    | +12V питания QUEEN BOARD                                      |
| 10.10. Коричневый провод 1.5мм<sup>2</sup>         |                                                         | 1    | подача +5V на терминальную шину BUS+5VDC                      |
| 10.11. Коричневый провод 1.5мм<sup>2</sup>         |                                                         | 1    | подача +5V на терминальную шину BUS+5VDC                      |
| 10.12. Коричневый провод 1.5мм<sup>2</sup>         |                                                         | 1    | подача +24V питания усилителя от источника 24VDC              |


