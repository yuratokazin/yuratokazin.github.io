# VS Code на Debian

Установка русского языка в VS Code выполняется через установку расширения [Russian Language Pack](https://www.google.com/search?q=Russian+Language+Pack&sca_esv=b1359834a2735cce&biw=1168&bih=562&sxsrf=ANbL-n4kND956FWFAvo1hNtbgsl85B1dHQ%3A1775930222487&ei=bovaafyzHdCzmtkP-dakwAc&ved=2ahUKEwiC9tbjtOaTAxVqmmoFHd0cI_AQgK4QegQIARAC&uact=5&oq=установка+русского+VS+Code+на+дебиян&gs_lp=Egxnd3Mtd2l6LXNlcnAiPdGD0YHRgtCw0L3QvtCy0LrQsCDRgNGD0YHRgdC60L7Qs9C-IFZTIENvZGUg0L3QsCDQtNC10LHQuNGP0L0yCRAhGKABGAoYKjIHECEYoAEYCjIHECEYoAEYCkilDlAAWABwAHgBkAEAmAGmBaABpgWqAQM1LTG4AQPIAQD4AQGYAgGgAtYFmAMAkgcDNS0xoAeDBrIHAzUtMbgH1gXCBwMzLTHIBw6ACAA&sclient=gws-wiz-serp&mstk=AUtExfCC3415DWUwZQTebdNo19iOclwK_97j-sGUfPhbICWFatjpXCedMez5UBqTdW2ux6pvw4XaAD3KacY3pds8ZeiGtTZ8CCFyOlFUh-Kw9PjQxBXSYOeYeYXdZljl3jKejIfPwGca5E92QrxTLTLqg5YmbD_98aKXYYTSL0claHQnOOk&csui=3). Скачайте `.deb` пакет с [официального сайта](https://code.visualstudio.com/), установите через `sudo dpkg -i`, затем нажмите `Ctrl+Shift+P` -> «Configure Display Language» -> «ru». 

Пошаговая инструкция

1. **Скачивание:** Перейдите на сайт Visual Studio Code и скачайте файл `.deb` для Debian/Ubuntu.

2. **Установка:** Откройте терминал, перейдите в папку с загруженным файлом и выполните:

   bash

```
sudo dpkg -i <имя_файла>.deb
sudo apt-get install -f # Для установки зависимостей, если потребуется
```

*Также можно использовать [репозиторий Debian Wiki](https://wiki.debian.org/ru/VisualStudioCode) для установки, советуют [пользователи Reddit](https://www.reddit.com/r/debian/comments/1k5niuq/most_common_way_to_install_vscode/?tl=ru).*

**Русификация:**

- Откройте VS Code.
- Нажмите `Ctrl+Shift+P` для открытия палитры команд.
- Введите `display` и выберите **Configure Display Language**.
- Выберите `ru` или **Install Additional Languages...**, если русского нет в списке.
- После установки расширения перезагрузите редактор. 

Подробные гайды по настройке можно найти на ресурсах вроде [Хабр](https://habr.com/ru/companies/timeweb/articles/916040/)

Как правильно установить Visual Studio Code?

**Выполните следующие действия, чтобы установить Visual Studio Code:**

1. Откройте веб-браузер и перейдите к **code**.**visualstudio**.com.
2. Скачайте версию операционной системы. **Visual Studio Code** поддерживает ОС Windows, Linux и macOS.
3. После скачивания запустите установщик.

**Запустите установку** с правами суперпользователя:

```
sudo dpkg -i code_1.115.0-1775600353_amd64.deb
```

**Исправьте зависимости** (если после установки `dpkg` возникли ошибки):

```
sudo apt-get install -f
```

После этого программа должна быть установлена.

### Установить расширение Pinterest

Установите Piny прямо с рынка расширений для предпочитаемого IDE.

# Tailwind Editor – Piny

Установка
Запустите функцию быстрого открытия VS Code (Ctrl+P), вставьте следующую команду и нажмите Enter.

```
ext install Pinegrow.piny
```

## Начать

1. **Установите расширение Pinterest** (вы делаете это сейчас)
2. Убедитесь, что **хотя** бы **одна папка рабочего пространства открыта.**
3. **Начните редактирование:** щелкните правой кнопкой мыши в любом месте вашего кода и выберите **Изменить в Piny**, чтобы запустить элементы управления визуальным редактированием.

![Редактировать в Piny](https://github.com/Pinegrow/piny-extension/raw/main/images/edit-in-piny.png)

Чтобы включить светлую тему в Visual Studio Code, нажмите `Ctrl+K`, затем `Ctrl+T` (или `Cmd+K`, `Cmd+T` на macOS), чтобы открыть список тем, и выберите одну из светлых, например, **"Light+"** или **"Quiet Light"**. 

**Подробная инструкция:**

1. Откройте палитру команд, нажав `Ctrl+Shift+P` (или `Cmd+Shift+P` на macOS).
2. Введите `color theme` (или "цветовая тема").
3. Выберите пункт **«Preferences: Color Theme»** («Настройки: Цветовая тема»).
4. Используйте стрелки вверх/вниз для предварительного просмотра. Выберите светлую тему из списка, нажав Enter. 

