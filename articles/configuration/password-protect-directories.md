<!-- Filename: How_do_you_password_protect_directories_using_htaccess%3F / Display title: Защита папок паролем  -->

## Введение

Возможно, вы захотите защитить каталог или весь сайт от публичного доступа. Одна из причин для этого — запретить публичный доступ к сайту разработки. Доступ будет предоставлен только тем, кто знает имя пользователя и пароль. Другая причина — паранойя, например, защита папки администратора, чтобы пользователи должны были ввести имя пользователя и пароль для доступа к форме входа администратора Joomla.

Метод, описанный здесь, предназначен для серверов Apache с использованием файла *.htaccess*.

### Предостережение от Apache.org

Базовая аутентификация не должна считаться безопасной для какого-либо строгого определения безопасности. Хотя пароль хранится на сервере в зашифрованном формате, он может передаваться от клиента к серверу в открытом виде через сеть. Любой, кто слушает с помощью какого-либо пакетного сниффера, сможет прочитать имя пользователя и пароль во время передачи.

Имя пользователя и пароль передаются с каждым запросом, а не только в момент их ввода пользователем. Следовательно, пакетный сниффер не обязательно должен слушать в какой-то особенно стратегический момент, а просто достаточно долго, чтобы увидеть любой отдельный запрос.

Кроме того, сам контент также передается по сети в открытом виде, поэтому, если веб-сайт содержит конфиденциальную информацию, тот же пакетный сниффер получит доступ к этой информации, даже если имя пользователя и пароль не использовались для прямого доступа к сайту.

Не используйте базовую аутентификацию для чего-либо, требующего реальной безопасности. Для большинства пользователей это представляет собой недостаток, поскольку очень немногие люди пойдут на это или имеют необходимое программное обеспечение или оборудование для того, чтобы выяснить пароли. Однако, если кто-то захочет получить доступ, сделать это будет очень просто.

Базовая аутентификация через SSL-соединение, тем не менее, будет безопасной, так как все будет зашифровано, включая имя пользователя и пароль.

## Использование cPanel

Если вы используете услугу хостинга, вы должны использовать метод защиты каталогов, предоставленный этой услугой. Например, в cPanel есть опция под названием Directory Privacy. При выборе этой опции вы можете перейти в любой каталог и установить для него имя. Затем у вас будет возможность создать имя пользователя и пароль для этого каталога. Просто, не правда ли?

Если вы теперь посмотрите в защищенный каталог, вы найдете новый файл .htaccess, содержащий что-то вроде следующего, настроенного для защиты папки api в Joomla:

```
#----------------------------------------------------------------cp:ppd
# Раздел управляется cPanel: Защищенные паролем директории       -cp:ppd
# - Не редактируйте этот раздел файла htaccess!                 -cp:ppd
#----------------------------------------------------------------cp:ppd
AuthType Basic
AuthName "API"
AuthUserFile "/home/username/.htpasswds/public_html/[jroot]/api/passwd"
Require valid-user
#----------------------------------------------------------------cp:ppd
# Конец раздела управляемого cPanel: Защищенные паролем директории -cp:ppd
#----------------------------------------------------------------cp:ppd
```
Важно понимать, что защита каталога в cPanel может использовать тот же файл .htaccess, который используется Joomla для других целей.

Если вы посмотрите в указанный файл passwd, вы увидите введенное вами имя пользователя и зашифрованную версию пароля.

Защиту можно удалить, повторив процесс и сняв галочку с пункта `Защитить этот каталог паролем.` Это удаляет раздел аутентификации из файла .htaccess. Это не удаляет сам файл .htaccess!

## Правила .htaccess

Вы можете выполнить все необходимые шаги вручную. Этот инструмент может помочь:

<a href="https://www.htaccessredirect.net/" rel="nofollow noreferrer noopener"><em>.htaccess</em> генератор</a>

Он создает необходимые файлы для вас. Вам нужно указать имя пользователя, пароль и путь.

Заполните два раздела: **Защита файла паролем** и **Генератор htpasswd**, а затем выберите кнопку `Сгенерировать код`. Вы получите текст для файла .htaccess и текст для файла .htpasswd в отдельных блоках.
Примеры:
```
//Защита файла паролем
<Files /admin>
AuthName "Запрос"
AuthType Basic
AuthUserFile /home/user/.htpasswd
Require valid-user
</Files>
```

```
John:$apr1$a3dbt6j7$KJQr137CY9QuN6tYl6M4Z1
```

*Перевод выполнен с помощью openai.com*
