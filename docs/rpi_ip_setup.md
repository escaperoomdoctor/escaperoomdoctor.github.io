# Raspberry Pi network setup guide

!> To use several Raspberry Pi in the same network without conflicts it is required to setup IP-addresses. This concerns only Ethernet network only (not WiFi), because default IP is constant - _192.168.100.10_

## Wi-Fi setup (optional)

Wireless connection setup can be done using Raspberry GUI shell, i.e. using mouse and display plugged to the target raspberry pi or using remote desktop management like VNC Viewer.
Click left mouse button on the network icon in the right-top of the raspberry desktop (usually it looks like vertical arrows - see the picture below). Choose your WiFi network name in the dropped list (left mouse click) and enter network key in the appeared window:

![rpi-wifi-setup](assets/screen/rpi-wifi-setup.png)

## Ethernet setup

Open console using GUI shell and enter the next command:

``` bash
sudo nano /etc/dhcpcd.conf
```

After text editor open, go to the end of the file and find the next text:

```
interface eth0    
static ip_address=192.168.100.10/24
```

_192.168.100.10_ - is a default raspberry pi IP-address and it must be changed to the new one if required. New IP must be in the range of _192.168.10.11_ to _192.168.10.49_. IP address must be unique within local network. Save and exit file by pressing ctrl-x + y + enter and reboot raspberry then using the next command in the console:

``` bash
sudo reboot
```

## Validation

After rebooting you should reconnect your VNC Viewer, but you must specify new IP-adress. To implement this you should edit connection setting:  
- Right mouse button click on the connection and choose "Properties…"  
- VNC Server and name parameters must contain the same IP-address as we just set up in the text editor  
- Press "OK".  

If connection is established, it's done!


