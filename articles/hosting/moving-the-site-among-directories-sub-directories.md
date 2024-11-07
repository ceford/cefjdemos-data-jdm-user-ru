<!-- Filename: Moving_the_site_among_directories/sub-directories / Display title: Перемещение Директории Установки -->

Часто бывает, что вы устанавливаете Joomla в подкаталог, а затем хотите переместить его в каталог более высокого уровня. Вот краткое руководство о том, как это сделать.

Предположим, вы установили Joomla в следующую папку: public_html/tryjoomla. Теперь, когда вы удовлетворены сайтом, вы захотите переместить его в public_html.

1. Переместите все файлы из подкаталога (т.е., public_html/tryjoomla) в каталог более высокого уровня (т.е., public_html). Вы можете использовать ваш любимый FTP-клиент или панель управления, предоставленную вашим хостинг-сервисом.
2. Скачайте и откройте файл configuration.php в текстовом редакторе.
3. Просто удалите имя папки tryjoomla из пути. Найдите следующие строки:
    ```
    var $live_site = '';
    var $log_path = '/home/username/public_html/tryjoomla/administrator/logs';
    var $tmp_path = '/home/username/public_html/tryjoomla/tmp';
    var $ftp_root = 'public_html/tryjoomla';
    ```
    Измените на:
    ```
    var $live_site = '';
    var $log_path = '/home/username/public_html/administrator/logs';
    var $tmp_path = '/home/username/public_html/tmp';
    var $ftp_root = 'public_html';
    ```
    Примечание: Переменной \$live_site редко требуется значение. Но если оно было задано во время установки, то отредактируйте также и этот путь.
    ```
    var $live_site = 'http://www.example.com/tryjoomla';
    ```
    Измените на:
    ```
    var $live_site = 'http://www.example.com';
    ```
4. Проверьте файл .htaccess вашего сайта. Подкаталог также должен быть удалён оттуда. Директиву RewriteBase следует закомментировать. Проверьте наличие RewriteRule, содержащего старый подкаталог.
5. Убедитесь, что в панели управления хостинга нет перенаправлений на старый подкаталог.
6. Если у вас включено кэширование, войдите в административную панель (которая теперь будет находиться по адресу `http://www.example.com/administrator`, а не `http://www.example.com/tryjoomla/administrator`). Перейдите в Система / Кэш и удалите все файлы кэша.

*Переведено openai.com*  

