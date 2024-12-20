<!-- Filename: J6.x:Articles:_Filter_Options / Display title: Статьи: Параметры фильтрации   -->

## Введение

После создания вашей первой статьи, описанной в статье «Начало работы» на странице [Добавление статьи](jdocmanual?article=user/getting-started/adding-an-article), в вашем списке статей будет содержаться одна статья. Год спустя у вас может быть тысяча статей, и вам потребуется использовать *Параметры фильтра*, чтобы найти то, что вам нужно.

На следующем скриншоте показаны статьи, используемые для подготовки этого набора руководств. Размер партии в списке установлен на 5, чтобы сократить длину скриншота.

*Параметры фильтра* открыты, чтобы показать доступные фильтры.

![Список статей](../../../en/images/articles/articles-filter-options.png)

Этот список содержит более 20 статей, созданных с установкой *Многоязычных образцов данных*, и несколько дополнительных статей, добавленных позже.

## Порядок сортировки

Обратите внимание, что порядок сортировки по умолчанию — *по убыванию ID*. Это размещает последнюю статью в начале списка, что обычно и требуется.  

## Постраничная навигация

Если количество статей больше, чем *Размер Пакета*, под списком отображается панель навигации. Она содержит иконки для перехода на *Первую страницу*, *Предыдущую страницу*, *Следующую страницу* или *Последнюю страницу*. Числа ведут к статьям на соответствующей странице. Панель навигации полезна, если вам нужно просмотреть список статей.

## Фильтры

Все фильтры работают *при изменении*, но фильтры запоминаются, и *опции фильтрации* остаются видимыми, пока выбран хотя бы один фильтр.

### Выбор Избранного

- **- Выбрано Избранное -** Выбирает как Избранные, так и Неизбранные статьи.
- **Неизбранные статьи** Выбирает только Неизбранные статьи.
- **Избранные статьи** Выбирает только Избранные статьи.

### Выбор Статуса

По умолчанию выбираются статьи со статусом *Опубликовано* и *Неопубликовано*. Это позволяет переключать состояние публикации с помощью значка в колонке *Статус*. *Удалённые* и *Архивные* материалы включаются только если выбрано *Все*.

- **Удаленные** Выбирает только удаленные статьи. Значок *Статус* отображает значок мусорной корзины, который можно использовать для публикации статьи. Кнопка *Удалить* на панели инструментов позволяет полностью удалить любую выбранную статью. Есть предупреждающее сообщение. После удаления используйте кнопку *Очистить* для возврата к нефильтрованному списку.
- **Неопубликованные** Выбирает только Неопубликованные статьи.
- **Опубликованные** Выбирает только Опубликованные статьи.
- **Архивные** Выбирает только Архивные статьи. Значок статуса позволяет изменить статус статьи на Неопубликованно. Архивные статьи больше не требуются, но могут быть доступны через пункт меню *Архивные статьи*.
- **Все** Выбирает все статьи независимо от статуса.

Если необходимо изменить статус статьи не с помощью значка в колонке Статус, это можно сделать через форму редактирования статьи.

### Выбор Категории

В выпадающем списке показаны все категории сайта в древовидной структуре, аналогичной используемой на странице списка *Статей: Категории*. Если вы выберете одну категорию, все статьи в этой категории будут выбраны вместе со всеми статьями в её подкатегориях, если не установлен фильтр *Выбор максимальных уровней*.

Можно выбрать несколько категорий, которые не находятся в одном древе категорий.

### Выбор Доступа

В выпадающем списке можно выбрать статьи в указанных *Уровнях Доступа*. Управление доступом описано в отдельной статье. Вкратце, это ограничивает видимость статей на сайте следующим образом:

- **Публичный** Статьи, доступные для всех.
- **Гость** Статьи, доступные для всех, кто не вошел в систему.
- **Зарегистрированный** Статьи, доступные для всех, кто вошел в систему.
- **Специальный** Статьи, доступные для всех, кто вошел в систему и принадлежит к группе пользователей, имеющей Специальный Доступ.
- **Суперпользователи** Статьи, доступные только для тех, кто вошел в систему как Суперпользователь.

### Выбор Автора

Выпадающий список позволяет выбрать статьи по конкретному автору.

- **Нет** Это особый случай, когда статья существует, но исходного автора нет. Может быть несколько авторов, которые вносили статьи, но больше не имеют учетных записей пользователей.
- **Создано мной** Список ваших собственных статей.
- **Имя автора** Список имен авторов статей, который может быть довольно длинным. Используется реальное имя, а не имя для входа. Выберите автора, чтобы увидеть статьи, написанные этим автором.

### Выбор Языка

Этот фильтр присутствует только на мультиязычных сайтах. При создании статьи она может быть назначена для всех языков или для одного конкретного языка, который имеет название языка и код страны в поле *Язык* на форме ввода данных, например, *Английский (en-GB)* или *Испанский (es-ES)*. В фильтре языка:

- **Все** Этот фильтр выбирает статьи, которые были назначены для всех языков. Это не означает все статьи!
- **Название языка (xx-YY)** Список установленных языков. Выберите конкретный язык, чтобы увидеть статьи, назначенные для этого языка.

### Выбор Тега

Список тегов. Выберите любой тег, чтобы увидеть статьи с этим тегом. Можно выбрать несколько тегов.

### Выбор Максимальных Уровней

Это ограничивает список статей до заданного количества уровней в иерархии. При отсутствии выбора включаются все уровни. Если установлен на 1, будут включены только статьи первого уровня в древе категорий.

## Несколько фильтров

На крупных, сложных сайтах вам может понадобиться использовать несколько фильтров. Фильтры сохраняются в течение сеанса, до выхода из системы или до истечения срока действия сеанса из-за бездействия.

*Переведено openai.com*

