<!-- Filename: Entering_raw_HTML_in_editors / Display title: Фильтры HTML -->

## HTML Тег Текстовое Поле

В HTML многострочное поле ввода называется текстовым полем. Любой текст между открывающим и закрывающим тегами отображается как текст, который может содержать HTML-разметку. Пример:
```
<textarea><p class="poem">Быстрая коричневая лиса<br>
перепрыгивает через ленивую собаку.</textarea>
```
Редакторы, такие как TinyMCE или Code Mirror, используют JavaScript для наложения на текстовое поле другого отображения, чтобы обеспечить ввод данных WYSIWYG или подсветку синтаксиса. Кнопка переключения под полем редактора переключает между видом текстового поля и WYSIWYG видом.

Виды редактора используются для содержимого статей и некоторых модулей. Однако, необходимо учитывать, что не все HTML-теги и атрибуты (такие как class="xyz") разрешены для всех пользователей. Некоторые или все они могут исчезнуть, когда вы сохраняете содержимое текстового поля или поля редактирования.

Это происходит из-за механизмов фильтрации, как в Глобальной конфигурации Joomla!, так и в конфигурации редактора. Фильтр редактора можно обойти, выбрав *Без редактора* в настройках вашего *Профиля пользователя*. Вы не можете обойти глобальные фильтры, но можете изменить их, чтобы они подходили для целей вашего сайта.

## Выбор редактора пользователя

Вы можете выбрать один из доступных редакторов, включая "Нет", из вашего профиля пользователя, доступного через меню Учетная запись пользователя / Редактировать профиль в верхнем правом углу экрана администратора. Форма "Редактировать: профиль" содержит вкладку "Основные настройки" с полем для выбора редактора. Обычно она установлена на *- Использовать по умолчанию -*, что обычно означает TinyMCE. Вы можете выбрать *Редактор Нет*. Это обойдет любое фильтрование HTML-тегов и атрибутов, не разрешенных настройками конфигурации TinyMCE.

**Предупреждение:** если вы выберете *Редактор - Нет* для создания контента, содержащего HTML-теги, не разрешенные фильтром редактора, а затем переключитесь обратно на редактор по умолчанию, вам следует быть осторожным, чтобы не редактировать и не сохранять этот контент снова, иначе вы потеряете любые отфильтрованные теги и атрибуты. Это легко сделать по ошибке, и предупреждения нет.

## Глобальная конфигурация: текстовые фильтры

На главной панели инструментов выберите «Глобальная конфигурация», а затем вкладку «Текстовые фильтры». По умолчанию для групп пользователей «Гость», «Публичный» и «Зарегистрированный» выбрана настройка *Нет HTML*. Любая из этих групп может иметь возможность заполнить текстовое поле, например, в контактной форме, которая запрашивает дополнительную информацию о проблеме, поэтому автоматическое удаление всех HTML-тегов обычно уместно. Другие группы, кроме суперпользователей, ограничены стандартным списком запрещенных элементов. Суперпользователи не имеют фильтрации.

![глобальная конфигурация текстовых фильтров](../../../en/images/configuration/global-configuration-filters-tab.png)

Примечания объясняют, что включено в стандартный список запрещенных элементов и как использовать другие списки.

## Конфигурация TinyMCE для текстовых фильтров

Редакторы реализованы как плагины в Joomla. Редактор CodeMirror не имеет настроек текстовых фильтров. Чтобы настроить редактор TinyMCE, найдите и выберите его в списке плагинов. Примерно в середине длинного списка настроек вы увидите поле с надписью *Использовать текстовый фильтр Joomla*, которое по умолчанию **выключено**. Следующие три поля:

* **Запрещенные элементы** — список тегов, которые всегда будут удалены. Стандартный список *script, applet, iframe* все имеют проблемы с безопасностью.
* **Допустимые элементы** — используйте этот список, чтобы ограничить допустимые теги подмножеством всех общих HTML-тегов. Пример: `a[href|target=_blank],strong/b,div[align],br`
* **Расширенные допустимые элементы** — используйте этот список, чтобы добавить элемент в существующий набор правил по умолчанию или изменить элемент в наборе правил по умолчанию. Пример: `img[class|src|border=0|alt|title|hspace|vspace|width|height|align|onmouseover|onmouseout|name]`

См. документацию TinyMCE для более подробного объяснения.

Чтобы обойти текстовые фильтры TinyMCE и использовать текстовые фильтры Joomla, установите *Использовать текстовый фильтр Joomla* в **Вкл**. Три дополнительных поля, описанных выше, исчезнут, так как они не используются.

*Переведено с помощью openai.com*

