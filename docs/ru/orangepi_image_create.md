# Создание образа для Orange Pi

Скачайте образ [Ubuntu Desktop](https://drive.google.com/drive/folders/1KzyzyByev-fpZat7yvgYz1omOqFFqt1k) и запишите на Micro SD карту с помощью win32DiskImager.

Выполните следующие команды:

``` bash
sudo apt update
sudo apt upgrade
# sudo apt install chromium-browser
snap install chromium
sudo apt install unclutter
sudo apt install x11vnc
x11vnc -storepasswd
```

Создайте файл /home/orangepi/.config/autostart/chromium.desktop и добавьте в него следующий текст:
```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Chromium
Exec=./autostart.sh
OnlyShowIn=XFCE;
StartupNotify=false
Terminal=false
Hidden=false
```

Создайте файл /home/orangepi/autostart.sh со следующим содержимым:
``` bash
#!/bin/bash

x11vnc -forever -usepw -display :0 -ultrafilexfer &
xset s off
xset -dpms
unclutter -idle 3 &
chromium-browser --start-fullscreen --noerrordialogs --no-first-run --fast --fast-start --disk-cache-dir=/dev/null --disk-cache-size=1 --incognito --kiosk http://192.168.0.117:3000/password
```
Для установки образа на встроенную память нужно ввести команду:
``` bash
nand-sata-install
```
В открывшейся утилите нужно выбрать _**2 Boot from eMMC-system on eMMC**_, а затем _**5 btrfs**_. По окончании процесса нажмите  _**Power off**_.
