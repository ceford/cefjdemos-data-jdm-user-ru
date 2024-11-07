<!-- Filename: J4.x:Fields_and_Field_Groups / Display title: Поля и группы полей  -->

## Введение

Поля используются для отображения дополнительных атрибутов Статей, Контактов или Пользователей. Данные вводятся в форме редактирования администратора и отображаются на сайте. Пример:

Предположим, вы пишете статьи о различных аспектах природы, иногда о цветах, иногда о животных. Одно из полей, которое вы могли бы захотеть записать и отобразить для обеих категорий, — это Латинское Название, требующее текстовое поле. Другое поле может быть Местообитание: Лес, Пруд, Луг и так далее, требующее выпадающий список. Для цветов вы могли бы захотеть зафиксировать Сезон Цветения, используя 4 флажка, по одному на каждый сезон, или 12 флажков, по одному на каждый месяц.

Пустые поля в форме ввода не отображаются на сайте, поэтому вы можете хранить все поля в одном длинном списке. Тем не менее, обычно лучше использовать категории для ваших Статей, например, Цветы и Животные. Поля могут быть назначены более чем одной Категории. Таким образом, поля Латинское Название и Местообитание будут назначены обеим категориям, но Сезон Цветения будет назначен только категории Цветов.

Если поле не назначено группе, оно появится в форме редактирования на вкладке Поля. Если поле назначено группе, оно будет отображаться на вкладке с тем же названием. Таким образом, для группы Цветов кажется уместным создать группу полей с именем Данные о Цветах (или просто Цветы, хотя использование одинаковых имён для разных вещей может запутать). А для других общих полей вы можете использовать группу Природа.

## Пример с объяснением - Заметки о Природе

Для статей о природе категория статьи и подкатегории для каждой ветви живого мира может выглядеть следующим образом:

![Категории статей о природе](../../../en/images/fields/fields-articles-categories-list.png)

Некоторые очевидные характеристики природы, на которые следует обратить внимание:

- Категория "Природа" предназначена для статей, которые касаются природы в общем, а не конкретных видов растений или животных.
- Подкатегории предназначены для более конкретных статей, и им могут понадобиться свои собственные подкатегории.
- Все формы жизни имеют Обычные имена и Латинские имена.
- Цветы и деревья имеют периоды цветения, высоту и ширину, а птицы и млекопитающие - нет.
- У птиц измеряют размах крыльев и длину, в то время как у млекопитающих - высоту и длину.
- Цвет может быть постоянным или изменяющимся.

Смысл здесь в том, что может быть необходимо настроить поля или группы полей для общих характеристик, таких как Латинское имя, а также отдельные группы полей для каждой категории природы.

## Группы полей

Создание групп полей для статей очень просто:

- Выберите **Содержимое → Группы полей** в меню администратора
- Нажмите кнопку **Создать** на панели инструментов.
- Введите подходящий **Заголовок**.
- Введите **Описание**. Оно появится под полем в форме редактирования статьи, когда выбрано *Переключение встроенной помощи*.
- Выберите **Сохранить и закрыть** на панели инструментов.

![Список групп полей содержимого](../../../en/images/fields/fields-field-groups-list.png)

### Упорядочивание

При вводе данных в статью группы полей будут появляться в порядке, указанном в этом списке. Перетащите элементы, чтобы изменить порядок.

## Поля

Чтобы создать новое поле статьи, выберите **Контент → Поля** в меню Администратора и заполните форму. Примеры показаны ниже.

### Текст - Латинское Название

Обратите внимание, что на скриншоте ниже это поле было присвоено группе полей "Природа" и категории "Природа". Это обеспечивает, что оно всегда будет отображаться в статьях в категории "Природа" и любых подкатегориях.

![Текстовое поле - латинское название в группе природа](../../../en/images/fields/fields-latin-name.png)

### Флажки - Период Цветения

Флажки появляются в форме редактирования статьи, чтобы вы могли отметить период цветения. В отображении статьи будут перечислены только те сезоны, которые вы отметили. Например, если вы отметите Весну и Лето, вывод покажет: Период Цветения: Весна, Лето.

Обратите внимание, что на этом скриншоте поле было присвоено группе "Цветы" и категории "Цветы". Это должно гарантировать, что поле будет присутствовать только в статьях о цветах.

![Поле с флажками - период цветения](../../../en/images/fields/fields-flowering-season.png)

### Цвет - Color

Чтобы вас запутать, название типа поля - Color (американское написание), но в документации этот ярлык обозначен как Colour (британское написание).

![Поле цвета](../../../en/images/fields/fields-colour.png)

Поле "Цвет" присвоено группе полей "Природа" и категории "Природа", так как оно не является уникальным для цветов.

### Целое число - Морозостойкость

Морозостойкость растения может быть представлена как целое число от 1 до 7. Поля для действительных чисел нет, поэтому длина и ширина могут быть целыми числами с указанием масштаба (см, м или фт) в ярлыке. Существуют настройки *Префикса* и *Суффикса* на вкладке *Опции*. Если очевидного верхнего предела нет, оставьте поле *Последнее:* пустым.

![Поле морозостойкости](../../../en/images/fields/fields-hardiness.png)

Морозостойкость по версии RHS - это характеристика, обычно применяемая к цветам!

С целочисленным полем есть проблема. Оно всегда имеет значение и, следовательно, всегда отображается в выводе. Вы можете обойти эту проблему с помощью переопределения шаблона для *Плагинов / Целые числа*. Например, вы можете использовать значение выше или ниже ожидаемых пределов, чтобы исключить поле из вывода.

## Форма редактирования статьи

Когда открывается форма "Статья: Новая", категория по умолчанию — 
"Без категории", а вкладки формы не включают "Поля" и "Цветы". 
Выберите категорию "Цветы", и форма перезагрузится с этими вкладками.

### Вкладка "Природа"

![Вкладка "Природа" статьи о пролесках](../../../en/images/fields/field-article-bluebell-nature-tab.png)

- **Латинское имя** Это текстовое поле ввода, поэтому достаточно ввести латинское имя 
  жизненной формы, которую охватывает статья. Однако категория "Природа"
  охватывает жизнь в целом, а также конкретных животных или растения. Поэтому это
  не является *обязательным* полем.
- **Цвет** В поле выбора цвета можно ввести шестнадцатеричное значение цвета с клавиатуры 
  или выбрать цвет из инструмента выбора цвета. Шестнадцатеричное 
  число имеет формат xrrggbb, где rr обозначает красный, gg — зеленый, а bb — синий цвет. 
  На выходе сайт отображает шестнадцатеричное значение, что не очень полезно!

### Вкладка "Цветы"

![Вкладка "Цветы" статьи о пролесках](../../../en/images/fields/field-article-bluebell-flowers-tab.png)

- **Сезон цветения** Поле с флажками — пролески известны как цветы весны, 
  поэтому уместен выбор одного флажка.
- **Зимостойкость** Целое числовое поле. Здесь есть проблема — нет возможности 
  оставить это поле пустым. Оно всегда отображается на выходе, 
  даже для более общих статей о цветах, где это не подходит. Имется обходной путь с использованием переопределения шаблона.

## Результат сайта

Посмотрите на результат, видимый на вашем сайте. В этом примере был создан элемент меню для одной статьи:

![Просмотр сайта статьи Bluebell](../../../en/images/fields/field-article-bluebell-site.png)

### Шестнадцатеричный цвет

По умолчанию данные отображаются как шестнадцатеричное значение цвета, что не особо полезно. Простое решение — создать переопределение шаблона для полей / плагина цвета, что показано на скриншоте выше.

Просто замените эту строку:
```
echo htmlentities($value);
```
следующими строками:
```
if (is_array($value)) {
  $list = [];
  foreach ($value as $v) {
    $x = htmlentities($v);
    $list[] = '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
    echo implode(', ', $list);
  }
} else {
    $x = htmlentities($value);
    echo '<span class="ps-5 pe-5" style="background-color: ' . $x . ';">&nbsp</span> ' . $x;
}
```
И перед шестнадцатеричным значением будет отображен прямоугольник с фоном цвета, соответствующим этому значению.

*Переведено с помощью openai.com*
