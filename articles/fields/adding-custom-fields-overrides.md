<!-- Filename: J3.x:Adding_custom_fields/Overrides / Display title: Переопределение шаблонов -->

## Автоматическое отображение поля

Каждое из доступных полей имеет опцию, обозначенную как *Автоматическое отображение*, которая может быть установлена в одно из следующих значений:

* После заголовка
* Перед отображением содержимого
* После отображения содержимого
* Не отображать автоматически

Если выбран последний из этих пунктов, то поле не отображается, пока вы не создадите переопределение шаблона для самостоятельного отображения поля. Или вы можете добавить `{field ID}` в статью, чтобы разместить поле в любом нужном вам месте. Но не забудьте сделать это в каждой статье.

Этот пример показывает, как создать переопределение шаблона для Контакта. Эти методы также применимы к компонентам Содержимого и Пользователя.

## Создание Переопределения Шаблона

Из меню Администратора:

* Выберите **Система / Шаблоны сайта / Cassiopeia: Подробности и файлы**
* Перейдите на вкладку **Создать переопределения**.
* Выберите **com_contact** в панели *Компоненты*
* Выберите **Контакт** из списка доступных представлений. Это макет для одной контактной информации.

В панели **Редактор**:
* Выберите **html / com_contact / contact / default.php**, это файл,
который задает общий макет страницы с одним контактом.
* Прокрутите этот файл и обратите внимание на серию блоков `<php if (...) : ?>`.
Каждый из них будет показывать или скрывать раздел текста в зависимости от настроек контакта.
* Обратите внимание на строки, содержащие
```
    <?php echo $this->item->event->afterDisplayTitle; ?> (строка 73)
    <?php echo $this->item->event->beforeDisplayContent; ?> (строка 98)
    <?php echo $this->item->event->afterDisplayContent; ?> (строка 189)
```
Одна из этих переменных, или ни одна из них, заполняется в зависимости от значения
поля Автоматический показ.

## Использование полей в вашем override

Все поля, соответствующие текущему элементу, доступны через свойство
`$this->item->jcfields`, которое является массивом и содержит следующие
данные для каждого поля (в этом примере для поля редактора):

```php
    Array
    (
        [4] => stdClass Object
            (
                [id] => 4
                [title] => article-editor
                [name] => article-editor
                [checked_out] => 0
                [checked_out_time] => 0000-00-00 00:00:00
                [note] =>
                [state] => 1
                [access] => 1
                [created_time] => 2017-04-07 12:08:59
                [created_user_id] => 856
                [ordering] => 0
                [language] => *
                [fieldparams] => Joomla\Registry\Registry Object
                    (
                        [data:protected] => stdClass Object
                            (
                                [buttons] =>
                                [width] =>
                                [height] =>
                                [filter] =>
                            )

                        [initialized:protected] => 1
                        [separator] => .
                    )

                [params] => Joomla\Registry\Registry Object
                    (
                        [data:protected] => stdClass Object
                            (
                                [hint] =>
                                [render_class] =>
                                [class] =>
                                [showlabel] => 1
                                [disabled] => 0
                                [readonly] => 0
                                [show_on] =>
                                [display] => 2
                            )

                        [initialized:protected] => 1
                        [separator] => .
                    )

                [type] => editor
                [default_value] =>
                [context] => com_content.article
                [group_id] => 0
                [label] => article-editor
                [description] =>
                [required] => 0
                [language_title] =>
                [language_image] =>
                [editor] =>
                [access_level] => Public
                [author_name] => Super User
                [group_title] =>
                [group_access] =>
                [group_state] =>
                [value] => Bar
                [rawvalue] => Bar
            )
    )
```

## Отображение поля

Функция `FieldsHelper::render()` используется для отображения каждого поля. Сначала добавьте оператор `use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;` в список операторов `use` в начале файла переопределения:

```php
defined('_JEXEC') or die;

use Joomla\CMS\Helper\ContentHelper;
use Joomla\CMS\HTML\HTMLHelper;
use Joomla\CMS\Language\Text;
use Joomla\CMS\Layout\FileLayout;
use Joomla\CMS\Layout\LayoutHelper;
use Joomla\CMS\Plugin\PluginHelper;
use Joomla\CMS\Router\Route;
use Joomla\Component\Contact\Site\Helper\RouteHelper;
use Joomla\Component\Fields\Administrator\Helper\FieldsHelper;
```

Затем, где бы вы не захотели разместить поля в вашем шаблоне, используйте следующий код:
```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo FieldsHelper::render($field->context, 'field.render', array('field' => $field)); ?><br>
<?php endforeach ?>
```

Или для прямого переопределения, которое не переводит метку:

```php
<?php foreach ($this->item->jcfields as $field) : ?>
    <?php echo $field->label . ':' . $field->value; ?><br>
<?php endforeach ?>
```

## Загрузка индивидуальных полей

Чтобы добавить индивидуальные поля в ваш контент, начните с выбора конкретных имен для ваших пользовательских полей, используя поле **Имя**, которое будет использоваться для прямого обращения к вашему полю в коде переопределения. На вкладке `Опции` выберите **Нет** в поле `Автоматическое отображение`, чтобы предотвратить его автоматическое отображение в стандартных позициях.

Затем, чтобы обеспечить прямой доступ по имени к пользовательским полям в переопределении, поместите код ниже в начало вашего файла. Вы должны сделать это для каждого PHP файла переопределения, в котором хотите разместить индивидуальные пользовательские поля.

```php
<?php foreach($this->item->jcfields as $jcfield) {
    $this->item->jcFields[$jcfield->name] = $jcfield;
} ?>
```

И, наконец, вы должны добавить код размещения поля в том месте, где вы хотите, чтобы ярлык поля или его значение отображались.

Чтобы добавить **ярлык** поля в ваше переопределение, вставьте код ниже, заменив `name-of-field` на имя поля.

```php
<?php echo $this->item->jcFields['name-of-field']->label; ?>:&nbsp;
```

Чтобы добавить **значение** поля в ваше переопределение, вставьте код ниже, заменив `name-of-field` на имя поля.

```php
<?php echo $this->item->jcFields['name-of-field']->rawvalue; ?>
```

Вы можете добавить этот код в любую часть вашего переопределения. Примеры: содержание div, src в теге `img`, в атрибуте класса CSS и т.д.

