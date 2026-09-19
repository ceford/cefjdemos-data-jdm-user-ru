<!--
{
    "source": "https://docs.joomla.org/category-list-override.md",
    "title": "\u041f\u0435\u0440\u0435\u043e\u043f\u0440\u0435\u0434\u0435\u043b\u0435\u043d\u0438\u0435 \u0441\u043f\u0438\u0441\u043a\u0430 \u043a\u0430\u0442\u0435\u0433\u043e\u0440\u0438\u0439",
    "description": "\u0423\u0437\u043d\u0430\u0439\u0442\u0435, \u043a\u0430\u043a \u0441\u043e\u0437\u0434\u0430\u0442\u044c \u043f\u0435\u0440\u0435\u043e\u043f\u0440\u0435\u0434\u0435\u043b\u0435\u043d\u0438\u0435 \u0448\u0430\u0431\u043b\u043e\u043d\u0430, \u0447\u0442\u043e\u0431\u044b \u0443\u043b\u0443\u0447\u0448\u0438\u0442\u044c \u043c\u0430\u043a\u0435\u0442 \u0441\u043f\u0438\u0441\u043a\u0430 \u043a\u043e\u043d\u0442\u0430\u043a\u0442\u043e\u0432 \u0432 \u043a\u0430\u0442\u0435\u0433\u043e\u0440\u0438\u0438 ",
    "author": ""
}
-->

## Список контактов в категории

Макет контактов в категории по умолчанию управляется шаблоном в коде компонента 
com_contacts. Макет по умолчанию выглядит так:

![комитет по культуре с использованием макета и стиля по умолчанию](../../../en/images/contacts/category-list-override/01-contacts-culture-committee.png)

Возможно, это личное мнение, но для меня макет контактов по умолчанию не вполне 
удовлетворителен. Мои замечания:

* Исходные портретные изображения имели ширину 500 пикселей и слишком сильно привлекали внимание.
* Имя контакта недостаточно выделено.
* Маркированный список личных данных не имеет заголовка и выглядит изолированным.
* Роль человека не имеет заголовка.
* Поля адреса и почтового индекса отсутствуют.
* Данные о местоположении неполны.
* Данные каждого контакта размещены в таблице и довольно тесно расположены на узких экранах.

Как же исправить это по своему вкусу? Моё решение — создать переопределение шаблона 
и добавить несколько пользовательских стилей. Вот результат:

![деловой комитет с использованием переопределения шаблона и пользовательских стилей](../../../en/images/contacts/category-list-override/02-contacts-business-committee.png)

## Переопределение макета шаблона

Папка com_contact/tmpl/category содержит три PHP-файла: default.php,
default_children.php и default_items.php. Последний файл в этом списке содержит
табличный макет списка.

Файлы переопределения создаются через System / Site Templates / Cassiopeia
Details and Files / Create Overrides. Выберите com_contact, а затем category.
После этого папка html будет содержать com_contact/category с тремя упомянутыми
выше файлами шаблона. 

### Изменение файла default.php на mydefault.php

Файл `default.php` содержит строку, указывающую, какой макет использовать для 
каждой отдельной записи. Выберите этот файл для редактирования и **переименуйте** его в 
`mydefault.php` (или используйте любой другой префикс вместо `my`). Не используйте 
символ подчёркивания в имени файла!

Позже, когда вы откроете форму Contacts / Category / Edit, поле Layout на вкладке Options 
позволит выбрать макет компонента или макет переопределения.
Это выглядит так:

```
---From Global Options---
  Use Global
---From Component---
  Default
---From cassiopeia Template---
  mydefault

```

### Редактирование файла mydefault.php

Строка 20 файла `mydefault.php` содержит `$this->subtemplatename = 'items';`.
Замените `items` на `myitems`, чтобы строки с 18 по 23 выглядели следующим образом:

```html
<div class="com-contact-category">
    <?php
        $this->subtemplatename = 'myitems';
        echo LayoutHelper::render('joomla.content.category_default', $this);
    ?>
</div>
```

### Изменение файла default_items.php на mydefault_myitems.php

Файл `default_items.php` содержит макет каждого контакта. Его необходимо
переименовать, чтобы сохранить возможность использовать исходный макет. Первая часть имени
не имеет значения. Для макета используется часть `myitems`, упомянутая в
файле `mydefault.php`.

### Редактирование файла mydefault_myitems.php

Раздел `<table>...</table>` этого файла занимает строки с 85 по 204. Для
переопределения макета я заменил разметку таблицы следующей разметкой сетки Bootstrap. На узких экранах три столбца располагаются друг под другом. На экранах шириной более
768 пикселей столбцы располагаются рядом. В изменённой разметке пользовательские
поля перемещены под имя контакта.

```
<div class="container-fluid text-center border border-2">
<?php $nrows = 0; foreach ($this->items as $i => $item) : ?>
    <?php if ($item->published !== 1 ||
        (!empty($item->publish_up) && strtotime($item->publish_up) > strtotime(Factory::getDate())) ||
        (!empty($item->publish_down) && strtotime($item->publish_down) < strtotime(Factory::getDate()))) { continue; } ?>
        <div class="row cat-list-row<?php echo $nrows % 2; $nrows += 1; ?> align-items-center">
            <div class="col-12 col-md-3">
                <?php if ($this->params->get('show_image_heading')) : ?>
                    <?php if ($item->image) : ?>
                        <?php echo LayoutHelper::render(
                            'joomla.html.image',
                            [
                                'src'   => $item->image,
                                'alt'   => 'official image of ' . $item->name,
                                'class' => 'contact-thumbnail img-thumbnail',
                            ]
                        ); ?>
                    <?php endif; ?>
                <?php endif; ?>
            </div>
            <div class="col-12 col-md-3">
                <div class="parliament-committee-fields">
                <a href="<?php echo Route::_(RouteHelper::getContactRoute($item->slug, $item->catid, $item->language)); ?>">
                    <span class="fs-2"><?php echo $this->escape($item->name); ?></span>
                </a>
                    <?php echo $item->event->beforeDisplayContent; ?>
                </div>
            </div>
            <div class="col-12 col-md-6 text-start">
                <?php if ($this->params->get('show_position_headings') && !empty($item->con_position)) : ?>
                    <strong><?php echo Text::_('COM_CONTACT_FIELD_INFORMATION_POSITION_LABEL'); ?></strong><br>
                    <?php echo $item->con_position; ?><br>
                <?php endif; ?>
                <?php if ($this->params->get('show_suburb_headings')) : ?>
                    <?php $location = []; ?>
                    <?php if (!empty($item->address)) : ?>
                        <?php $location[] = $item->address; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->suburb)) : ?>
                        <?php $location[] = $item->suburb; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->state)) : ?>
                        <?php $location[] = $item->state; ?>
                    <?php endif; ?>
                    <?php if (!empty($item->postcode)) : ?>
                        <?php $location[] = $item->postcode; ?>
                    <?php endif; ?>
                        <strong><?php echo Text::_('COM_CONTACT_FIELD_INFORMATION_ADDRESS_LABEL'); ?></strong><br>
                    <?php echo implode("<br>\n", $location); ?><br>
                <?php endif; ?>
                <?php if (!empty($item->misc)) : ?>
                    <?php echo $item->misc; ?>
                <?php endif; ?>
            </div>
        </div>
    <?php endforeach; ?>
</div>
```

## Стилизация

Классы стилей Bootstrap можно определить в файле `mydefault_myitems.php`.
Например, `<span class="fs-2">...</span>` используется для увеличения размера шрифта имени контакта. Другие стили можно добавить в файл `user.css`, например
настроить отображение маркированных списков только внутри тега с классом
`contactList`.

Ниже приведены стили, добавленные в файл user.css для получения макета
делового комитета, показанного выше.

```
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}
a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}
#contactList ul {
  list-style-type: none;
  padding-left: 0;
}
.cat-list-row0 {
  background-color: #efefef;
}
.cat-list-row0:hover, .cat-list-row1:hover  {
  background-color: #ddd;
}
div.parliament-committee-fields {
  text-align: left;
  margin-top: 1rem;
}
div.parliament-committee-fields ul.fields-container {
  list-style-type: none;
  padding-left: 0;
}
div.parliament-committee-fields ul.fields-container span.field-label {
  font-weight: 700;
}
```

*Переведено openai.com*