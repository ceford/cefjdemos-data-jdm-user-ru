<!-- Filename: J4.x:Global_Configuration / Display title: Глобальная настройка  -->

## Обзор

При установке сайт Joomla создаёт файл с именем **configuration.php** в корне сайта. Этот файл содержит значения конфигурационных переменных, которые применяются ко всему сайту. Примеры включают название сайта и учетные данные базы данных, которые были введены в процессе установки. Существует множество других переменных, которым присваиваются подходящие начальные значения.

Форма глобальной конфигурации позволяет суперпользователю изменять конфигурационные переменные в соответствии с потребностями сайта. Помимо переменных, хранящихся в configuration.php, форма отслеживает информацию о ведении журнала, фильтрации и управлении доступом, часть из которой сохраняется в базе данных.

## Скриншот

Форма глобальной конфигурации имеет шесть вкладок, некоторые из которых содержат длинные списки параметров. Используйте кнопку *Переключить встроенную справку* на панели инструментов, чтобы показать или скрыть информацию о каждом параметре.

![Вкладка сайта глобальной конфигурации](../../../en/images/configuration/global-configuration-site-tab.png)

Некоторые параметры показывают или скрывают другие параметры при их выборе. Например, кнопка **Сайт офлайн** показывает больше полей при установке в *Да*, чем при установке в *Нет*. При расширенной встроенной справке большинство полей достаточно хорошо документированы, чтобы не требовать дальнейших объяснений здесь, за исключением дополнительных пользовательских заметок на каждой вкладке.

## Вкладка Сайт

### Панель Сайта

- **Название сайта** Это имя сайта, которое отображается в форме входа
  администратора и в ссылке Сайт на панели заголовка. Измените его при необходимости.
- **Сайт в автономном режиме** По этому пункту есть отдельный
  [учебник](jdocmanual?article=user/configuration/site-offline).
- **Максимальное количество элементов в списке по умолчанию** задает
  максимальное количество элементов на странице в списочных видах по умолчанию.
  По умолчанию этот параметр установлен на 20, но списочные виды обычно
  включают выпадающий список для выбора других значений в диапазоне от 5 до 100.
  Меньшие значения обрабатываются быстрее и требуют меньше прокрутки.

### Панель метаданных

- **Описание метаданных сайта** Это описание метаданных используется по
  умолчанию, если оно не указано в поле Описание метаданных статьи или в поле
  Описание метаданных меню. Если все три поля пусты, то описание метаданных
  не включается в вывод страницы. Поисковые системы часто используют это
  описание для предоставления описательного текста для страницы. Если оно
  отсутствует, поисковые системы могут использовать текст из контента страницы,
  который может быть неуместным. Рекомендуется описание цели сайта примерно
  в 20 слов.
- **Права на контент** задает запись метаданных *прав*. Если это уместно,
  опишите здесь, какие права имеют другие на использование этого контента.
  Эта запись метаданных не будет включена в веб-страницы, если это поле пусто.
  Пример: лицензия Creative Commons Атрибуция 4.0 Международная (см.
  [Выбор лицензии Creative Commons](https://creativecommons.org/choose/)).

### Панель SEO

SEO — это аббревиатура от *Оптимизация для поисковых систем*. Настройки
в этой группе изменяют формат URL для страниц на сайте, и это может оказать
значительное влияние на позиции в результатах поисковых систем для
отдельных страниц и сайта в целом. URL для SEO более читаемые для человека.

**Совет:** После внесения любых изменений в настройки в этой группе обновите
любые из открытых страниц сайта в вашем веб-браузере (обычно для этого
достаточно нажать Ctrl+R или Cmd+R). Не обновив, вы рискуете столкнуться с тем,
что формат веб-ссылок внутри сайта больше не будет соответствовать тому,
который ожидает Joomla, и тем самым создаст впечатление, что ссылки сломаны.

**Совет:** По возможности избегайте изменения настроек SEO после того,
как сайт уже установлен. Это может привести к сломанным ссылкам с других
сайтов и, возможно, временно снизит позиции сайта в результатах поисковых систем.

- **Unicode алиасы** Изменение этого параметра не изменяет алиасы
  ретроактивно, это просто меняет поведение автоматической генерации
  алиасов для будущего редактирования и создания контента.
  *Транслитерация* (Нет) является настройкой по умолчанию.

### Панель с печеньем

- **Домен для куки** Замещает домен для куки по умолчанию с доменом,
  добавленным здесь. Наиболее вероятная ситуация, когда она потребуется,
  это если Joomla сайт "связан" с другими сайтами (например, форумом,
  электронной коммерцией) в поддоменах Joomla сайта. Домен
  для куки по умолчанию может выглядеть как `www.example.com`, но использование
  здесь `.example.com` (обратите внимание на ведущую точку) позволит выдавать куки,
  которые будут действительны для любого поддомена example.com.
- **Путь для куки** Замещает путь по умолчанию, для которого куки
  действительны, с путем, добавленным здесь. Это может понадобиться,
  если у вас несколько инсталляций Joomla в соседних папках.

## Вкладка системы

![Вкладка системных настроек](../../../en/images/configuration/global-configuration-system-tab.png)

### Панель отладки

Элементы на этой панели хорошо объяснены в интерактивной помощи. Однако, если вы столкнетесь с проблемой, которая отключает нормальный доступ к интерфейсу администратора, возможно, вам придется установить отладку системы, отредактировав файл configuration.php с помощью текстового редактора. На большинстве хостинг-систем, основанных на Linux, разрешения на файл установлены на 444, что предотвращает сохранение из текстового редактора. Измените разрешение на 644 перед редактированием. Затем установите \$debug = `true`; и \$error_reporting = `'maximum'`; и сохраните документ. Затем вы получите трассировку стека, которая точно укажет, где происходит проблема. Вы можете использовать эту информацию, чтобы обратиться за помощью на форумах. Большинство проблем возникает из-за несовместимых сторонних расширений или проблем с хостингом.

## Вкладка "Сервер"

![Вкладка настроек сервера](../../../en/images/configuration/global-configuration-server-tab.png)

### Панель "Почта"

Сайт на Joomla должен иметь возможность отправлять исходящие электронные письма. В частности, он будет отправлять автоматические сообщения владельцу сайта при наличии доступных обновлений. Однако некоторые хостинг-сервисы ограничивают методы отправки исходящей почты. Используя ваш собственный частный адрес электронной почты в поле "Email отправителя":

- Сначала попробуйте PHP Mail и выберите кнопку *Отправить тестовое письмо*. Если письмо прибудет, значит все работает. В противном случае:
- Попробуйте опцию Sendmail. Если это не работает:
- Попробуйте опцию SMTP. Это должно быть настроено на конкретный почтовый сервер. Это может быть сервер, предоставленный вашим хостинг-сервисом, или аккаунт Gmail.
- **SMTP Host** Имя хоста SMTP сервера (например, *smtp.example.com*).
  - **SMTP Port** Порт для подключения к SMTP серверу. Обычно это *25*, когда "Безопасность SMTP" установлена как *None*, или *465* или *587*, когда "Безопасность SMTP" установлена как `SSL/TLS` или `STARTTLS`. Уточните у вашего поставщика услуг SMTP, какой порт использовать.
  - **SMTP Security** Вид безопасности, требуемой SMTP сервером: *None*, *SSL/TLS* или *STARTTLS*. По умолчанию: *None*.
  - **SMTP Authentication** Требуется ли аутентификация перед тем, как SMTP сервер примет исходящие письма. По умолчанию: *No*.
  - **SMTP Username** Имя пользователя для подключения к SMTP серверу в режиме SSL или TLS. Может быть оставлено пустым, если аутентификация SMTP не требуется.
  - **SMTP Password** Пароль для подключения к SMTP серверу в режиме SSL или TLS. Может быть оставлено пустым, если аутентификация SMTP не требуется.

### Использование Gmail в качестве почтового сервера

Если у вас есть работающий аккаунт Gmail, вы можете использовать Gmail в качестве вашего почтового сервера, настроив это в глобальной конфигурации. На вкладке "Сервер" укажите следующее:

- Почтовик: SMTP
- SMTP Host: smtp.gmail.com
- SMTP Port: 465
- SMTP Security: SSL/TLS
- SMTP Authentication: Yes
- Заполните следующие две строки своей информацией. Необходимо использовать специальный пароль для приложения (ASP), описанный ниже.
- SMTP Username: ваше имя пользователя gmail
- SMTP Password: ASP, который вы создали и описан ниже.

Также работают следующие комбинации:

- SMTP Port: 587
- SMTP Security: STARTTLS
- SMTP Port: 25
- SMTP Security: STARTTLS

#### Примечания

- Модуль SSL не требуется включать в Apache.
- Расширение OpenSSL необходимо включить в PHP. Подробности можно найти на [странице установки php.net](https://www.php.net/manual/en/openssl.installation.php).
- Если вы используете WAMP на Windows, модуль openssl по умолчанию не включен, и вам нужно его включить. Для этого:
  - Откройте файл php.ini и раскомментируйте строку `extension=php_openssl.dll`, удалив точку с запятой ; в начале строки.
  - Сохраните файл php.ini и перезапустите службу Apache.
- Если вы используете двухэтапную аутентификацию в Gmail, вам нужно добавить новый пароль в Настройки - Аккаунты - Изменение настроек аккаунта - Другие настройки Google Аккаунта - Безопасность - Двухэтапная аутентификация - Управление паролями для приложений.
- Когда новый Пароль для конкретного приложения (ASP) представлен в виде групп из четырёх символов, разделённых пробелами, убедитесь, что вы **НЕ вводите пробелы** в поле пароля SMTP в настройках почтового сервера в Joomla.
- Пароли для конкретных приложений (ASPs): смотрите страницу поддержки Google о том, как [войти с паролем к приложению](https://support.google.com/accounts/answer/185833).
- Двухэтапная аутентификация: смотрите страницу поддержки Google о том, как [включить двухэтапную аутентификацию](https://support.google.com/accounts/answer/185839).

## Вкладка ведения журналов

![Вкладка глобальной настройки сайта](../../../en/images/configuration/global-configuration-logging-tab.png)

В нормальной работе сайт Joomla должен иметь ведение журналов отключенным. Если возникают проблемы, вы можете включить ведение журналов, установив поле **Логировать почти всё** в положение `Да`. Поле **Логировать устаревший API** предназначено исключительно для разработчиков. Поле **Путь к папке журналов** показывает, где искать журналы, если вы настроили ведение журналов для помощи в отладке. Ошибки, которые вы найдете там, это лишь те, которые перехватывает Joomla. Могут быть и другие ошибки, которые будут отображаться только в журналах ошибок вашего сервера.

## Вкладка Фильтры текста

![Вкладка глобальной конфигурации сайта](../../../en/images/configuration/global-configuration-filters-tab.png)

Настройки фильтров текста будут применяться ко всем полям текстового редактора, отправляемым пользователями в выбранных группах. Эти параметры фильтрации предоставляют больше контроля над HTML, который ваши контент-менеджеры отправляют. Вы можете быть настолько строгим или либеральным, насколько это необходимо, чтобы соответствовать потребностям вашего сайта. Фильтрация осуществляется по желанию, и настройки по умолчанию обеспечивают хорошую защиту от разметки, часто ассоциируемой с атаками на веб-сайты.

## Вкладка Разрешения

![Глобальная вкладка настройки сайта](../../../en/images/configuration/global-configuration-permissions-tab.png)

Разрешения контролируют, что пользователи в каждой группе пользователей могут видеть и делать. Записи во вкладке Разрешения устанавливают разрешения по умолчанию для сайта.

Существует подробное описание использования настроек под этой вкладкой, а также общие принципы работы и настройки разрешений в [Учебнике по Списку Управления Доступом](jdocmanual?article=user/users/access-control).

*Переведено с помощью openai.com*
