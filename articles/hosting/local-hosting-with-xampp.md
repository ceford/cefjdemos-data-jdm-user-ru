<!-- Filename: / Display title: Локальный хостинг с XAMPP   -->

## Введение

XAMPP — это легкий в установке пакет, который включает в себя веб-сервер Apache, PHP, XDEBUG и базу данных MySQL. Это позволяет создать среду, необходимую для запуска Joomla! на локальной машине. Последняя версия XAMPP доступна на веб-сайте [Apache Friends](https://www.apachefriends.org/index.html). Доступны загрузки для Linux, Windows и Mac OS X. Скачайте пакет для вашей платформы.

*Важное замечание относительно XAMPP и Skype:* Apache и Skype оба используют порт 80 в качестве альтернативы для входящих подключений. Если вы используете Skype, перейдите в меню Инструменты-Опции-Расширенные-Соединение и снимите выделение с опции *Использовать 80 и 443 в качестве альтернатив для входящих подключений*. Если Apache запускается как служба, он захватит порт 80 раньше, чем запустится Skype, и вы не увидите проблемы. Но, чтобы быть в безопасности, отключите опцию в Skype.

## Установка

Установка на любой платформе очень проста — используйте установщик. Для XAMPP нет реального руководства или справочника. Документация представлена в виде вопросов и ответов, ссылка на которые доступна на странице загрузок.

### Установка на Windows

Для Windows рекомендуется устанавливать XAMPP в "c:\xampp" (не в "c:\program files"). Если вы сделаете это, ваши папки местных веб-сайтов, такие как Joomla!, будут находиться в папке "c:\xampp\htdocs". (По общепринятой практике, весь веб-контент располагается в папке "htdocs".)

Если у вас несколько HTTP-серверов (например, IIS), вы можете изменить порт прослушивания xampp. В файле \apache\conf\httpd.conf измените строку Listen 80 на Listen \[портномер\] (например, "Listen 8080").

<div class="alert alert-info">
<h4>Учебник Joomla Community Magazine<h4>
<p>В этом <a href="https://magazine.joomla.org/all-issues/june-2020/github-installing-git" rel="noreferrer noopener">статье Joomla Community Magazine</a> вы найдете подробный учебник по установке XAMPP на Windows вместе с Joomla 4 Beta, Joomla Patch Tester и Git.</p></div>

Для установки XDebug: [XAMPP - Настройка XDebug для PHP 8](https://odan.github.io/2020/12/03/xampp-xdebug-setup-php8.html)

### Установка на Linux

#### Установка XAMPP

Страница загрузок загружает установочный файл xampp-linux-x64-8.2.12-0-installer.run, где 8.2.12 — это последняя версия. Запустите установочный файл для установки Apache2, MySQL и PHP.

После установки используйте следующие команды для запуска и остановки служб:
```sh
    sudo /opt/lampp/lampp start
    sudo /opt/lampp/lampp stop
```

#### Тестирование вашего локального сервера XAMPP

Откройте браузер и перейдите на

    http://localhost

Файл index.php перенаправит на

    http://localhost/xampp

Там вы найдете инструкции о том, как изменить стандартные имена пользователей/пароли. На компьютере, который не обслуживает файлы для Интернета или локальной сети, изменение стандартных параметров — это личное решение.

#### Получение Joomla

* Загрузите последнюю версию установки Joomla в формате zip
* Разархивируйте на жесткий диск
* Подключитесь к localhost с помощью FTP-клиента
* Создайте папку для вашей Joomla на локальном сервере
* FTP-передача распакованных файлов установки Joomla в вновь созданную папку Joomla.

##### Важно:

- Установка xammp устанавливает правильные права собственника файлов и разрешения.
- Использование **команды CHOWN** вызовет **проблемы с правами собственника для xampp**.
- **Использование nautilus** для манипуляции папками/файлами на localhost приведет к **проблемам с правами собственника для xampp**.

#### Информация о базе данных

- Хост: localhost
- Имя базы данных по умолчанию: test
- Пользователь базы данных по умолчанию: root
- Пароль по умолчанию: **нет** пароля по умолчанию.
- Пароль администратора: ваш выбор.

Установка демо-данных рекомендуется для начинающего пользователя.

После установки удалите папку установки и укажите свой браузер на: `http://localhost/yournewjoomlafolder` или `http://localhost/yournewjoomlafolder/administrator`.

#### Создание ссылки в меню Ubuntu

##### Для создания графического интерфейса для xammp, связанного с меню Ubuntu

Откройте Терминал и введите

    sudo nano /usr/share/applications/xampp-control-panel.desktop

Скопируйте следующее в редактор nano и сохраните.

    [Desktop Entry]
    Encoding=UTF-8
    Name=XAMPP Control Panel
    Comment=Start and Stop XAMPP
    Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
    Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg
    Terminal=false
    Type=Application
    Categories=GNOME;Application;Network;
    StartupNotify=true

Если панель управления не запускается, попробуйте запустить команду Exec непосредственно в терминале:

    gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"

Если вы получите ошибку:

    Error importing pygtk2 and pygtk2-libglade

Установите отсутствующие библиотеки:

    sudo apt-get install python-glade2

#### Отладчик PHP XDebug

Пакет XAMPP для Linux не включает отладчик PHP XDebug. Для установки XDebug на Debian или Ubuntu:

- Установите пакет *build-essential*:

    sudo apt-get update
    sudo apt-get install build-essential
    sudo apt-get install autoconf

- Загрузите [пакет разработки](http://www.apachefriends.org/en/xampp-linux.html) для вашей версии XAMPP и извлеките его поверх существующей установки:

    sudo tar xvfz xampp-linux-devel-1.7.7.tar.gz -C /opt

- Сборка XDebug:

    wget http://xdebug.org/files/xdebug-2.1.3.tgz
    tar xzf xdebug-2.1.3.tgz
    cd xdebug-2.1.3/
    /opt/lampp/bin/phpize

После этого на вашей консоли будет следующее вывод...

    Настроено для:
    PHP Api Version:         20090626
    Zend Module Api No:      20090626
    Zend Extension Api No:   20090626

    ./configure --with-php-config=/opt/lampp/bin/php-config
    make
    sudo make install

Затем вывод будет таким... пожалуйста, следите за указанной директорией.

    Установка общих расширений:     /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Создайте папку в папке temp, которая будет содержать файл данных, сгенерированный XDebug:

    sudo mkdir /opt/lampp/tmp/xdebug
    sudo chmod a+rwx -R /opt/lampp/tmp/xdebug

Альтернативные установки:

Установка с использованием библиотеки расширений PHP (PECL), включенной в xampp:

    sudo /opt/lampp/bin/pecl install xdebug

На Ubuntu/Debian вы можете установить, используя:

    apt-get install php5-xdebug

(предупреждение: это также установит Apache и PHP из репозиторий apt).

##### Предупреждение для пользователей 64-разрядных систем

При компиляции XDebug или установке через apt-get, вы получите ошибку при (пере)запуске xampp:

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/xdebug.so: wrong ELF class: ELFCLASS64

Это происходит потому, что xampp работает на 32 бита, а XDebug — на 64 бита. Чтобы решить эту проблему, создайте xdebug.so на 32-битной машине или загрузите его с:

    http://code.activestate.com/komodo/remotedebugging/

Загрузите файл: "PHP Remote Debugging Client" для "Linux (x86)" Извлеките содержимое файла на ваш компьютер, этот архив содержит несколько папок с номерами версий, например, 4.4, 5.0, 5.1 ... 5.3 и так далее, войдите в папку с более высокой версией или ту, которая подходит вам, затем вручную скопируйте файл "xdebug.so" в следующее расположение, перезаписав, если потребуется

    /opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

Помните, это расположение может быть другим на вашем компьютере

### Установка на Mac OS X

Mac OS X действительно включает в себя сервер Apache по умолчанию, но большинство разработчиков предпочитают использовать интегрированные инструменты и конфигурируемость, предоставляемые XAMPP.

Как и в случае с большинством программ на Mac, установка очень проста. Посетите веб-сайт [Apache Friends](https://www.apachefriends.org/) и загрузите установщик (xampp-osx-8.2.4-0-installer.dmg). Дважды щелкните загруженный установочный файл, чтобы начать процесс установки.

Чтобы запустить сервер, откройте "XAMPP Control.app" и нажмите кнопку запуска рядом с Apache.

#### Небольшая отладка

Многие пользователи Mac сталкиваются с незначительными трудностями на этом этапе при попытке настроить другой экземпляр Apache на своем компьютере. Если вы не можете запустить Apache от XAMPP, у вас есть два варианта:
**Вы можете изменить порт прослушивания XAMPP.** В \Applications\XAMPP\xamppfiles\etc\httpd.conf измените строку "Listen 80" на Listen \[портНомер\]. Например:

    Listen 8080

**Вы можете изменить порт прослушивания предварительно установленного сервера Apache.** В поисковике перейдите в "/etc" (CMD+SHIFT+G); оттуда вы сможете перейти к обычно скрытым файлам Apache. Найдите папку с надписью Apache2 и отредактируйте файл "http.conf". Измените строку "Listen 80" на Listen \[портНомер\]. Например:

    Listen 8080

*Примечание: Если вы решите изменить порт предварительно установленного сервера Apache, возможно, вам потребуется перезапустить компьютер, чтобы изменения вступили в силу. Вам также необходимо будет аутентифицироваться как администратор для изменения этих файлов.*

### Тестирование установки XAMPP

После установки XAMPP и запуска Apache с помощью инструмента XAMPP Control Panel вы можете протестировать его, открыв ваш браузер и перейдя на `http://localhost`. Вы должны увидеть экран приветствия XAMPP, аналогичный приведенному ниже.

![Стартовая страница xampp](../../../en/images/hosting/local-hosting-xampp.png)

Выберите ссылку с названием `phpinfo()` в верхнем меню. Это отобразит длинный экран с информацией о конфигурации PHP, как показано ниже.

![Страница информации о версии php xampp](../../../en/images/hosting/local-hosting-xampp-php.png)

На этом этапе XAMPP успешно установлен. Обратите внимание на строку *Loaded Configuration File*. Мы будем редактировать этот файл в следующем разделе для настройки XDebug.

*Переведено openai.com*

