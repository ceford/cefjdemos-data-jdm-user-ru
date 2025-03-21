<!-- Filename: J4.x:Joomla_CLI_Installation / Display title: Установка Joomla CLI -->

## Введение

Система управления контентом Joomla обычно устанавливается через веб-интерфейс. Однако опытные пользователи могут захотеть установить Joomla, используя команды в терминальном интерфейсе. Это позволяет быстро развертывать несколько экземпляров Joomla.

## Системные требования

Joomla требует PHP, базы данных и веб-сервера. Для последней
информации о поддерживаемом программном обеспечении и минимальных и рекомендуемых
версиях, пожалуйста, посетите
<a href="https://manual.joomla.org/docs/next/get-started/technical-requirements/"
rel="noreferrer noopener">страницу технических требований</a>.

Установка может быть выполнена двумя способами:

1. Ручная установка
2. Автоматическая установка с помощью скрипта

## Ручная установка

Ручная установка позволяет хорошо контролировать процесс установки. Каждый шаг виден в терминале и может быть прерван с помощью `Ctrl+C` в случае неверного ввода.

### Необходимые шаги

1.  Загрузите zip или tar файл пакета установки на веб-сервер.
2.  Распакуйте zip или tar файл.
3.  Переименуйте распакованную папку и переместите её в подходящее место в корне документов веб-сервера.
4.  Перейдите в папку, содержащую код Joomla и выполните следующую команду:<br>
    `php installation/joomla.php install`
5.  Вам будет предложено ввести параметры, необходимые для установки, как в следующем примере стенограммы:
```bash
php installation/joomla.php install

Установка Joomla
================

Проверка системных требований...ОК
Сбор конфигурации...

 Введите имя вашего сайта Joomla:
 > J51
 Введите настоящее имя вашего суперпользователя:
 > John Doe
 Установите имя пользователя для вашей учетной записи суперпользователя:
 > johndoe
 Установите пароль для вашей учетной записи суперпользователя:
 >
 Введите адрес электронной почты суперпользователя сайта:
 > johndoe@example.com
 Тип базы данных. Поддерживаемые: mysql, mysqli, pgsql [mysqli]:
 >
 Хост базы данных [localhost]:
 >
 Имя пользователя базы данных:
 > j4
 Пароль базы данных:
 >
 Имя базы данных [joomla_db]:
 > j51
 Префикс для таблиц базы данных [u5dke_]:
 >
 Шифрование для соединения с базой данных. Значения: 0=Нет, 1=Одностороннее, 2=Двустороннее [0]:
 >
 Относительный или абсолютный путь к публичной папке []:
 >
ОК
Проверка соединения с БД...ОК
Создание и заполнение базы данных...ОК
Запись configuration.php и дополнительная настройка ...ОК
Удаление папки /installation...ОК
 [ОК] Joomla установлена
```

После успешного завершения скрипта новый сайт станет доступен через ваш веб-браузер.

### Примечания

*   Обращайте пристальное внимание на ваши вводимые данные. Невозможно вернуться на шаг назад в скрипте. Если ввод неверен, скрипт должен быть прерван.
*   Имя вашего сайта Joomla отображается в заголовке администратора, поэтому оно должно быть кратким и отличительным. Оно может быть изменено позже.
*   Настоящее имя вашего суперпользователя можно будет изменить позже.
*   Имя пользователя для вашей учетной записи суперпользователя не должно быть похоже на *admin*. Это потенциально небезопасно, так как может быть легко угадано хакером.
*   Пароль пользователя должен состоять из 12 символов.
*   Тип базы данных по умолчанию это *mysqli*. Поддерживаемые типы баз данных — MySQL (mysql) и PostgreSQL (pgsql) и совместимые типы, такие как MariaDB.
*   Хост базы данных практически всегда `localhost`. IP-адрес или имя хоста следует вводить сюда только если необходимый сервер базы данных установлен на другом хосте. Однако, пользователь терминала должен иметь права на запись на выбранном хосте. Вы получите эту информацию от вашего интернет-провайдера (ISP).
*   Имя пользователя базы данных обычно отличается от имени суперпользователя.
*   Пароль базы данных для Joomla обычно отличается от пароля суперпользователя.
*   Имя базы данных по умолчанию `joomla_db`, но нередко используются и другие названия.
*   Префикс для таблиц базы данных выбирается случайным образом из пяти символов. Этот параметр используется для разделения таблиц Joomla от других таблиц, содержащихся в базе данных, если она используется и другими приложениями.
*   Настройки шифрования для соединения с базой данных редко используются. Если ваш интернет-провайдер (ISP) не указал иное, оставьте это значение по умолчанию [0].

## Скриптовая автоматическая установка

Установка Joomla контролируется файлом *joomla.php*, расположенным в
подпапке *installation* после распаковки файла пакета Joomla. Любой
язык программирования, который позволяет вызывать и выполнять PHP-файлы, дает возможность создать скрипт, который автоматизирует необходимые приготовления и саму
установку с использованием пользовательских переменных. Список параметров можно получить
с помощью следующей команды:
```bash
php installation/joomla.php help install
```
Вот пример shell-скрипта с именем jinstall.sh, размещенного в корневой папке Joomla,
созданного для простой установки Joomla:
```
#!/bin/bash

php installation/joomla.php install \
--site-name=SITE-NAME \
--admin-user=ADMIN-USER \
--admin-username=ADMIN-USERNAME \
--admin-password=ADMIN-PASSWORD \
--admin-email=johndoe@example.com \
--db-type=mysqli \
--db-host=localhost \
--db-user=j51 \
--db-pass=Garbage1n0ut \
--db-name=j51 \
--db-prefix=xyz12_ \
--db-encryption=0 \
--public-folder=j51
```
Когда его права доступа установлены на 700, достаточно вызвать скрипт
из командной строки с помощью `./jinstall.sh`, и Joomla будет установлена практически мгновенно. Скрипт можно было бы отредактировать для изменения значений-заполнителей или
их можно изменить позже, после входа в систему Администратора.

Если вы используете этот подход, не забудьте удалить ваш скрипт jinstall.sh или перенести
его из веб-дерева для использования в другом месте позже. Папка установки
удаляется в конце процесса установки. Поэтому повторный запуск скрипта jinstall.sh
не сработает.

