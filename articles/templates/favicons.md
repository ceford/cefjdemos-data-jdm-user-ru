<!-- Filename: J4.x:Favicons / Display title: Фавиконы -->

## Фавиконы Joomla!

Фавиконы — это маленькие иконки, которые появляются на вкладке браузера рядом с именем вашего сайта. Ближе к началу файла шаблона index.php находятся три инструкции для загрузки фавиконов на страницу:
```php
    // Браузеры поддерживают SVG фавиконы
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon.svg', '', [], true, 1), 'icon', 'rel', ['type' => 'image/svg+xml']);
    $this->addHeadLink(HTMLHelper::_('image', 'favicon.ico', '', [], true, 1), 'alternate icon', 'rel', ['type' => 'image/vnd.microsoft.icon']);
    $this->addHeadLink(HTMLHelper::_('image', 'joomla-favicon-pinned.svg', '', [], true, 1), 'mask-icon', 'rel', ['color' => '#000']);
```
Для шаблона Cassiopeia Joomla будет искать фавиконы в следующих местах:

1.  **media/templates/site/cassiopeia/images** - их там нет, поэтому Joomla будет искать в следующем месте.
2.  **media/system/images** - они там есть, поэтому Joomla будет использовать их оттуда.

Если вы хотите использовать свои собственные фавиконы вместо фавиконов Joomla, загрузите их в первое место:
**media/templates/site/cassiopeia/images**. Вы можете сделать это, используя форму Настройка шаблонов. Они не будут затронуты обновлением шаблона Cassiopeia.

Фавиконы иногда используются в большем размере и в местах, отличных от вкладки браузера. Например, вот снимок экрана части стартовой страницы Firefox, показывающий некоторые из избранных мест Пользователя:

![примеры фавиконов со стартовой страницы Firefox](../../../en/images/templates/favicons-firefox-start-collection.png)

Все современные браузеры поддерживают SVG иконки, поэтому вам следует сделать создание SVG иконки приоритетной задачей.

## О SVG

SVG — это аббревиатура от Scalable Vector Graphics (масштабируемая векторная графика). Файл SVG содержит текст в формате, который определяет расположение и форму линий с цветами линий, цветов заливки и так далее. Следующий скриншот показывает файл *joomla-favicon.svg*, открытый в текстовом редакторе. Номера строк создаются текстовым редактором. В файле они отсутствуют. Длинные строки представляют собой кривые и здесь обрезаны для удобства отображения.

![содержимое текста joomla favicon](../../../en/images/templates/favicons-joomla-favicon-svg-text.png)

Чтобы создать файл SVG, необходимо использовать подходящее приложение, такое как Inkscape. Приложения для растровой графики, такие как Photoshop или GIMP, не подходят. Если вы предпочли бы разработать значок в приложении для растровой графики или у вас уже есть существующий логотип в растровом формате, который можно адаптировать для значка, вы можете импортировать получившийся PNG файл в Inkscape и там обвести его, чтобы создать файл SVG. Обведенное изображение должно быть удалено после обводки!

Фактическое создание SVG favicon выходит за рамки этой статьи. Создание стандартного файла *favicon.ico* из файла *joomla-favicon.svg* очень просто — множество сайтов делают это онлайн бесплатно.

## Как создать фавиконы

Если вы хотите создать собственные фавиконы, лучший способ сделать это — создать SVG-фавикон, а затем использовать онлайн-инструмент для генерации всех остальных форматов, используя его в качестве входных данных. В этом примере требуется иконка, подходящая для дочернего шаблона под названием Cassiopeia Green. Иконка должна быть квадратной и не слишком сложной, так как минимальный размер отображения составляет 16x16 пикселей. Некоторые устройства требуют более высоких разрешений, таких как 32x32 или 180x180, а Google рекомендует кратные значения 48x48 пикселей. Если вы начнете с SVG, вам не нужно беспокоиться об этом - просто создайте почти квадратное изображение с подходящим дизайном. В этом примере фавикон будет представлять собой буквы *J4* темно-зеленого цвета.

### Inkscape

Inkscape — это бесплатное кроссплатформенное приложение для работы с векторной графикой, использующее открытый исходный код и предназначенное для работы с файлами SVG. Оно работает на Linux, Mac и Windows. Перейдите на сайт Inkscape (inkscape.org), чтобы скачать копию для вашей платформы. Следующие иллюстрации показывают экран Inkscape на одном из этапов выполнения нижеуказанных инструкций.

![inkscape с фавиконом в подготовке](../../../en/images/templates/favicons-inkscape-favicon.png)

### Создание SVG

1.  Запустите Inkscape и сделайте окно удобного размера: выберите Вид / Увеличение / Увеличение страницы
2.  Выберите инструмент "Текст", обозначенный буквой A на левой панели инструментов
3.  Выберите Arial, Нормальный, 48 и px
4.  Переместите мышь, чтобы определить рамку в любом месте страницы
5.  Введите текст: J4
6.  Выберите Вид / Масштабирование выделенного
7.  Выберите Контур / Объект в контур — видимых изменений не будет, но слова больше не будут текстом
8.  Выберите Файл / Свойства документа
9.  Выберите Изменить размер под содержимое
10. Удалите масштаб, чтобы лучше видеть, но убедитесь, что все буквы по-прежнему выделены
11. Установите значение высоты такое же, как у ширины. Введите это!
12. Закройте диалоговое окно Свойства документа
13. Снова выберите Вид / Увеличение страницы — символы нужно центрировать
14. Правка / Выбрать все
15. Объекты / Выровнять и распределить
16. Переместите выбор как группу / Относительно страницы / Центровка по горизонтали — вы должны увидеть перемещение J4 в вертикальную среднюю точку
17. Выберите панель "Заливка и обводка" справа — правая панель имеет выпадающий список, обозначенный вниз-указанной стрелкой
18. В панели "Заливка и обводка" выберите значок "Заливка" и первое заполненное поле
19. В панели RGB введите 006400ff в поле RGBA в нижнем правом углу — это код CSS-стиля *darkgreen*
20. Файл / Сохранить
21. В диалоговом окне сохранения введите подходящее имя файла, например green-favicon-j4.svg
22. Выберите подходящее местоположение, например *~/Documents/joomla-dev/svgs*
23. Выберите Оптимизированный SVG (*.svg*) из выпадающего списка в нижней части формы.
24. Выберите *Сохранить*
25. Выберите *OK* для всех параметров по умолчанию в форме выхода оптимизированного SVG.
26. Закройте SVG, над которым вы работаете — у вас будет возможность сохранить изображение в формате Inkscape, но в этом нет необходимости.

### Редактирование SVG с текстовым редактором

Запустите ваш любимый текстовый редактор, чтобы сделать изменения, которые были невозможны в Inkscape.

1.  Откройте свой только что созданный SVG-файл — обратите внимание, что первая строка представляет собой спецификацию XML
2.  Вы можете удалить вторую строку — это комментарий, содержащий "Создано с помощью Inkscape"
3.  Если присутствует, вы можете удалить строку, содержащую текст, поскольку его нет
4.  Откройте оригинальный joomla-favicon.svg файл — он находится в *joomla_root/media/system/images*
5.  Скопируйте блок стилей и вставьте его в свой SVG на строке, следующей за заявлением SVG
6.  Закройте оригинальный файл *joomla-favicon-svg*, чтобы избежать случайных изменений в нем
7.  В блоке стилей вашего собственного SVG-файла измените path {fill: \#000;} на path {fill: \#006400;}, значение в строке
8.  Удалите *fill="#006400"* из строки
9.  Сохраните
10. Откройте изображение в вашем браузере. Для Firefox это Файл / Открыть файл...

Вы должны увидеть изображение в вашем браузере. Пример показывает J4 размером 47 пикселей квадрат. Следующий этап — создать другие типы иконок, которые вам понадобятся, используя ваше вновь созданное SVG как мастер.

### Онлайн обработка

Перейдите на сайт Real Favicon Generator. Существуют и другие сайты, но этот кажется особенно всеобъемлющим.

1.  Выберите кнопку с надписью *Выберите изображение фавикона*
2.  Сайт покажет вам ваше главное изображение. Он также сообщает, что *Ваше изображение не квадратное (688x512). Мы можем это исправить, добавив прозрачные поля*
3.  Выберите кнопку *Продолжить с этим изображением* под главным изображением.
4.  Существуют подформы с бледно-голубыми фонами для нескольких типов иконок — заполните каждую из них, проверяя, что предпросмотр соответствует вам.
5.  Лучше придерживаться настроек по умолчанию в параметрах генератора фавиконов, если вы не знаете лучше. За исключением:
6.  Путь, выберите вариант "Я не могу..." и введите: *media/templates/cassiopeia-green/images*
7.  Выберите кнопку *Сгенерировать ваши фавиконы и HTML-код*
8.  После короткой задержки появится новая форма, выберите кнопку "Скачать ваш пакет: *Favicon*"
9.  Сохраните скачанное...
10. Выберите и скопируйте блок ссылок, чтобы сохранить где-нибудь.
11. Закройте сайт онлайн обработки

Скачанный файл представляет собой *zip* файл, содержащий 10 элементов: *favicon.ico*, *safari-pinned-tab.svg*, шесть PNG файлов, *browserconfig.xml* и *site.webmanifest*.

### Размещение

Чтобы использовать стандартный набор фавиконов Joomla, необходимо переименовать и переместить иконки в *joomla_root/media/templates/yourtemplate/images*:

- Ваше основное SVG изображение, *green-favicon-j4.svg*, необходимо переименовать в *joomla-favicon.svg*
- Скачанный файл *safari-pinned-tab.svg* нужно переименовать в *joomla-favicon-pinned.svg*
- Скачанный файл *favicon.ico* просто нужно переместить

### Блок ссылок

Блок ссылок, скопированный ранее, содержит:

```html
<link rel="apple-touch-icon" sizes="180x180" href="media/templates/cassiopeia-green/images/apple-touch-icon.png">
<link rel="icon" type="image/png" sizes="32x32" href="media/templates/cassiopeia-green/images/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="media/templates/cassiopeia-green/images/favicon-16x16.png">
<link rel="manifest" href="media/templates/cassiopeia-green/images/site.webmanifest">
<link rel="mask-icon" href="media/templates/cassiopeia-green/images/safari-pinned-tab.svg" color="#5bbad5">
<link rel="shortcut icon" href="media/templates/cassiopeia-green/images/favicon.ico">
<meta name="msapplication-TileColor" content="#ffc40d">
<meta name="msapplication-config" content="media/templates/cassiopeia-green/images/browserconfig.xml">
<meta name="theme-color" content="#ffffff">
```

Возможно, вам не нужно использовать его!

*Переведено openai.com*
