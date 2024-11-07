<!-- Filename: J4.x:Switching_Templates / Display title: Переключение шаблонов -->

## Шаблоны сайта и администратора

Joomla 4 поставляется с единственным шаблоном сайта — Cassiopeia, и единственным шаблоном администратора — Atum. Вы можете получить дополнительные шаблоны от поставщиков шаблонов сторонних разработчиков, как бесплатные, так и платные, а также создать свои собственные шаблоны, проще всего в качестве дочерних шаблонов.

Вряд ли вам захочется использовать альтернативный шаблон администратора, поэтому эта статья охватывает только альтернативные шаблоны сайта. Для примера был создан дочерний шаблон с зелёной темой, как описано в статье о дочерних шаблонах. Также на сайте, который используется для примера, установлены тестовые образцы данных.

## Стиль шаблона по умолчанию

Один из ваших шаблонов должен быть отмечен как шаблон по умолчанию. Он используется для всех страниц, кроме отдельных страниц, которые указывают альтернативный шаблон. Чтобы установить шаблон по умолчанию:

- Выберите **Система → Панель шаблонов → Стили шаблонов сайта** в меню администратора.
- Выберите одну из кнопок в колонке «По умолчанию».

![страница списка стилей шаблонов сайта](../../../en/images/templates/switch-templates-styles-list.png)

Посмотрите на свой сайт, чтобы убедиться, что все страницы используют шаблон по умолчанию.

## Использование альтернативного стиля

Joomla позволяет вам выбрать стиль для конкретной страницы из меню
назначения. Выбор можно сделать из формы стиля шаблона или
формы редактирования меню. Оба метода дают одинаковый результат. Первый
метод более удобен для выбора группы пунктов меню,
относящихся к одному и тому же меню.

### Метод назначения через меню шаблона

Из списка стилей шаблонов:

- Выберите стиль, который **не** установлен по умолчанию. Жёлтая звезда
  указывает стиль по умолчанию.
- Выберите вкладку Назначение меню.
- Выберите отдельные пункты меню или переключите все элементы в меню.
- Сохраните

![вкладка назначения пункта меню страницы редактирования стиля](../../../en/images/templates/switch-templates-styles-edit-style-menu-assignment.png)

В этом примере выбраны все пункты меню из меню `Главное тестовое меню`.
Вернитесь на ваш сайт и выберите любой пункт меню,
который должен использовать выбранный шаблон.

### Метод деталей меню

Этот метод используется для установки шаблона для отдельных пунктов меню.

- Выберите **Меню → \[Название Меню\]** из меню администратора.
- Выберите ссылку на пункт меню из колонки Заголовок, чтобы открыть форму редактирования.
- В поле **Стиль Шаблона** выберите желаемый стиль шаблона.
- Сохраните

![страница редактирования пункта меню показывающая выбор стиля](../../../en/images/templates/switch-templates-styles-edit-menu-style.png)

Вернитесь на ваш сайт и выберите измененный пункт меню, чтобы убедиться, что он
отображается с выбранным стилем шаблона.

*Переведено openai.com*
