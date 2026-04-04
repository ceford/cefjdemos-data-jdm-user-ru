<!-- Filename: Installing_Joomla_on_a_Raspberry_Pi / Display title: Установка Raspberry Pi -->

## Предисловие

**Примечание: Этот документ еще не завершен и не полностью протестирован.**

<a href="https://www.raspberrypi.org/"
rel="nofollow noreferrer noopener">Raspberry Pi</a> — это
маленький одноплатный компьютер, который изначально был разработан для содействия
обучению основам информатики в школах и развивающихся странах.
Благодаря своей универсальности, он стал очень популярным и используется как
медиаплеер, небольшой автономный сервер и т.д. Вы можете использовать его как веб-сервер
и установить Joomla! на него. Эта страница покажет вам, как запустить ваш сайт Joomla!
на Raspberry Pi.

## Аппаратное обеспечение

- **Raspberry Pi версии 3 Model B** - Существует несколько моделей Raspberry Pi. Вы можете использовать большинство моделей, которые имеют порт Ethernet (типы Model B). Однако для производительности мы будем использовать последнюю версию с максимальным объемом оперативной памяти.
- **micro SD карта** - Для операционной системы + веб-сервера + Joomla. (RPi версии 3 модели B использует micro SD, другие версии могут использовать обычные SD карты).
- **Адаптер на 5 Вольт (1 Ампер)** - для питания Raspberry Pi вам нужно преобразовать сетевое напряжение (230V или 110V) в 5 Вольт. Raspberry Pi требует около 1 Ампер, и, возможно, больше, если вы подключаете к нему USB устройства.
- стандартный **Ethernet кабель** - для подключения RPi к вашей локальной сети / роутеру / интернету.

## Установка операционной системы

Операционная система Raspbian — это версия Debian Linux, специально скомпилированная для Raspberry Pi. Доступны две версии <a href="https://www.raspberrypi.com/software/" rel="nofollow noreferrer noopener">Raspbian</a>: **Raspbian Jessie with Pixel Lite** (версия с графическим интерфейсом PIXEL на основе Debian Jessie) и **Raspbian Jessie Lite** (минимальная версия на основе Debian Jessie). Поскольку мы используем Raspberry Pi как веб-сервер для Joomla, нам не понадобится графический интерфейс.

**Скачайте** <a href="https://www.raspberrypi.org/downloads/raspbian/" rel="nofollow noreferrer noopener">Raspbian Jessie Lite</a> и распакуйте загруженный файл, например, **2016-09-23-raspbian-jessie-lite.zip** (306 МБ) в **2016-09-23-raspbian-jessie-lite.img** (1,4 ГБ).

Теперь нам нужно скопировать файл .img на карту (micro) SD. Вы можете использовать инструмент с графическим интерфейсом, такой как <a href="https://unetbootin.github.io/" rel="nofollow noreferrer noopener">UNetbootin</a> (для Windows, Mac OS X и Linux) или сделать это в командной строке.

**Будьте осторожны** при записи образа диска *.img* на другой диск. Если вы укажете неверный диск назначения, вы перезапишете этот диск, сделав его непригодным для использования и потеряв данные.

### Windows

В терминале (CMD) проверьте, какому устройству соответствует SD-карта, и выполните что-то вроде:

```
    dd bs=1M if=c:\temp\2016-09-23-raspbian-jessie-lite.img od=[устройство вашей SD-карты]
```

Смотрите также <a href="https://www.raspberrypi.org/documentation/installation/installing-images/windows.md" rel="nofollow noreferrer noopener">Установка образов операционной системы с использованием Windows</a>

### Apple OSX

Проверьте, какое устройство используется для вашей SD-карты. В нашем случае это *disk1s1*, и мы в терминале выполним:

```
    sudo dd bs=1M if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/disk1s1
```

Смотрите также: <a href="https://www.raspberrypi.org/documentation/installation/installing-images/mac.md" rel="nofollow noreferrer noopener">Установка образов операционной системы на MacOS</a>

### Linux

Мы подключаем картридер с (micro) SD-картой к компьютеру. С помощью *dmesg* мы можем найти имя устройства SD-карты. В нашем случае dmesg показывает что-то вроде `[xxxxxx.xxxxxxx]  sdd: sdd1 sdd2`, что означает, что у нас есть SD-карта с 2 разделами. Не записывайте образ Raspbian на раздел, а на весь диск **sdd**.

Мы будем использовать *dd* ("Disk Dump") для записи Input File (*if*) на Output File (*of*), используя заданный размер блока (*bs*).

**Будьте осторожны**: *dd* будет записывать на устройство без каких-либо предупреждений. Тщательно проверьте, что вы записываете на правильное устройство! Если вы запишете на неправильный диск, вы всегда будете помнить команду *dd* как "Уничтожитель Дисков".

```bash
    sudo dd if=~/Downloads/2016-09-23-raspbian-jessie-lite.img of=/dev/sdd bs=4M
```

Смотрите также <a href="https://www.raspberrypi.org/documentation/installation/installing-images/linux.md" rel="nofollow noreferrer noopener">Установка образов операционной системы на Linux</a>

**ПРЕДУПРЕЖДЕНИЕ для версии Raspbian Stretch**: чтобы SSH-сервер работал с загрузки, вам нужно создать пустой файл *ssh* на корневом разделе.

## Подключение Raspberry Pi к локальной сети

После установки операционной системы Raspbian на SD-карту мы:

- Вставим micro SD-карту в слот SD-карты на Raspberry Pi.
- Подключим Ethernet-кабель к Raspberry Pi и к локальной сети (подключим его к нашему роутеру).
- Подключим источник питания 5V к Raspberry Pi.

Загрузка Raspberry Pi занимает примерно 30 секунд. Нам нужно найти IP-адрес, чтобы подключиться к нему с помощью SSH. Для этого можно использовать разные подходы:

- войти в веб-интерфейс вашего роутера и найти подключенные устройства;
- использовать мобильный телефон, подключенный к Wi-Fi роутеру, с помощью приложения для сканирования сети, например, **Fing Overlook**;
- использовать команду, такую как **nmap**. Предположим, что наш ПК имеет IP-адрес **192.168.0**.25, мы можем найти все другие устройства в том же сетевом диапазоне, выполняя следующее:
```
    sudo nmap -sP 192.168.0/24
```
Которое может показать следующие детали:

    Starting Nmap 6.47 ( http://nmap.org ) at 2016-10-22 17:42 CEST
    Nmap scan report for 192.168.0.35
    Host is up (0.00042s latency).
    MAC Address: 42:42:42:42:42:42 (Raspberry Pi Foundation)

Для входа на наш Raspberry Pi используем команду **ssh**.

```
    ssh pi@192.168.0.35
```

При первом подключении появится сообщение:

    The authenticity of host '192.168.0.35 (192.168.0.35)' can't be established.
    ECDSA key fingerprint is 42:42:42:42:42:42:42:42:42:42:42:42:42:42:42:42.
    Are you sure you want to continue connecting (yes/no)?

Выберем **Yes**

    Warning: Permanently added 192.168.0.35 (ECDSA) to the list of known hosts.
    pi@192.168.0.35's password:

и используем *пароль по умолчанию*: *raspberry*, который при успешном входе покажет:

    The programs included with the Debian GNU/Linux system are free software;
    the exact distribution terms for each program are described in the
    individual files in /usr/share/doc/*/copyright.

    Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
    permitted by applicable law.
    pi@raspberrypi:~ $

Мы можем настроить Raspberry Pi используя текстовый интерфейс через:

    sudo raspi-config

### Инструмент конфигурации программного обеспечения Raspberry Pi (raspi-config)

С помощью этого инструмента мы изменим только следующие настройки.

#### 1 Расширение файловой системы

По умолчанию диск на SD-карте имеет размер того же размера, что и файл .img размером 1.4GB, который вы использовали для создания SD-карты для вашего Raspberry Pi. Вы можете использовать эту опцию, чтобы получить остальное дисковое пространство.

#### 2 Изменение пароля пользователя

По соображениям безопасности лучше **изменить пароль по умолчанию** "raspberry" как можно скорее.

#### 3 Параметры загрузки

Мы хотим, чтобы Raspberry Pi загружался в текстовую консоль

##### B2 Консоль текстового автологина, автоматически вошедшая системой 'pi' пользователем

#### 9 Расширенные параметры

##### A3 Разделение памяти

Поскольку мы будем использовать Raspberry Pi как сервер без подключения монитора, мы можем уменьшить память, используемую для GPU, с 64 до **16**

#### 5 Параметры интернационализации

##### I2 Изменить часовой пояс

Мы изменим часовой пояс на наш собственный часовой пояс (например, Europe/Amsterdam)

После всех изменений перезагрузим Raspberry Pi и снова войдем в систему с новым паролем.

    ssh pi@192.168.0.35

Теперь пришло время установить всё остальное.

## Обновление программного обеспечения

Перед установкой чего-либо, мы:

- **обновим** список версий программного обеспечения из всех
  внешних репозиториев
    sudo apt-get update

- **обновим** все установленные программы
    sudo apt-get upgrade

**Обновление списка версий и обновление всех программ — это то, что
следует делать регулярно.**

## Веб-сервер Nginx

Быстрая и легкая альтернатива веб-серверу Apache - это набирающий популярность **Nginx**.

### Установка Nginx

Мы установим nginx и все зависимости (то есть программное обеспечение, необходимое для работы nginx) с помощью команды

    sudo apt-get install nginx

Мы увидим сообщение:

    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    The following extra packages will be installed:
     fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx-common nginx-full
    Suggested packages:
     libgd-tools fcgiwrap nginx-doc ssl-cert
    The following NEW packages will be installed:
     fontconfig-config fonts-dejavu-core libfontconfig1 libgd3 libjbig0 libtiff5 libvpx1 libxpm4 libxslt1.1 nginx nginx-common nginx-full
    0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
    Need to get 3,550 kB of archives.
    After this operation, 8,666 kB of additional disk space will be used.
    Do you want to continue? [Y/n] y

Выбрав "y", nginx и все необходимые пакеты будут установлены.

Вы можете проверить установку с помощью браузера. Перейдите на IP-адрес вашего Raspberry Pi, в нашем случае
<a href="http://192.168.0.35/" rel="nofollow noreferrer noopener">http://192.168.0.35/</a>. Мы должны увидеть сообщение:

    Welcome to nginx on Debian!
    If you see this page, the nginx web server is successfully installed and working on Debian. Further configuration is required.
    For online documentation and support please refer to nginx.org
    Please use the reportbug tool to report bugs in the nginx package with Debian.
    However, check existing bug reports before reporting a new bug.
    Thank you for using debian and nginx.

#### Запуск и остановка Nginx

После установки Nginx автоматически запустится. Вы можете:

- Остановить Nginx: sudo service nginx stop
- Запустить Nginx: sudo service nginx start
- Перезапустить Nginx: sudo service nginx restart

### Настройка Nginx

#### Глобальная настройка Nginx

В глобальной настройке Nginx мы можем настроить кеширование по умолчанию и т.д. Raspberry Pi 3 использует 64-битный **четырехъядерный** процессор ARM Cortex-A53 с тактовой частотой 1.2 ГГц. Если у вас есть более ранняя версия с меньшим количеством ядер ЦП, вам следует использовать

    sudo nano /etc/nginx/nginx.conf

чтобы изменить "worker_processes" в соответствии с количеством ЦП вашего устройства. По умолчанию это настроено как

    worker_processes 4;

поэтому для Raspberry Pi 3 ничего менять не нужно.

После изменения конфигурации Nginx или конфигурации виртуального домена, нужно выполнить команду 

    sudo nginx reload

чтобы изменения вступили в силу.

#### Виртуальные домены

Возможно запускать несколько сайтов Joomla на одном сервере, используя виртуальные домены.

Разместите каждый сайт в отдельной папке в корневом каталоге по умолчанию /var/www/, например:

- /var/www/example.com/
- /var/www/voorbeeld.nl/
    sudo mkdir /var/www/example.com
    sudo mkdir /var/www/voorbeeld.nl

Для каждого сайта мы создадим виртуальный домен, который в основном представляет собой текстовый файл с конкретной информацией о домене:

- /etc/nginx/sites-available/example.com
    server {
    listen 80;
    server_name example.com www.example.com;
    root /var/www/example.com;

    access_log /var/log/nginx/example.com.access_log;
    error_log /var/log/nginx/example.com.error_log info;

    location / {
      index index.php index.html index.htm;
      }
    }

- /etc/nginx/sites-available/voorbeeld.nl
    server {
    listen 80;
    server_name voorbeeld.nl www.voorbeeld.nl;
    root /var/www/voorbeeld.nl;

    access_log /var/log/nginx/voorbeeld.nl.access_log;
    error_log /var/log/nginx/voorbeeld.nl.error_log info;

    location / {
      index index.php index.html index.htm;
      }
    }

Нам нужно включить каждый сайт, создав ссылку из /etc/nginx/sites-enabled/ на виртуальный домен в "sites-available". Мы создаем символическую ссылку для каждого виртуального домена:

    sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/example.com
    sudo ln -s /etc/nginx/sites-available/voorbeeld.nl /etc/nginx/sites-enabled/voorbeeld.nl

Чтобы эта конфигурация виртуального домена вступила в силу, мы выполняем

    sudo nginx reload

и, если всё настроено правильно, мы увидим ответ:

    Reloading nginx configuration: nginx.

## База данных

Мы можем установить MariaDB или MySQL; Joomla будет работать с обеими системами. Давайте установим MariaDB с помощью:

    sudo apt-get install mariadb-server

Во время установки вам нужно будет добавить пароль для пользователя **root**. Давайте создадим **пароль для базы данных**, например **correcthorsebatterystaple**.

Наконец, давайте повысим безопасность нашей установки MariaDB, удалив root-аккаунты, доступные из вне локального хоста, анонимные учетные записи пользователей и тестовую базу данных. Мы можем сделать это с помощью

    mysql_secure_installation

## PHP

Для PHP мы установим **php-fpm** (менеджер процессов FastCGI), который работает как демон и принимает запросы Fast/CGI. Кроме того, мы установим **php5-mysql**, который является модулем для соединения с базой данных MySQL непосредственно из PHP-скриптов.

более новый php7 следует установить с помощью

```bash
sudo apt-get install php-fpm php-mysql
```

Теперь нам нужно сообщить Nginx, что он должен использовать php-fpm для файлов с расширением .php. Мы добавим несколько строк в наши виртуальные домены:

```bash
sudo nano /etc/nginx/sites-available/example.com
```

добавьте:

```nginx
location ~ \.php$ {
    fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
    fastcgi_index index.php;
    include fastcgi_params;
}
```

Проверьте это, создав следующий PHP файл

```bash
sudo nano /var/www/example.com/test.php
```

Мы используем браузер, чтобы проверить, видим ли мы страницу конфигурации PHP по адресу
<a href="http://192.168.0.35/example.com/test.php" rel="nofollow noreferrer noopener">http://192.168.0.35/example.com/test.php</a>

## Joomla!

- сделать
```
    sudo wget https://github.com/joomla/joomla-cms/releases/download/3.6.3/Joomla_3.6.3-Stable-Full_Package.zip
    sudo unzip -x Joomla_3.6.3-Stable-Full_Package.zip
```

## Подключение Raspberry Pi к интернету

Мы хотим, чтобы люди в интернете могли посещать наш сайт на Joomla, который расположен на Raspberry Pi. Чтобы это осуществить, нам нужно **настроить интернет-роутер** для перенаправления всего **входящего трафика** на порт 80 **на наш Raspberry Pi**.

Используйте веб-браузер, чтобы подключиться к веб-интерфейсу вашего роутера. Роутер обычно находится на первом номере вашего диапазона IP-адресов, в нашем случае это 192.168.0.1. В нашем роутере мы настраиваем **Перенаправление портов (Port Forwarding)**:

- Внешний IP-адрес: 0.0.0.0
- Внешний начальный порт: 80
- Внешний конечный порт: 80
- Внутренний IP-адрес: 192.168.0.35 ( = наш Raspberry Pi)
- Внутренний начальный порт: 80
- Внутренний конечный порт: 80
- Протокол: TCP

Убедитесь, что он включен.

Если все работает правильно, вы должны увидеть ваш собственный сайт на Joomla на Raspberry Pi, посетив ваш внешний IP-адрес (Найдите ваш внешний IP-адрес с помощью инструмента, такого как
<a href="http://www.whatsmyip.org/"
rel="nofollow noreferrer noopener">whatsmyip.org</a>).

### Использование доменного имени

Предположим, что наш внешний IP-адрес 42.42.42.42. Также предположим, что мы зарегистрировали доменное имя example.com. Мы хотели бы предоставлять наш сайт на Joomla на Raspberry Pi посетителям, посещающим example.com. Если ваш регистратор доменных имен дает возможность настроить **систему доменных имен (DNS)**, тогда нам нужно создать **A запись** в DNS, которая указывает наше **доменное имя на** наш **IP-адрес** 42.42.42.42. Обратите внимание, что может пройти до 24 часов, прежде чем все интернет-провайдеры будут перенаправлять трафик своих клиентов на настроенную A запись.

### Статический IP-адрес

Большинство роутеров продолжат назначать тот же внутренний IP-адрес вашему Raspberry Pi. Иногда лучше настроить ваш Raspberry Pi на использование статического IP-адреса:

    sudo nano /etc/network/interfaces

изменить

    iface eth0 inet static

на

    iface eth0 inet static
    address 192.168.0.35
    netmask 255.255.255.0
    gateway 192.168.0.1

Шлюз — это IP-адрес вашего роутера. Вы также можете найти его, используя

    route

# Внешние ссылки

- <a href="https://raspberrypi.org"
  rel="nofollow noreferrer noopener">Фонд Raspberry Pi</a> (RPF) -
  официальный сайт и форумы
- <a href="http://elinux.org/RaspberryPiBoard"
rel="nofollow noreferrer noopener">Raspberry Pi Wiki</a>,
  поддерживаемый RPF
- Видео презентации
  <a href="https://youtu.be/u2MFQCoexD0"
  rel="nofollow noreferrer noopener">Joomla на Raspberry
  Pi (с Nginx)</a> на Joomladay Germany 2013 в Нюрнберге, Германия

*Переведено openai.com*

