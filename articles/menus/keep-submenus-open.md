<!--
{
    "source": "https://docs.joomla.org/https:",
    "title": "\u041e\u0441\u0442\u0430\u0432\u0438\u0442\u044c \u043f\u043e\u0434\u043c\u0435\u043d\u044e \u043e\u0442\u043a\u0440\u044b\u0442\u044b\u043c\u0438",
    "description": " ",
    "author": ""
}
-->

Модуль меню можно использовать для отображения горизонтального меню (обычно в верхней части страницы) или вертикального меню (обычно на боковой панели слева или справа). В горизонтальном (верхнем) меню оставлять подменю открытым нежелательно. Поэтому по умолчанию модуль меню закрывает подменю при загрузке страницы.

## Поведение переключателя при состоянии *открыто*

Однако в вертикальном меню (на боковой панели) часто желательно оставлять подменю открытым, если оно содержит активный пункт меню. В Joomla 6.0 был введён новый CSS-класс `nav-active-open`, специально предназначенный для управления автоматическим открытием подменю при загрузке страницы для активного пункта меню. Теперь установка этого класса позволяет добиться такого поведения. Класс задаётся в модуле через панель управления.

![настройка класса меню в панели управления для nav-active-open, чтобы переключатель оставался открытым для активного меню](../../../en/images/menus/keep-submenus-open/01-menu-class-setting.png)

## Как создать меню на боковой панели без переключателя раскрытия

Если вы хотите оставить все подменю открытыми, переключатель раскрытия не нужен. Вместо этого используйте [переопределение шаблона](jdocmanual?article=user/templates/template-overrides).

Переопределение этого шаблона выполняется следующим образом:

1. Сначала в меню администратора выберите Система → Шаблоны → Шаблоны сайта, а затем выберите пункт Cassiopeia — Подробности и файлы. Откроется форма Шаблоны: Настройка (Cassiopeia).

2. Перейдите на вкладку Создать переопределения и выберите mod_menu:

![выбор переопределения шаблона модуля меню](../../../en/images/menus/keep-submenus-open/02-create-override-select-mod-menu.png)

Это скопирует все файлы разметки меню из модуля меню в переопределение. После этого снова откройте вкладку Редактор.

3. На вкладке Редактор раскройте элементы в разделе HTML → mod_menu. Здесь вы найдёте файл `default.php`. Откройте файл и скопируйте его содержимое в безопасное место. Закройте файл.

4. Создайте новый файл в папке html → mod_menu. Его имя не должно содержать символ подчёркивания. В этом примере новый файл называется `treedefault.php`. Это позволяет выбирать либо стандартную разметку меню, либо эту альтернативную разметку в любом из модулей меню. В следующем списке файлов переопределения исходный файл обведён красным, а новый альтернативный — зелёным.

![вкладка редактирования переопределения mod_menu — открытие default.php](../../../en/images/menus/keep-submenus-open/03-edit-mod-menu.png)

4. Отредактируйте новый файл разметки. Следующие шаги перечислены в обратном порядке, чтобы сохранить номера строк в процессе редактирования:

Измените строку 104 так, чтобы она содержала следующее:

```
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
```

Это оставляет меню открытым и добавляет отступ к подменю.

Замените строки 98–101 на `break`

```php
                    echo '<button class="mod-menu__toggle-sub" aria-expanded="false">' .
                 break;
                    '<span class="icon-chevron-down" aria-hidden="true"></span>' .
                    '<span class="visually-hidden">' . Text::sprintf('MOD_MENU_TOGGLE_SUBMENU_LABEL', $item->title) . '</span>' .
                    '</button>';
```

Удалите строки 93–94

```php
                    echo '<span class="icon-chevron-down" aria-hidden="true">' .
                        '</span></button>';
```

Удалите строки 66–71

```php
    // The next item is deeper - add toggle only here it is a heading or separator
    if ($item->deeper && (int) $item->level === $startLevel && in_array($item->type, ['separator', 'heading'])) {
        // Add a toggle button.
        echo '<button class="mod-menu__toggle-sub" aria-expanded="false">';
    }
```

Удалите строки 15–20

```php
/** @var Joomla\CMS\WebAsset\WebAssetManager $wa */
$wa = $app->getDocument()->getWebAssetManager();
$wa->getRegistry()->addExtensionRegistryFile('mod_menu');
$wa->usePreset('mod_menu.menu');
```

Это полный файл переопределения `treedefault.php`:

```
<?php

/**
 * @package     Joomla.Site
 * @subpackage  mod_menu
 *
 * @copyright   (C) 2009 Open Source Matters, Inc. <https://www.joomla.org>
 * @license     GNU General Public License version 2 or later; see LICENSE.txt
 */

defined('_JEXEC') or die;

use Joomla\CMS\Helper\ModuleHelper;
use Joomla\CMS\Language\Text;

$tagId      = $params->get('tag_id', '') ?: 'mod-menu' . $module->id;
$id         = ' id="' . htmlspecialchars($tagId, ENT_QUOTES, 'UTF-8') . '"';
$startLevel = (int) $params->get('startLevel', 1);

// The menu class is deprecated. Use mod-menu instead
?>
<ul<?php echo $id; ?> class="mod-menu mod-list nav <?php echo $class_sfx; ?>">
<?php foreach ($list as $i => &$item) {
    $itemParams = $item->getParams();
    $class      = 'nav-item item-' . $item->id;

    if ($item->id == $default_id) {
        $class .= ' default';
    }

    if ($item->id == $active_id || ($item->type === 'alias' && $itemParams->get('aliasoptions') == $active_id)) {
        $class .= ' current';
    }

    if (in_array($item->id, $path)) {
        $class .= ' active';
    } elseif ($item->type === 'alias') {
        $aliasToId = $itemParams->get('aliasoptions');

        if (count($path) > 0 && $aliasToId == $path[count($path) - 1]) {
            $class .= ' active';
        } elseif (in_array($aliasToId, $path)) {
            $class .= ' alias-parent-active';
        }
    }

    if ($item->type === 'separator') {
        $class .= ' divider';
    }

    if ($item->deeper) {
        $class .= ' deeper';
    }

    if ($item->parent) {
        $class .= ' parent';
    }

    echo '<li class="' . $class . '">';

    switch ($item->type) :
        case 'separator':
        case 'component':
        case 'heading':
            require ModuleHelper::getLayoutPath('mod_menu', 'default_' . $item->type);
            break;
        default:
            require ModuleHelper::getLayoutPath('mod_menu', 'default_url');
            break;
    endswitch;

    // The next item is deeper.
    if ($item->deeper) {
        // Check type - add only on first level
        // @todo aria-label - set in menu item ???
        if ((int) $item->level === $startLevel) {
            switch ($item->type) {
                case 'heading':
                case 'separator':
                    break;

                default:
                    break;
            }
        }
        echo '<ul class="list-unstyled ps-3" aria-hidden="false">';
    } elseif ($item->shallower) {
        // The next item is shallower.
        echo '</li>';
        echo str_repeat('</ul></li>', $item->level_diff);
    } else {
        // The next item is on the same level.
        echo '</li>';
    }
}
?></ul>
```

## Результат

В результате получается простой список без функциональности переключателя для модуля меню боковой панели, показанный здесь слева:

![результат с переопределением шаблона — простой список без кнопок переключения и соответствующей функциональности](../../../en/images/menus/keep-submenus-open/05-site-result.png)

*Переведено openai.com*
