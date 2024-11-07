<!-- Filename: J4.x:CLI_Database_Exporter_Importer / Display title: Экспорт и импорт базы данных в CLI  -->

## Введение

Перед обновлением Joomla! или установкой стороннего расширения настоятельно рекомендуется создать резервную копию вашего сайта. Интерфейс командной строки Joomla! (CLI) предоставляет команды для экспорта (резервного копирования) и импорта (восстановления) вашей базы данных Joomla!. Обратите внимание, что он не создаёт резервную копию вашей файловой системы, это нужно делать отдельно.

## Требования

Чтобы использовать эти команды, вам нужен доступ к терминалу на хосте, где установлен сайт. Это может быть проблемой на общем хостинге! Вам также нужны базовые знания команд Linux shell, таких как ls и cd. Если всё это незнакомо, вам, вероятно, стоит использовать Akeeba Backup, самое популярное расширение для резервного копирования и восстановления, бесплатное для базового использования.

## Местоположение временного хранилища резервных копий

Будьте внимательны при выборе места хранения резервной копии. Оно должно находиться в вашем личном файловом пространстве, но вне веб-дерева. Цель состоит в том, чтобы создать файл резервной копии, который вы сможете скачать на свой локальный компьютер или другое безопасное место, после чего файл резервной копии можно удалить для экономии пространства. Также убедитесь, что не используете системную папку /tmp, доступ к которой может иметь любой пользователь. Лучшим местом будет ваша личная папка tmp. Структура дерева папок:
```
|-/home/username/tmp - ваша личная папка tmp
|-/home/username/public_html - ваша корневая папка Joomla
```

## Инструкции

Войдите в вашу хост-систему и перейдите в корневую папку вашего сайта.
```
cd /home/username/public_html
```

- Показать все доступные команды CLI:
```sh
  php cli/joomla.php list
```
- Экспортировать базу данных в папку tmp аккаунта:
```sh
  php cli/joomla.php database:export --folder /home/username/tmp/mydbname
```
- Импортировать базу данных из папки:
```sh
php cli/joomla.php database:import --folder /home/username/tmp/mydbname
```

Вы также можете:

- Экспортировать базу данных как .zip файл:
```sh
php cli/joomla.php database:export --zip --folder /home/username/tmp/mydbname
```
- Экспортировать таблицу:
```sh
php cli/joomla.php database:export --table xxxxx_action_log_config --folder /home/username/tmp/mydbname
```
- Экспортировать таблицу как .zip файл:
```sh
php cli/joomla.php database:export --table xxxxx_action_log_config --zip --folder /home/username/tmp/mydbname
```
- Импортировать таблицу:
```sh
php cli/joomla.php database:import --table xxxxx_action_log_config --folder /home/username/tmp/mydbname
```
- Если вам нужна помощь:
```sh
php cli/joomla.php database:export --help
php cli/joomla.php database:import --help
```

## Резервное копирование

Чтобы создать полный резервный копий папок, файлов и базы данных, выполните следующие команды:

1. Архивируйте корневой каталог Joomla:
```sh
tar --exclude='/home/username/public_html/tmp' -zcvf /home/username/tmp/joomla_bak.tgz /home/username/public_html > /home/username/tmp/joomla_bak.log
```
2. Экспортируйте всю базу данных Joomla из корневой папки Joomla:
```sh
php cli/joomla.php database:export --folder /home/username/tmp/db_bak
```

## Восстановление

Чтобы восстановить, сначала убедитесь, что база данных и пользователь базы данных существуют. Затем выполните следующие команды:

1. Извлеките архив:
```sh
tar -xvf /home/username/tmp/joomla_bak.tgz --directory /home/username/public_html
```
2. Убедитесь, что вы находитесь в корневом каталоге вашего сайта:
```sh
cd /home/username/public_html
```
2. Импортируйте базу данных Joomla:
```sh
php cli/joomla.php database:import --folder /home/username/tmp/db_bak
```

## Примечания

В опциях команды tar -zcvf и -xvf буква v обозначает подробный (verbose) режим - список обработанных файлов быстро прокручивается вниз по экрану терминала. Исключите букву v, чтобы не видеть этот список,
*Переведено сервисом openai.com*

