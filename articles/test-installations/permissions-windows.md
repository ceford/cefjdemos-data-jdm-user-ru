<!-- Filename: How_do_Windows_file_permissions_work? / Display title: Разрешения файлов: Windows  -->

## Введение

Для тех из вас, кто разрабатывает или обслуживает свои сайты на Joomla! из среды Windows, иногда бывает сложно получить релевантную информацию о разрешениях. К сожалению, факт таков, что большинство веб-сервисов предоставляется на Unix, и этот процесс довольно хорошо задокументирован в данной среде. Надеемся, что следующая информация поможет развеять некоторое замешательство и предоставит небольшое руководство. 

## Обзор веб-серверов Windows

Во-первых, давайте обсудим различия между серверами. В целом, большинство пользователей Windows, как представляется, используют либо Apache (Win32), либо Microsoft IIS. Эти два веб-сервера работают очень по-разному и используют слегка отличающиеся модели доставки. Apache (Win32) обычно запускается на хост-компьютере от имени пользователя, под которым он был установлен, тогда как IIS устанавливается под определённого пользователя, но будет запускаться под недавно созданным пользователем *IUSR_*.

## Разрешения по умолчанию

По умолчанию Unix, как правило, предоставляет полный доступ к файлам и каталогам только *владельцу*. В отличие от Unix, Windows по умолчанию также назначает группе *Все* полные разрешения. Первое, что сделает любой грамотный администратор Windows, — это удалить права группы *Все* для повышения безопасности. Для тестирования на локальном ПК это, вероятно, не нужно, но это объясняет, почему, если *Все* не удалено и вы запускаете какой-либо скрипт проверки разрешений или проверку перед установкой Joomla!, у вас будут полные права на *чтение, запись и выполнение*. Вы получаете права группы *Все*.

## Microsoft Internet Information Server (IIS)

IIS выпускается в двух основных вариантах: PWS (личный веб-сервер) и IIS (сервер интернет-информации). По сути, это одно и то же приложение. PWS — это урезанная версия IIS, предназначенная для настольных сред, тогда как IIS предназначен для серверных сред. PWS ограничивает вас одним основным веб-сайтом, поэтому ваши приложения обычно будут установлены в поддиректориях основного веб-сайта. IIS, с другой стороны, предоставляет возможность запускать виртуальные хосты из этих директорий, обеспечивая многосайтовую функциональность.

Из-за различий в функциональности PWS не имеет *Мастера разрешений*, так как считается, что это не требуется. Только один пользователь будет использовать сервер PWS. В IIS сервер будет использоваться многими пользователями, поэтому необходимы разные назначения разрешений.

Когда учетная запись *Everyone* удалена, в Windows IIS остается учетная запись *IUSR_**, обладающая полными правами на директории веб-сервера. Проверка разрешений теперь должна показать другие результаты. Только учетная запись *IUSR_** имеет полные разрешения, а другие пользователи должны иметь либо *Только чтение*, либо никаких прав. Права определяются тем, какие права другим пользователям были вручную назначены для директорий IIS.

### Назначение разрешений

Назначение разрешений в Windows достаточно простое, но иногда может быть несколько запутанным. Щелкните правой кнопкой мыши по соответствующей папке или файлу. Выберите *Свойства* или *Общий доступ и безопасность*, чтобы зайти в панель управления безопасностью Windows. Выберите (однократный клик) любое имя пользователя из списка, чтобы увидеть права этого пользователя в нижней части панели. Некоторые права могут быть *серым цветом*. Они недоступны, либо потому что текущий пользователь (под которым вы вошли) не имеет достаточно высоких разрешений для их изменения, либо они наследуются от вышестоящей директории и настроены на использование разрешений этой вышестоящей директории. (Это, как правило, механизм по умолчанию.)

Как видно, Windows использует следующую схему разрешений/прав:

| # | Управление | Разрешает # |
| :---:        |:-----   | :--- |
| 1.| Полный контроль | Разрешает: 1, 2, 3, 4, 5, 6, 7 |
| 2.| Изменение | Разрешает: 2, 3, 4, 5, 6 | |
| 3.| Прочитать и выполнить | Разрешает: 3, 4 | |
| 4.| Список содержимого папки | Разрешает: 4 (но программы не могут выполняться) | |
| 5.| Чтение | Разрешает: 5 (означает: 4) | |
| 6.| Запись | Разрешает: 6 (означает: 4) | |
| 7.| Особые разрешения | Разрешает: комбинации |

### Свойства разрешений файлов Windows

Разрешения файлов Windows можно рассматривать как имеющие сходные свойства с разрешениями файлов UNIX или Linux (режимы). Они просто представлены по-разному. Например, если вы в основном являетесь пользователем Unix/Linux, вы, вероятно, привыкли к представлению разрешений как 644/666 755/777, вместо описания их, как выше. Итак, когда вы используете 644, это означает:

- Владелец этого файла может читать и записывать его.
- Группа владельца может читать файл.
- Все остальные могут читать файл.

**Примечание:** Разрешения Windows и Unix (списки управления доступом) не совмещаются точно; Windows не использует механизм *групп* таким же образом. Для этого обсуждения и в отношении среды веб-хостинга они могут быть приравнены. Однако в Windows *Группы* не используются, и *Everyone* должна была быть удалена. Здесь Windows и Unix не совсем совмещаются, но можно *сопоставить* или *согласовать* эквиваленты значений.

Этот обзор не даст вам конкретного руководства по разрешениям для Windows или NTFS, а больше понимания того, как номера разрешений в стиле UNIX/Linux связываются с машиной с файловой системой NTFS. Файлы, которые помещены в корневую папку `www` или `public_html`, или любую другую директорию, на которую указывает ваш сайт (`www.domain.com` или `localhost`) на жестком диске, должны принадлежать вашему пользовательскому аккаунту, но только если этот пользователь не считается привилегированным, например, "Администратор" в Windows или "root" в UNIX/Linux. Эти учетные записи предоставляют слишком много доступа и не должны использоваться для повседневных задач.

### Лучшие практики

Обычно используемые принципы безопасности предполагают, что все **файлы** должны иметь следующие разрешения.

- **Владелец** Читать и записывать
- **Группа** Только чтение
- **Другие** Только чтение

Все **директории/папки** должны иметь следующие разрешения.

- **Владелец** Читать, записывать и выполнять
- **Группа** Читать и выполнять
- **Другие** Читать и выполнять

Можно утверждать, что это не является *оптимальной* безопасностью, но необходимо соблюдать баланс между безопасностью, функциональностью и поддерживаемостью.

Windows, в отличие от Unix, не поддерживает отдельный ACL для *выполнения*, а просто предоставляет *чтение и выполнение* в комбинации, что не подразумевает *запись*. Однако, *чтение и выполнение* ACL подразумевает *показать содержимое директории*. Поэтому, если у вас есть только разрешения *чтения и записи* на директории, но не *выполнение*, вы не сможете увидеть содержимое директории и могут возникнуть проблемы при попытке выполнить файл через веб-браузер. Чтобы полностью сопоставить/согласовать их с разрешениями Windows, требуется некоторое понимание разрешений UNIX/Linux. Следующая таблица должна помочь:

| Режим Unix   | ACL Windows | Комментарии|
|:-----------:| :----   | :--- |
| 7 | Изменение| Чтение, запись и выполнение, вы должны быть владельцем этого файла | 
| 6 | Читать и записывать | | 
| 5 | Читать и выполнять| используется для большинства приложений | 
| 4 | Только чтение | безопасность за счет скрытности — не самая лучшая практика | 
| 3 | Писать и выполнять | не доступно через Windows, если только не используются *особые* разрешения, что не является распространенным | 
| 2 | Только писать | не доступно через Windows, если только не используются *особые* разрешения, что не является распространенным | 
| 1 | Только выполнение | (не доступно через Windows, если только не используются *особые* разрешения, что не является распространенным) |

В сравнении с режимами Unix, когда вы видите что-то вроде 644, разделите это на три элемента:

Первое число представляет разрешения владельца, второе — разрешения группы, и третье — разрешения других. Эквивалент Windows будет:

- **Владелец** (6) Читать и записывать
- **Группа** (4) Только чтение
- **Другие** (4) Только чтение

Надеемся, что этот пример дает некоторое понимание того, как коррелировать режимы/разрешения Unix с разрешениями Windows/ACL. Этот документ не включает более сложные темы, такие как *эффективные*, *наследуемые* или *особые* разрешения. Несмотря на удобство использования Windows, механизмы разрешений и ACL Microsoft на самом деле довольно сложны и обширны, но это может дать вам краткое руководство, чтобы уменьшить путаницу, связанную с переводом разрешений между Unix и Windows.

*Переведено openai.com*

