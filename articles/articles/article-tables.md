<!-- Filename: J4.x:Article_Tables / Display title: Статья: Редактирование - Таблицы  -->

## О таблицах

В HTML таблицы состоят из строк и столбцов ячеек. Например, простая таблица может состоять из 4 строк и 4 столбцов, что дает 16 ячеек. Тем не менее, ячейки могут быть объединены либо горизонтально, либо вертикально, чтобы создать достаточно сложные структуры таблиц. У таблиц также есть не столь очевидные характеристики, такие как заголовок, тело, подвал и подписи. Таблицы могут быть вложенными!

По умолчанию ячейки таблицы расширяются, чтобы вместить свое содержимое. Единственное стилевое оформление происходит из разметки таблицы: по умолчанию ячейки заголовка (`<th>`) имеют жирный, центрированный текст, в то время как ячейки данных (`<td>`) имеют обычный, выровненный по левому краю текст.

Использование таблиц следует ограничить строго табличными данными, такими как расписание или календарь, где важно сохранить структуру строк и столбцов. Таблицы не следует использовать для компоновки, такой как размещение изображений или текста рядом друг с другом.

Больше информации можно найти в следующих статьях:

- [Основы таблиц](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Basics)
- [Продвинутые функции и доступность](https://developer.mozilla.org/en-US/docs/Learn/HTML/Tables/Advanced)
- [Стилизация таблиц](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Styling_tables)

Таблицы — это дилемма! Если вставить таблицу с помощью инструментов таблиц в TinyMCE, таблица будет выглядеть хорошо на экране редактирования и на сайте, но макет достигается с помощью встроенных стилий CSS, которые могут быть объемными и трудными для редактирования. Если таблица вставлена как чистый HTML, результат выглядит не очень хорошо в текстовом редакторе TinyMCE, но это позволяет использовать классы Bootstrap и выглядеть гораздо лучше на сайте. Обе методы разобраны ниже.

## Вставка таблицы с помощью инструментов TinyMCE

Чтобы начать работу с таблицей:

- Откройте статью, которую вы хотите отредактировать.
- Установите курсор на пустую строку в том месте, где должна появиться таблица.
- В первой строке инструментов TinyMCE выберите кнопку *Table* (Таблица).
- В выпадающем меню выберите Table (Таблица), затем передвиньте курсор, чтобы определить количество строк и столбцов. Также можно использовать клавиши со стрелками.
- Выберите последнюю ячейку в матрице 4x4.
- Заполните ячейки таблицы.

Опции редактирования:

- Вы можете вставить строку выше или ниже выделенной ячейки.
- Вы можете вставить столбец перед или после выделенной ячейки.
- Вы можете удалить строку или столбец.
- Вы можете перетащить границы столбцов, чтобы изменить ширину или высоту столбцов.
- Вы можете объединять ячейки - выделите ячейки, перетащив по ним курсор, затем используйте Table -> Cell -> Merge cells (Таблица -> Ячейка -> Объединить ячейки).
- Вы можете выбрать Свойства таблицы, включая ширину границы, стиль и цвет, а также цвет фона.

Если вы используете кнопку переключения редактора, вы увидите, что разметка достигнута с помощью встроенных стилей для каждой строки и каждой ячейки. Вот короткий пример:

```html
<table style="border-collapse: collapse; width: 100%; height: 96px;" border="1"><colgroup><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"><col style="width: 24.9735%;"></colgroup>
<tbody>
<tr style="height: 24px;">
<td style="height: 24px;">День</td>
<td style="height: 24px;">Утро</td>
<td style="height: 24px;">День</td>
<td style="height: 24px;">Вечер</td>
</tr>
<tr style="height: 24px;">
<td style="height: 24px;">Вторник</td>
<td style="height: 24px;">Добро пожаловать</td>
<td style="height: 24px;">Презентации</td>
<td style="height: 24px;">Барбекю</td>
</tr>
...
</tbody>
</table>
```

## Вставка таблицы в виде HTML

Если вы предпочитаете, вы можете отказаться от встроенных стилей и использовать классы Bootstrap. Вам потребуется изменить таблицу, созданную с помощью инструментов таблицы TinyMCE, или набрать ее самостоятельно. Она будет выглядеть так:

```html
<div class="table-responsive">
<table class="table table-striped table-bordered table-group-divider">
<thead>
<tr>
<th>День</th>
<th>Утро</th>
<th>День</th>
<th>Вечер</th>
</tr>
</thead>
<tbody class="table-group-divider">
<tr>
<th>Вторник</th>
<td>Добро пожаловать</td>
<td>Презентации</td>
<td>Барбекю</td>
</tr>
...
</tbody>
</table>
</div>
```

Здесь классы Bootstrap оказывают следующие эффекты:

- `table` - применяет несколько стилей, чтобы создать приятный стандартный макет таблицы.
- `table-striped` - чередует темные и светлые строки.
- `table-bordered` - применяет границы к ячейкам.
- `table-group-divider` - добавляет жирную линию над элементом.
- `table-responsive` - позволяет прокручивать широкую таблицу справа налево.

Следующий скриншот сайта показывает таблицу программы конференции с
встроенными стилями по умолчанию TinyMCE и аналогичную таблицу с классами Bootstrap:

![Пример таблиц](../../../en/images/articles/articles-site-tables.png)

Смотрите документацию Bootstrap по [Таблицам](https://getbootstrap.com/docs/5.3/content/tables/) для получения дополнительных опций.  

## Дополнение

Вы можете разместить HTML-код для таблицы в Пользовательском модуле и включить этот модуль в статью. В статье это отображается как `{loadmoduleid xx}`, где xx — это ID модуля.

*Переведено с помощью openai.com*

