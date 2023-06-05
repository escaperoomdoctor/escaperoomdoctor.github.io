# Queen Sound installation and setup

_Queen Sound_ is purposed for additional sound channels inside the escape room. This solution is quite big and expensive, but it's very flexible and well suitable for the such cases like extra sound for separate room or big gadget accompaniment.  

## Devices list  

| device                      |                       photo                        | comments                                  |
|-----------------------------|:--------------------------------------------------:|-------------------------------------------|
| 1. Power strip              |  ![](assets/photo/power-strip-2.jpg ':size=100')   |                                           |
| 2. Processor module         |                                                    |                                           |
| 2.1. Raspberry Pi           | ![](assets/photo/raspberry_pi_3_1.jpg ':size=200') | exact model: Raspberry Pi 3 model B or B+ |
| 2.2. Micro-SD card          |     ![](assets/photo/microsd-1.jpg ':size=40')     | class 10, 8-32Gb                          |
| 2.3. RPi power supply       |  ![](assets/photo/ac_dc_adapter_1.jpg ':size=60')  | 5.1V, 2.5A                                |
| 2.4. USB sound card         |   ![](assets/photo/usb-audio-1.jpg ':size=100')    | model: creative SB play 3                 |
| 3. Audio                    |                                                    |                                           |
| 3.1. Audio amplifier        |     ![](assets/photo/tda7498.png ':size=100')      | model: TDA7498 chip based amplifier       |
| 3.2. 24VDC power supply     |    ![](assets/photo/12vdc-ps-1.jpg ':size=200')    | requirements > 200W                       |
| 3.3. Mini-jack 3.5 to 2xRCA |  ![](assets/photo/minijack_2rca.jpg ':size=100')   |                                           |
| 3.4. 2, 4 or 8 speakers     |    ![](assets/photo/speakers-1.jpg ':size=100')    |                                           |

Speakers connection we can look [here](hw_plug_sound), but if you need to plug only two speakers, just plug each speaker to each of two amplifiers channel.  

## Raspberry Pi preparations

To prepare Raspberry Pi, first [upload OS image](rpi_image_upload), and then setup an IP address, using [this guide](rpi_ip_setup). Use [installation guide](rpi_soft_install) to copy the last _queen\_sound_ version to the folder _/home/pi/queen/_. Also, we are uploading necessary audio files.  

After, you should set a _queen\_sound_ executable attributes to make an opportunity of run this file. To implement this make a right mouse click on the target file and select "Properties" in the popup menu. Select "Permissions" tab in the "File properties" dialog and make an Execute = Anyone, press enter then:  

![rpi_fileprops](assets/screen/rpi_fileprops.jpg)  

## Sound check  

To implement a test, create an adapter component in the _Queen Studio_, set property hwtype=sound, and specify an Raspberry IP address, where _Queen Sound_ is running, port=4455. Start _Queen Room_ and be sure the connection with _Queen Sound_ is established (adapter becomes green), double left click on the adapter, then submenu "play"  and choose file sound\_check.mp3 to play from the list (files should be copied in advance). For Raspberry Pi, _Queen Sound_ plays this audio on all devices (audio, hdmi, usb, ... ), and for Windows it plays file on all devices, specified in the queen\_sound.cfg. Btw, queen\_sound.cfg is not required for the Raspberry Pi.   






