<!-- Filename: Installing_Joomla!_using_BitNami_Joomla!_stack / Display title: Установка Bitnami   -->

## Предисловие

**ПРИМЕЧАНИЕ:** Установка BitNami Joomla! больше не существует как отдельный инсталлятор. Вместо этого она поставляется: 1) как облачный экземпляр, 2) в контейнере, либо Kubernetes, либо Docker или 3) как виртуальная машина. Виртуальная машина будет запускаться на вашей операционной системе в гипервизоре, таком как Virtual Box или VMware Player. Она все еще поставляется со всеми необходимыми зависимостями, как в виде отдельного инсталлятора.

Опция 1 больше не применяется. Также в Опции 2, BitNami Lamp Stack далее, поставляется в облаке или виртуальной машине. В любом случае, Bitnami делает процесс установки Joomla! на локальном компьютере простым и полным.

Вы можете скачать последнюю версию пакета Bitnami для Joomla! для Windows, Linux и Mac на <a href="http://bitnami.org/stack/joomla" rel="nofollow noreferrer noopener">http://bitnami.org/stack/joomla</a>.

**Требуется пересмотр!**

BitNami Joomla! Stack — это инсталлятор "все в одном", который упрощает установку Joomla на вашем компьютере. Он бесплатный, легкий в использовании и автономный. Это значит, что он содержит и автоматически настраивает каждую часть программного обеспечения (зависимость), необходимую для работы Joomla в целях разработки или эксплуатации, включая Apache HTTP Server, MySQL и PHP.

## Вариант 1: Joomla! стек (Рекомендуется)

Этот метод предполагает, что у вас уже установлена среда
(**W**indows/**L**inux/**M**ac)...**AMP** (Apache HTTP Server, MySQL и PHP).

### Установка Joomla! Стек

Независимо от операционной системы, которую вы используете (Windows / Linux / Mac), процесс установки одинаков.

Скачайте последнюю версию Joomla! стека с
<a href="http://bitnami.org/stack/joomla"
rel="nofollow noreferrer noopener">сайта BitNami</a>.

Найдите установочный файл, который вы только что скачали (имя файла будет похоже на bitnami-joomla-VERSION-linux-installer.run). Дважды щелкните на значке, чтобы запустить установщик.

Если вы используете Linux, вам сначала нужно предоставить файлу права на выполнение, используя эту команду:

chmod +x /path/to/bitnami-joomla-VERSION-linux-installer.run

<img src="https://docs.joomla.org/images/a/a0/Joomla_welcome2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack setup" />

Нажмите "Далее".

<img src="https://docs.joomla.org/images/5/5f/Joomla_components2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack components" />

Выберите компоненты, которые вы хотите установить. Если вы не уверены, оставьте выбранными компоненты по умолчанию. Нажмите "Далее", когда закончите.

<img src="https://docs.joomla.org/images/0/0a/Joomla_directory2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack installation directory" />

Теперь система спросит, куда вы хотите установить программу. Укажите место, куда хотите установить BitNami Joomla! стек и нажмите "Далее", когда закончите.

<img src="https://docs.joomla.org/images/3/3c/Joomla_userdata2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack sdmin account" />

Пользователь и пароль, которые вы предоставите здесь, будут использованы для создания учетной записи администратора в Joomla! Нажмите "Далее", когда закончите.

<img src="https://docs.joomla.org/images/8/8b/Joomla_sitename2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack sitename" />

Введите имя, которое хотите использовать для вашего сайта Joomla, и нажмите "Далее".

<img src="https://docs.joomla.org/images/d/dd/JoomlaReadytoinstall2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack Ready to install2" />

Установщик позволяет вам настроить учетную запись электронной почты, чтобы Joomla! могла отправлять уведомления по электронной почте. Нажмите "Далее".

<img src="https://docs.joomla.org/images/9/9d/JoomlaCopyingfiles2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack Copying files" />

Подождите минуту, пока установщик копирует файлы и настраивает вашу Joomla! установку.

<img src="https://docs.joomla.org/images/e/ea/Joomlafinalscreen2.png"
decoding="async" data-file-width="614" data-file-height="538"
width="614" height="538" alt="Joomla Bitnami lampstack final screen" />

Joomla! теперь установлена и готова к использованию. Нажмите "Завершить", чтобы запустить приложение.

<img src="https://docs.joomla.org/images/8/8d/JoomlaManager.png"
decoding="async" data-file-width="784" data-file-height="586"
width="784" height="586" alt="Joomla Bitnami lampstack Manage servers" />

С помощью инструмента менеджера легко запускать / останавливать серверы Apache и MySQL.

<img
src="https://docs.joomla.org/images/7/73/Joomlaapplicationscreen2.png"
decoding="async" data-file-width="982" data-file-height="729"
width="982" height="729" alt="Joomla application screen" />

Вы можете легко управлять базой данных Joomla! с помощью phpMyAdmin.

<img src="https://docs.joomla.org/images/f/f3/JoomlaphpMyAdmin.png"
decoding="async" data-file-width="982" data-file-height="751"
width="982" height="751" alt="phpMyAdmin screen" />

## Вариант 2: BitNami LAMPStack и Joomla!

### Что такое BitNami LAMPStack?

BitNami LAMPStack — это бесплатный пакет, который легко устанавливается и включает все необходимые программные компоненты (зависимости) для настройки и запуска среды LAMP (Apache, MySQL и PHP для Linux) для разработки или производственных нужд. Это самодостаточный пакет, который не вносит изменений в вашу систему и может быть легко удален. Вы можете загрузить последнюю версию BitNami LAMPStack для Linux на сайте <a href="http://bitnami.org/stack/lampstack" rel="nofollow noreferrer noopener">http://bitnami.org/stack/lampstack</a>. Недоступны также <a href="http://bitnami.org/stack/wampstack" rel="nofollow noreferrer noopener">версия для Windows</a> и <a href="http://bitnami.org/stack/mampstack" rel="nofollow noreferrer noopener">версия для OS X</a>.

Независимо от того, под какой операционной системой вы работаете (Windows / Linux / Mac), процесс установки одинаков.

### Установка BitNami LAMPStack

Найдите установочный файл, который вы только что загрузили с сайта BitNami (имя файла будет похоже на bitnami-lampstack-VERSION-linux-installer.run). Дважды щелкните значок, чтобы запустить установку.

<img src="https://docs.joomla.org/images/1/14/Lampstack_welcome.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Приветствие Bitnami lampstack" />

Нажмите "Вперед".

<img src="https://docs.joomla.org/images/7/78/Lampstack_directory.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Каталог Bitnami lampstack" />

Теперь укажите место, куда вы хотите установить программу. Выберите расположение на вашем компьютере и нажмите "Вперед", когда закончите.

<img src="https://docs.joomla.org/images/2/22/Lampstack_passwd.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Пароль Bitnami lampstack" />

Введите ваш root пароль для MySQL. Это будет пароль для пользователя "root" для базы данных.

<img src="https://docs.joomla.org/images/7/72/LampstackReadytoinstall.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Готов к установке Bitnami lampstack" />

Установщик теперь готов начать процесс установки. Нажмите "Вперед".

<img src="https://docs.joomla.org/images/1/19/LampstackCopyingfiles.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Копирование файлов Bitnami lampstack" />

Подождите минуту, пока установщик копирует файлы и настраивает вашу установку LAMPStack.

<img src="https://docs.joomla.org/images/b/bc/Lampstackfinalscreen.png" decoding="async" data-file-width="516" data-file-height="391" width="516" height="391" alt="Финальный экран Bitnami lampstack" />

BitNami LAMPStack теперь настроена и готова к использованию. Нажмите "Завершить", чтобы запустить приложение.

### Установка Joomla! вручную

Следуйте инструкциям, изложенным в статье Установка Joomla.

*Переведено с помощью openai.com*

