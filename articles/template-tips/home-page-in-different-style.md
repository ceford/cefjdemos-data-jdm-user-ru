<!-- Filename: J4.x:Home_Page_in_Different_Style / Display title: Домашняя страница в другом стиле  -->

## Главная страница сайта

Для выбора главной страницы сайта из любого типа пункта меню нужно выбрать серый значок в колонке «Домой» в любом списке пунктов меню. Попробуйте внести изменения! Просмотрите изменения на вашем сайте в отдельной вкладке или окне браузера. Вы без труда сможете вернуться к исходному варианту. Если вы хотите, чтобы ваша главная страница выглядела уникально, то можете выбрать тип меню с одним элементом, тип меню с блогом категории, тип меню с избранными статьями или что-то другое.

Предположим, вы хотите, чтобы ваша главная страница имела отличительный вид, слегка отличающийся от всех других страниц на вашем сайте. Существует множество различных методов, чтобы настроить внешний вид главной страницы:

- Через модули, назначенные только для главной страницы.
- Через пользовательские стили.
- Через переопределение шаблона или макет.
- Через отдельный шаблон или дочерний шаблон, используемый только для пункта меню главной страницы.
- Еще больше...?

## Пример: Пример данных Cassiopeia

Пример данных Cassiopeia создает домашнюю страницу, используя тип пункта меню **Статьи в фокусе**. Она оформлена в соответствии с изображением на скриншоте ниже (некоторые незначительные изменения были внесены в отдельные статьи для лучшего скриншота здесь).

![домашняя страница с использованием cassiopeia и примера данных](../../../en/images/templates/templates-home-page-style-cassiopeia-sample-data.png)

Вот как достигается эта компоновка:

### Модуль изображений

Большое изображение под меню находится в настраиваемом модуле с именем Image, назначенном положению баннера в шаблоне Cassiopeia.

![настраиваемый модуль, используемый в стиле примерных данных](../../../en/images/templates/templates-home-page-style-custom-module-image.png)

Вкладка назначения меню: модуль назначен только для домашней страницы:

![вкладка назначения меню настраиваемого модуля](../../../en/images/templates/templates-home-page-style-custom-module-menu-assignment.png)

Фоновое изображение выбрано на вкладке Опции формы редактирования модулей: Настраиваемый.

На вкладке Расширенные / поле Компоновка выбран элемент `баннер`. Компоновка баннера является компоновкой шаблона:

### Компоновка шаблона

Компоновка модуля по умолчанию в `siteroot/modules/mod_custom/tmpl/default.php` не отображает модуль так, как хотелось бы. Существует альтернативная компоновка в `siteroot/templates/cassiopeia/html/mod_custom/banner.php`. Поскольку `banner.php` отсутствует в коде настраиваемого модуля, он работает как компоновка, которую вы можете выбрать, а не как переопределение, которое всегда используется. В модуле изображения вы можете выбрать компоновку по умолчанию, сохранить и перезагрузить сайт, чтобы увидеть разницу. Переключитесь обратно на компоновку баннера и снова сохраните, чтобы восстановить нормальное поведение.

Существуют отдельные статьи о переопределениях и компоновках.

### Модуль Newsflash

Под большим изображением находятся три маленькие коробки, каждая с изображением и текстом под ним. Они создаются с использованием модуля Статьи - Newsflash в верхнем положении шаблона-а. Модуль настроен на отображение 3 элементов. Его назначение меню - только домашняя страница. Вкладка Расширенные имеет Компоновку, установленную на горизонтальную, и Стиль модуля - на noCard.

![модуль newsflash](../../../en/images/templates/templates-home-page-style-newsflash-module-image.png)

Это завершает объяснение того, как была создана домашняя страница с использованием примерных данных Cassiopeia.

## Дополнительные Опции

Вы можете захотеть сделать больше. Например, изменить цветовую схему для домашней страницы, добавить водяной знак или создать пользовательский макет. Вот несколько идей:

### Отображение Страницы

В меню: форма редактирования пункта для домашнего меню, выберите вкладку "Отображение страницы". Поле "Класс страницы" обычно пустое. Все, что вводится здесь, становится дополнительным классом в

элементе страницы. Например, ввод `fancyhome` приводит к следующему выводу на домашней странице только для этой страницы:
```html
<body class="site com_content wrapper-static view-featured no-layout no-task itemid-101 fancyhome has-sidebar-right">
```
Затем вы можете создать файл user.css через **Система → Шаблоны Сайта → Cassiopeia Подробности и Файлы**. Выберите кнопку `Новый файл` и создайте user.css в папке css. Затем введите стили в форме редактирования user.css. Пример:
```css
    .fancyhome {
      background-color: #f8fff8;
    }
```
Это наделит домашнюю страницу светло-зеленым фоном. Используйте \#f8f8ff; для светло-голубого фона или \#ffffee для светло-желтого. Вы можете делать множество других вещей со своим стилем fancyhome, но вам нужны хорошие знания css.

### Альтернативные Шаблоны Главной Страницы

Вы можете установить альтернативные шаблоны сайта, полученные от сторонних поставщиков шаблонов. И вы можете создать дочерние шаблоны, которые действуют аналогично. В любом случае вы можете выбрать, какой шаблон будет использоваться по умолчанию для всех страниц, а какой только для домашней страницы.

- Выберите **Система → Стили Шаблонов Сайта** в администраторском меню.
- Выберите шаблон, который вы хотите использовать для домашней страницы. Это должен быть один из тех, что не выбран как шаблон по умолчанию.
- На вкладке "Назначение в Меню" выберите только элемент домашнего меню. Все, что не выбрано здесь, все равно будет использовать ваш шаблон по умолчанию.
- Вы можете выбрать некоторые параметры на вкладке "Дополнительно", но они различаются для каждого шаблона и здесь не рассматриваются.

Существуют и другие статьи по настройке Cassiopeia.

*Переведено с помощью openai.com*

