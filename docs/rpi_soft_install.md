# Raspberry Pi QUEEN software installation guide

!> We assuming the Raspberrie's default IP address _192.168.100.10_. If you have different one, please specify it instead of the default one

## Software installation  

Use XFTP application to copy files (guide is specified below):  

:page_facing_up: [Raspberry Pi FTP and SSH clients install](rpi_ftp_ssh_setup)  

Open XFTP, establish the connection with the target raspberry pi. Create _/home/pi/queen_ folder if not existed, and then copy _queen\_room_ and required project there. In the result you must see the following files in the folder _/home/pi/queen_:  

- /macroeffects  
- /media  
- /scenarios  
- room.xml  
- queen_room

Run queen room from VNC, but, before, be sure that queen room has an execute permissions, if it's not not set it up.


## Execution permission setup for queen_room  

If you copy an executable file (like _queen\_room_, _queen\_tv_ and etc) you should set an executable attributes to make an opportunity of run this file. To implement this make a right mouse click on the target file and select "Properties" in the popup menu. Select "Permissions" tab in the "File properties" dialog and make an Execute = Anyone, press enter then:  

![rpi_fileprops](assets/screen/rpi_fileprops.jpg)  


