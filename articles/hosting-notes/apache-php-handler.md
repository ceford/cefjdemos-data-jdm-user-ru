<!-- Filename: J4.x:Apache_PHP_Handler / Display title: Обработчики Apache PHP -->

## Заметки

Чтобы определить, какой метод ваш веб-сервер использует для обработки PHP-файлов,
воспользуйтесь ссылками **Администратор / Система / Системная информация** и выберите вкладку Информация о PHP. Поиск страницы по запросу **Server API**. Общие способы
обработки PHP-файлов веб-серверами Apache включают:

### DSO (mod_php)

- **Преимущество:** один из самых быстрых обработчиков.
- **Недостаток:** работает только с одной версией PHP; файлы, сохраняемые
  скриптами PHP, принадлежат пользователю Apache **за исключением** случаев,
  когда используется вместе с mod_ruid2.
- **Как распознать:** Server API - Apache 2.0 Handler

### CGI/FastCGI

- **Преимущество:** скрипты выполняются от имени пользователя домена или поддомена, очень быстрый
  обработчик.
- **Недостаток:** медленнее, чем mod_php, нельзя внести изменения в конфигурацию PHP
  в файле .htaccess.
- **Как распознать:** Server API - CGI/FastCGI

### FPM/FastCGI

- **Преимущество:** очень быстрый, обеспечивает дополнительный уровень гибкости.
- **Недостаток:** использует больше памяти, чем большинство других, нельзя внести
  изменения в конфигурацию PHP в файле .htaccess.
- **Как распознать:** Server API - FPM/FastCGI

### LSAPI (mod_lsapi)

- **Преимущества:**
   - Поддерживает кэширование.
   - Является наиболее производительным обработчиком с малым использованием памяти.
   - Не требует настройки.
   - Может работать с несколькими версиями PHP в одной установке.
   - Поддерживает директивы конфигурации PHP через файлы .htaccess.
   - Обеспечивает безопасность, так как скрипты выполняются от имени владельца домена.
- **Недостатки:**
   - Не все возможности LSAPI доступны.
- **Как распознать:** Server API - ?

На локальном ноутбуке или настольном компьютере вы можете использовать mod_php, но, возможно,
вам потребуется установить пользователя Apache на ваше собственное имя пользователя и указать корневую директорию документов
в вашем собственном файловом пространстве. В противном случае у вас будут проблемы с правами доступа к файлам и папкам.

На хостинг-сервисе необходимо использовать один из вариантов FastCGI или LSAPI.
Хостинг-сервисы могут предоставить вам выбор.

*Переведено openai.com*
