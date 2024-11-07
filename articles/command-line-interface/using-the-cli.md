<!-- Filename: J4.x:Using_the_CLI / Display title: Использование интерфейса командной строки  -->

## Интерфейс командной строки (CLI)

Если у вас есть доступ к серверу через терминал, вы можете использовать CLI Joomla для выполнения рутинных задач без необходимости использовать учетные данные пользователя Joomla. Даже без доступа к терминалу, например, на некоторых аккаунтах общего хостинга, вы можете запускать команды CLI с помощью cron-заданий. Команды CLI часто быстрее или удобнее, чем эквиваленты, выполняемые через интерфейс администратора Joomla (или cPanel). Резервное копирование сайта и установка сайта в режим офлайн/онлайн - это примеры, где вы можете предпочесть использование CLI.

Ядро Joomla имеет около 30 полезных команд, и вы можете добавить больше с помощью дополнительных расширений. Например, вы можете получить внешние данные, такие как данные о геолокации или курсы обмена валют для пользовательского компонента.

## Использование CLI

CLI используется путем вызова исполняемого файла php через командную строку. Это часто отличается от того, что используется веб-сервером, например Apache. Если вы используете cron-задачу, вам, возможно, придется указать полный путь к исполняемому файлу php, как показано ниже:

```
/usr/local/bin/php /home/username/public_html/[дополнительная подпапка]/cli/joomla.php
```

В противном случае, при использовании командной строки терминала, перейдите в директорию cli Joomla и начните выполнение команды без параметров:

```
cd /home/username/public_html/[дополнительная подпапка]/cli
php joomla.php
```

![Список команд](../../../en/images/command-line-interface/cli-command-list.png)

И опробуйте некоторые команды справки, чтобы ознакомиться с ожидаемыми результатами:

```
php joomla.php help
php joomla.php list
php joomla.php help cache:clean
php joomla.php help config:get
```

Каждое описание помощи и строки использования жестко закодированы в файлах библиотеки Console или в сторонних плагинах.

Попробуйте выполнить некоторые простые команды действий:

```
php joomla.php config:get debug
php joomla.php cache:clean
php joomla.php site:down
php joomla.php site:up
```

## Опции

Если вы вызываете команды из cron, возможно, вы не хотите видеть какой-либо вывод:

    php joomla.php -q cache:clean

Обратите внимание, что опции могут использовать пробел или знак =, но переменные должны использовать знак =:

    php joomla.php session:gc --application administrator
    php joomla.php session:gc --application=administrator

    php joomla.php config:set debug=true

## Команды

Краткое объяснение каждой основной команды.

### Кэш

Очистка истекших записей из системного кэша:

    php joomla.php cache:clean --help
    php joomla.php cache:clean

![Вывод очистки кэша](../../../en/images/command-line-interface/cli-cache-clean.png)

    php joomla.php cache:clean expired

![Вывод очистки истекшего кэша](../../../en/images/command-line-interface/cli-cache-clean-expired.png)

### Конфигурация

Получить или установить переменную конфигурации, одну из переменных в
configuration.php или группу переменных. Допустимые группы: db, session,
mail,

    php joomla.php config:get debug --help
    php joomla.php config:get debug

![Вывод получения конфигурации отладки](../../../en/images/command-line-interface/cli-get-debug.png)

    php joomla.php config:set debug=true

![Вывод установки конфигурации отладки](../../../en/images/command-line-interface/cli-set-debug.png)

    php joomla.php config:get --group session

![Вывод получения группы конфигурации session](../../../en/images/command-line-interface/cli-config-get-group-session.png)

### Ядро

Проверка обновлений или обновление Joomla.

    php joomla.php core:check-updates --help
    php joomla.php core:check-updates

![Вывод проверки обновлений ядра](../../../en/images/command-line-interface/cli-check-updates.png)

    php joomla.php core:update --help
    php joomla.php core:update

![Вывод обновления ядра](../../../en/images/command-line-interface/cli-core-update.png)

### База данных

Экспорт или импорт базы данных. Вы можете экспортировать или импортировать все таблицы или выбранную таблицу. Не используйте эту функцию для импорта всех таблиц многоязычного сайта. Это может привести к полной остановке работы Smart Search.

    php joomla.php database:export --help
    php joomla.php database:export --table f4rc2_banners --folder /home/username/tmp/mydb (одна таблица)
    php joomla.php database:export --folder /home/username/tmp/mydb (все таблицы)

    php joomla.php database:import --help
    php joomla.php database:import --table /home/username/tmp/mydb/f4rc2_banners (одна таблица)
    [ОШИБКА] Файл /home/username/tmp/mydb/f4rc2_banners.xml не существует.
    php joomla.php database:import --folder /home/username/tmp/mydb (все таблицы в этой папке)

### Расширения

Просмотр, обнаружение, установка или удаление расширений.

    php joomla.php extension:list --help
    php joomla.php extension:list
    php joomla.php extension:list --type component
    php joomla.php extension:list --type file
    php joomla.php extension:list --type language
    php joomla.php extension:list --type library
    php joomla.php extension:list --type module
    php joomla.php extension:list --type package
    php joomla.php extension:list --type plugin
    php joomla.php extension:list --type template

    php joomla.php extension:discover --help
    php joomla.php extension:discover
    php joomla.php extension:discover:list
    php joomla.php extension:discover:install --eid=

    php joomla.php extension:install --help
    php joomla.php extension:install --path=
    php joomla.php extension:install --url=

    php joomla.php extension:remove --help
    php joomla.php extension:remove

### Поисковик

Очистка и перестроение индекса (фильтры поиска сохраняются).

    php joomla.php finder:index --help
    php joomla.php finder:index
    php joomla.php finder:index purge

![Вывод очистки индекса поисковика](../../../en/images/command-line-interface/cli-finder-index-purge.png)

### Планировщик

Просмотр, изменение состояния или запуск плановых задач.

    php joomla.php scheduler:list --help
    php joomla.php scheduler:list

    php joomla.php scheduler:state --help
    php joomla.php scheduler:state (интерактивный ввод для id задачи)

    php joomla.php scheduler:run --help
    php joomla.php scheduler:run --id ID
    php joomla.php scheduler:run --all

### Сессия

Выполнение сборки мусора в сессиях.

    php joomla.php session:gc --help
    php joomla.php session:gc
    php joomla.php session:gc --application administrator

    php joomla.php session:metadata:gc --help
    php joomla.php session:metadata:gc

### Сайт

Перевод сайта в офлайн или онлайн режим.

    php joomla.php site:down --help
    php joomla.php site:down

    php joomla.php site:up --help
    php joomla.php site:up

### Обновление

Проверка на наличие ожидающих обновлений расширений. Удаляет старые файлы, которые должны были быть удалены во время обновления Joomla.

    php joomla.php update:extensions:check --help
    php joomla.php update:extensions:check

    php joomla.php update:joomla:remove-old-files --help
    php joomla.php update:joomla:remove-old-files

![Вывод удаления старых файлов при обновлении Joomla](../../../en/images/command-line-interface/cli-update-remove-old-files.png)

### Пользователь

Просмотр и управление пользователями.

    php joomla.php user:list --help
    php joomla.php user:list

    php joomla.php user:add --help
    php joomla.php user:add --username cinderella --name Cinderella --email cinders@localhost --usergroup Manager (ввод пароля по запросу)
    php joomla.php user:add (запрос данных)

![Вывод добавления пользователя с запросом данных](../../../en/images/command-line-interface/cli-add-user.png)

    php joomla.php user:addtogroup --help
    php joomla.php user:addtogroup (запрос данных)
    php joomla.php user:addtogroup --username=cinderella --group=Manager

    php joomla.php user:removefromgroup --help
    php joomla.php user:removefromgroup (запрос данных)
    php joomla.php user:removefromgroup --username=cinderella --group=Manager

    php joomla.php user:reset-password --help
    php joomla.php user:reset-password (запрос данных)
    php joomla.php user:reset-password --username=cinderella (запрос пароля)

    php joomla.php user:delete --help
    php joomla.php user:delete (запрос имени пользователя)
    php joomla.php user:delete --username=cinderella (запрос подтверждения - y для подтверждения)


