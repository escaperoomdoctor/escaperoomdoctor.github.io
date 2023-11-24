# Создание образа для Orange Pi

Скачайте образ [Ubuntu Jammy Desktop 3.0.8](https://drive.google.com/file/d/1HeoGfnMVskSirPlZ4zKhoSxEIKjxeNQd/view?usp=drive_link), распакуйте с помощью 7-Zip и запишите на Micro SD карту с помощью win32DiskImager или balenaEthcer.

Выполните следующие команды:

``` bash
sudo apt-get update
sudo apt-get install unclutter
sudo apt-get install x11vnc
x11vnc -storepasswd
```

Создайте файл /home/orangepi/.config/autostart/chromium.desktop и добавьте в него следующий текст:
```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Name=Autostart
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
firefox-esr -kiosk -private-window https://pranx.com/hacker/typer
```

Для установки компонента для защиты от записи выполнить команду:
``` bash
sudo apt-get install overlayroot
```

Для включения защиты от записи необходимо в файл /etc/overlayroot.conf добавить следующую строку вместо overlayroot="":
``` bash
overlayroot="tmpfs"
```

Если необходимо отредактировать какие-либо файлы или что-то изменить, то необходимо выполнить следующую команду:
``` bash
sudo overlayroot-chroot
```

После этого в терминале можно будет производить изменения. Для выхода из данного режима, нужно нажать Ctrl+D.
Находясь в режиме с возможностью записи изменений, можно отредактировать файл /etc/overlayroot.conf и отключить защиту от записи.

Для установки образа на встроенную память нужно ввести команду:
``` bash
sudo nand-sata-install
```
В открывшейся утилите нужно выбрать _**2 Boot from eMMC-system on eMMC**_, а затем _**ext4**_ или _**5 btrfs**_.
По окончании процесса нажмите  _**Power off**_.
