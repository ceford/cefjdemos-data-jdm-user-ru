<!--
{
    "source": "https://docs.joomla.org/J4.x:Setting_Up_Your_Local_Environment",
    "title": "\u041d\u0430\u0441\u0442\u0440\u043e\u0439\u043a\u0430 \u043b\u043e\u043a\u0430\u043b\u044c\u043d\u043e\u0433\u043e \u043e\u043a\u0440\u0443\u0436\u0435\u043d\u0438\u044f",
    "description": " ",
    "author": ""
}
-->

Начиная с Joomla! 4 мы изменили процесс разработки. Теперь невозможно
клонировать репозиторий и получить работоспособную установку Joomla.
Мы следуем лучшим практикам и реализуем процесс сборки CMS.

## Краткое руководство по началу работы

Шаги по настройке среды разработки зависят от вашей операционной
системы. Мы не можем написать документацию для каждой операционной системы (ОС),
поэтому воспользуйтесь предпочитаемой поисковой системой, чтобы найти необходимую инструкцию.

### Необходимые инструменты

1.  PHP — в основном тот же, который необходим для работы сайта Joomla, но
    вам потребуется версия PHP CLI (интерфейс командной строки). (См.
    страницу [Настройка LAMPP-сервера для разработки на PHP](https://docs.joomla.org/Special:MyLanguage/Configuring_a_LAMPP_server_for_PHP_development "Special:MyLanguage/Configuring a LAMPP server for PHP development").)
2.  Composer — для управления зависимостями Joomla на PHP. Чтобы получить помощь
    по установке Composer, ознакомьтесь с документацией
    по адресу <a href="https://getcomposer.org/doc/00-intro.md" class="external free"
    target="_blank"
    rel="nofollow noreferrer noopener">https://getcomposer.org/doc/00-intro.md</a>.
3.  Node.js — для компиляции файлов JavaScript и SASS Joomla. Чтобы получить помощь
    по установке Node.js, следуйте инструкциям, доступным
    на сайте <a href="https://nodejs.org/en/" class="external free" target="_blank"
    rel="nofollow noreferrer noopener">https://nodejs.org/en/</a>. Обратите внимание:
    для установки Joomla потребуется NodeJS 12 или более поздней версии.
4.  Git — для управления версиями.

### Шаги по настройке локального окружения

1.  Клонируйте репозиторий
2.  Переключитесь на ветку последнего выпуска.
3.  Выполните `composer install` (composer = менеджер пакетов для PHP) из
    корневого каталога репозитория git. (Можно добавить *--ignore-platform-reqs*, если
    локально не установлен PHP-LDAP и он вам не нужен.)
4.  Выполните `npm ci` (npm = менеджер пакетов для JavaScript, параметр "ci"
    означает «чистая установка») из корневого каталога репозитория git.
    (Обратите внимание: для этого требуется npm версии 10.1.0 или выше.
    Выполните `npm install -g npm@lts`, чтобы обновить npm до
    версии LTS.)

Пользователи Linux и OSX могут настроить следующий псевдоним bash, добавив
следующее в файл *~/.bashrc*:

```
    alias jclean="rm -rf administrator/templates/atum/css; \
    rm -rf templates/cassiopeia/css; \
    rm -rf administrator/templates/system/css; \
    rm -rf templates/system/css; \
    rm -rf media/; \
    rm -rf node_modules/; \
    rm -rf libraries/vendor/; \
    rm -f administrator/cache/autoload_psr4.php; \
    rm -rf installation/template/css"
    alias jinstall="jclean; composer install; npm ci"
```

Это удалит все скомпилированные файлы в вашей системе и выполнит новую
установку одной командой при вызове `jinstall` внутри вашей установки Joomla.

## Более подробное руководство по началу работы

В наши дни Joomla похожа на многие другие веб-инструменты. Она содержит большую часть кода на PHP,
а объём кода JavaScript постоянно увеличивается. Хотя разработка на PHP не требует
столь тщательной подготовки, для JavaScript требуется множество инструментов. Основная
причина заключается в том, что никто не пишет код таким образом, чтобы его понимал каждый браузер,
поэтому код необходимо транспилировать, например, из ES6 в совместимую версию JavaScript. То же
самое относится к CSS. Для Joomla мы используем SASS, который преобразуется
в нативный CSS, понятный любому браузеру. Обратной стороной является то, что настройка
среды разработки становится немного сложнее, но инструменты делают написание кода удобнее.
Благодаря наблюдателям и автоматической перезагрузке браузера вы можете видеть изменения
в режиме реального времени.

### PHP

Достаточно выполнить `composer install`, поскольку эта команда установит зависимости PHP,
сохранённые в файле *composer.lock*. Вы можете выполнять её сколько угодно раз.
Новые пакеты будут устанавливаться только при изменении файла
*composer.lock*. Не выполняйте `composer update`, поскольку эта команда
обновит все пакеты до более новых версий и изменит
файл *composer.lock*.

**Примечание:** возможно, потребуется выполнить `composer install` с
параметром `--ignore-platform-reqs`, чтобы игнорировать требования к платформе,
указанные в Composer. То есть если у вас не установлено расширение LDAP для PHP.

### Скрипты Node/npm

Node.js поставляется с менеджером пакетов под названием NPM (в некотором смысле аналогичным
Composer). В NPM есть команда `run`, и мы подготовили несколько скриптов,
чтобы упростить вашу работу. После изменения файлов JS или SASS необходимо выполнять команды
из корневого каталога репозитория. Ранее для установки зависимостей требовалось
один раз выполнить `npm ci`.

#### npm run build:css (до Joomla 6.1)

Эта команда скомпилирует файлы SASS в CSS, а также создаст минифицированные файлы.

#### npm run build:js (до Joomla 6.1)

Эта команда скомпилирует и транспилирует файлы JavaScript в правильный формат
и создаст минифицированные файлы.

#### Начиная с Joomla 6.2 используйте следующие команды:

- npm run build -- -n <extension> — пересобрать определённое расширение
- выполните npm run builders-list, чтобы найти имя расширения
- npm run build -- --all — пересобрать всё

## Возможные проблемы

При выполнении composer install могут возникнуть следующие ошибки

```
    Problem 1
        - Installation request for joomla/ldap 2.0.0-beta -> satisfiable by joomla/ldap[2.0.0-beta].
        - joomla/ldap 2.0.0-beta requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
    Problem 2
        - Installation request for symfony/ldap v5.1.5 -> satisfiable by symfony/ldap[v5.1.5].
        - symfony/ldap v5.1.5 requires ext-ldap * -> the requested PHP extension ldap is missing from your system.
```

Решение — выполнить composer install с параметром  
`--ignore-platform-reqs`, чтобы игнорировать требования к платформе,  
указанные в Composer. Это необходимо, если у вас не установлено  
расширение LDAP для PHP.

```
    composer install --ignore-platform-reqs
```

Если вы получили ошибку входа, подобную показанной ниже, удалите  
файл `administrator/cache/autoload_psr4.php`.

![экран ошибки входа в Joomla 4](../../../en/images/hosting-local/local-environment-setup/01-joomla-4-login-error-screen.png)

*Переведено openai.com*