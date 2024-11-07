<!-- Filename: category-list-override.md / Display title: Переопределение списка категорий  -->

## Пункт меню "Список контактов в категории"

Это может быть личное мнение, но для меня макет списка категории Контактов по умолчанию не совсем удовлетворителен. Мои проблемы:

* Фото контакта слишком большие, почти 500 пикселей в ширину.
* Имя контакта не достаточно выделено.
* Маркированный список с личными данными не имеет заголовка и выглядит изолированным.
* Должность не имеет заголовка, поэтому может казаться изолированной.
* Поля с адресом и почтовым индексом отсутствуют.
* Данные о местоположении неполные.
* Личное заявление отсутствует.
* Список оформлен в таблице, что немного лучше на узких экранах, но выглядит довольно тесно.

Как это исправить в соответствии с моими предпочтениями?

## Стилизация

Изображение имеет CSS-стиль `contact-thumbnail img-thumbnail`. Инструменты разработчика браузера показывают, что для img-thumbnail установлено значение `max-width: 100%;`, но contact-thumbnail не используется. Единственное появление этого стиля на всем сайте находится в данном месте, поэтому можно безопасно установить переопределение в user.css, чтобы ограничить ширину изображения. Размер шрифта имени контакта можно увеличить, используя окружающий его тег `a`:

```
.contact-thumbnail {
  max-width: 200px;
  margin-right: 1rem;
}
a:has(.contact-thumbnail) {
  font-weight: 700;
  font-size: larger;
}
```

Список настраиваемых полей можно улучшить, удалив маркеры и отступы путем выбора только списков с маркерами, которые находятся внутри тега с классом contactList:
```
#contactList ul {
  list-style-type: none;
  padding-left: 0;
}
```
![стилизованный бизнес-комитет](../../../en/images/contacts/contact-business-committee-styled.png "Стилизованный Бизнес-Комитет")

Это все, что можно сделать с помощью стилизации. Лучше, но все равно недостаточно. Чтобы добавить больше элементов и изменить макет, потребуется переопределение макета. 

## Переопределение шаблона компоновки

Папка com_contact/tmpl/category содержит три PHP файла: default.php, default_children.php и default_items.php. Последний в этом списке содержит компоновку таблицы для списка.

Файлы переопределения создаются через Система / Шаблоны сайта / Cassiopeia, Детали и файлы / Создать переопределения. Выберите com_contact, затем category. Папка html будет содержать com_contact/category с тремя шаблонными файлами, упомянутыми выше. Для редактирования следует выбрать файл default_items.php. Строки с 83 по 203 содержат таблицу, используемую для компоновки.

Это может быть неочевидно, но $this->items - это массив членов категории, и каждый член фактически содержит все данные для каждого элемента, а не только те, которые упомянуты в параметрах меню.

Ниже представлен заменяющий код для секции `<table>...</table>` файла default_items.php с использованием сетки Bootstrap. На узких экранах три столбца располагаются один за другим. На экранах шириной более 768 пикселей столбцы располагаются бок о бок. Дополнительные пояснения следуют за кодом.

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
                                'alt'   => 'официальное изображение ' . $item->name,
                                'class' => 'contact-thumbnail img-thumbnail',
                            ]
                        ); ?>
                    <?php endif; ?>
                <?php endif; ?>
            </div>
            <div class="col-12 col-md-3">
                <a href="<?php echo Route::_(RouteHelper::getContactRoute($item->slug, $item->catid, $item->language)); ?>">
                    <span class="fs-2"><?php echo $this->escape($item->name); ?></span>
                </a>
            </div>
            <div class="col-12 col-md-6 text-start">
                <?php if ($this->params->get('show_position_headings') && !empty($item->con_position)) : ?>
                    <strong>Позиция</strong><br>
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
                        <strong>Адрес</strong><br>
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
### Объяснение

Список контактов может содержать элементы, которые не опубликованы или имеют даты publish_up и publish_down, которые не являются текущими. Их необходимо исключить из отображения, и требуется отдельный счетчик, чтобы поддерживать чередование цветов фона в каждой строке.

Тег img выглядит следующим образом:
```
<img src="/j51/images/parliament/Official_portrait_of_Liam_Byrne_crop_2.jpg" 
alt="официальное изображение Liam Byrne" class="contact-thumbnail img-thumbnail"
width="479" height="639" loading="lazy">
```
Класс `<span class="fs-2">...</span>` устанавливает имя контакта в размер шрифта 2, что будет аналогично Заголовку 2.

Элемент `show_suburb_headings` используется в качестве прокси для отображения полного адреса, так как некоторые отдельные элементы адреса не имеют селекторов Показывать/Скрывать в элементе меню.

### Дополнительное стилизование

Версия списка контактов с сеткой требует дополнительного стилизования в user.css:
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
```

### Результат

![gridded business committee](../../../en/images/contacts/contact-business-committee-grid.png "Gridded Business Committee")

*Переведено openai.com*

