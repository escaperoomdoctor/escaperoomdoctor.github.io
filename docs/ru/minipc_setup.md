# Установка Ubuntu Desktop на Мини ПК

## Подготовка

Скачайте образ [Ubuntu Desktop 22.04.4 LTS](https://releases.ubuntu.com/22.04.4/ubuntu-22.04.4-desktop-amd64.iso)
и запишите на USB-накопитель с помощью win32DiskImager или balenaEthcer.

!> Внимание! Все данные с USB-накопителя будут удалены!

Подключите USB-накопитель, клавиатуру, мышь и источник питания к Мини ПК.

## Установка

Нажать кнопку включения, а затем `F7` на клавиатуре для вызова меню выбора загрузочного устройства.

Выбрать среди устройств USB-накопитель с помощью стрелок и нажать Enter.
Выбрать пункт `Try or install Ubuntu`. Дождаться загрузки установщика.

Экран _**"Welcome"**_. Выбрать `Install Ubuntu`.

Экран _**"Keyboard layout"**_. Нажать `Continue`.

Экран _**"Wireless"**_. Выбрать `I don't want to connect to a Wi-Fi network right now`, нажать `Continue`.

Экран _**"Updates and other software"**_.
Выбрать `Normal installation`, поставить галочку `Install third-party software for graphics and Wi-Fi hardware and additional media formats`,
нажать `Continue`.

Экран _**"Installation type"**_. Выбрать `Erase disk and install Ubuntu`, нажать `Install now`.

Окно _**"Write the changes to disks?"**_. Нажать `Continue`.

Экран _**"Where are you?"**_. Выбрать часовой пояс, нажать `Continue`.

Экран _**"Who are you?"**_. Заполнить следующие поля:
- _Your name_: erd (поля _Your computer's name_ и _Pick a username_ заполнятся автоматически);
- _Choose a password_: erd;
- _Confirm your password_: erd.

Выбрать `Log in automatically`. Нажать `Continue`. Дождаться окончания установки.

## По окончании установки

Окно _**"Installation complete"**_. Нажать `Restart now`. Произойдёт перезагрузка.

На экране загрузки появится надпись _Please remove the installation medium, the press ENTER_.
Отключите USB-накопитель и нажмите `Enter`. Дождитесь запуска системы.

Экран _**"Enable Ubuntu Pro"**_. Выбрать `Skip for now`, нажать `Next`.

Экран _**"Help improve Ubuntu"**_. Выбрать `No, don't send system info`, нажать `Next`.

Экран _**"Privacy"**_. Нажать `Next`.

Экран _**"You're ready to go!"**_. Нажать `Done`.
