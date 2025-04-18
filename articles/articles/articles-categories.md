<!-- Filename: J4.x:Create_and_Manage_Article_Categories / Display title: Статьи: Категории -->

## Введение

Представьте себе библиотеку без системы классификации: книги просто размещены на полках в порядке их поступления. Это не очень удобно, если библиотека содержит миллионы книг, а вы ищете что-то по истории, садоводству или науке. То же самое касается статей. Если у вас десятки, сотни или тысячи статей, вам действительно нужна методика их классификации, чтобы легко находить то, что вам нужно. Для этого и существуют категории.

Категория в Joomla! может содержать как статьи, так и подкатегории в древовидной структуре с любой степенью вложенности, хотя вряд ли вы захотите углубляться более чем на три или четыре уровня. Например, если ваши статьи касаются природы, вы можете классифицировать их следующим образом:

- Животные
  - Птицы
    - Ястребы
    - Вьюрки
    - Чайки
  - Млекопитающие
    - Обезьяны
    - Приматы
    - Грызуны
- Растения
  - Цветы
    - Маргаритки
    - Розы
  - Деревья
    - Дубы
    - Вяз

В этом примере категория *Животные* может содержать общие статьи о животных, а также подкатегории для статей о различных видах животных.

Joomla предоставляет одну категорию по умолчанию с названием «Без категории». Любая статья, не отнесенная к созданной вами конкретной категории, становится частью категории «Без категории». Вы создаете категории по мере необходимости, чтобы соответствовать тематике ваших статей.

Статья может принадлежать только одной категории. В некоторых случаях этого может быть недостаточно. Предположим, например, вы хотите найти книги всех видов на определенном языке, или все ядовитые растения или всех опасных животных. Здесь на помощь приходят теги. Они описаны в другом месте.

### Использование Категорий

На странице администратора *Статьи* в форме *Параметры фильтрации* есть выпадающий список **- Выбор категории -**, который отображает древовидную структуру категорий, позволяя вам отфильтровать статьи в выбранной категории. Вы также можете создать типы пунктов меню *Блог категории* и *Список категории* для отображения статей из выбранной категории посетителям сайта.

## Добавление категорий и подкатегорий

Существует несколько способов перейти на страницу *Статьи: Новая категория*:

- Через **Домашнюю панель управления**. Выберите **плюс (+) символ** справа от 
  ссылки *Категории статей*. Это приведет вас на страницу списка *Статьи: Категории*.
- Через **Меню администратора**. Выберите элемент *Контент*, чтобы развернуть список, 
  и затем выберите **плюс (+) символ** справа от ссылки *Категории*.
- Через **Панель управления контентом**. Выберите значок панели справа от 
  ссылки *Контент* в меню администратора, а затем в панели *Контент* выберите 
  **плюс (+) символ** справа от ссылки *Категории*.
- Через **Статьи: Категории**. Следуйте любому из маршрутов на страницу списка и 
  выберите кнопку **Новый** в панели инструментов.

Следующий скриншот показывает ссылку *Категории статей* на домашней панели управления к 
списку категорий и рядом *Символ плюс*, ведущий к форме *Статьи: Новая категория*.

![Иконка добавления категории выделена на домашней панели управления](../../../en/images/articles/category-add-via-home-dashboard.png)

## Статьи: форма новой категории

![Форма редактирования новой категории статей](../../../en/images/getting-started/article-category-edit.png)

На скриншоте выше показана заполненная форма. Всего нужно заполнить два поля, все остальные имеют значения по умолчанию или нулевые значения, которые можно оставить на данный момент и заполнить позже по мере необходимости.

- **Заголовок** - это единственное обязательное поле. Заголовок должен быть коротким, но описательным для категории.

### Вкладка "Категория"

- **Описание** Хотя это и не обязательно, это поле может отображаться на страницах списка категорий сайта, управляемых пунктами меню. Возможно, вам потребуется вернуться позже и обновить описание.
- **Родительская** Если установлено значение *- Без родительской -*, этот новый элемент является потенциально родительской категорией для других категорий. Если выбрана другая категория в качестве родительской, этот новый элемент является подкатегорией.
- **Статус** По умолчанию новая категория установлена в *Опубликовано*. Вы можете изменить статус категории на *Опубликовано*, *Неопубликовано*, *Архивировано* или *Удалено в корзину*. [ToDo] Объясните, что происходит, когда категория не опубликована...
- **Доступ** По умолчанию доступ установлен как *Публичный*. Другие варианты ограничения доступа: *Гость*, *Зарегистрированный*, *Специальный* и *Суперпользователи*. [ToDo] Объясните, как может использоваться доступ к категории...
- **Язык** На многоязычных сайтах установка этого параметра на значение *Все* сделает новую категорию независимой от языка сайта. Если установлен определенный язык, она будет доступна только на страницах, использующих этот язык.
- **Теги** Если вы используете их, вы можете добавить один или несколько тегов к категории. Установка тегов на уровне категории – это хороший способ поддерживать согласованность. Для этого урока был создан тег *Природа*, который использовался для фильтрации списков, чтобы показывать только элементы, связанные с уроками.
- **Примечание** и **Примечание о версии** Используйте их для добавления соответствующих примечаний, если это необходимо.

### Вкладка "Опции"

Настройки на этой вкладке влияют на внешний вид этой категории на страницах сайта.

- **Макет** Это относится к размещению контента на странице. Может быть выбор макетов в зависимости от используемого компонента и шаблона. [ToDo] Примеры...
- **Изображение** Возможно, вы захотите использовать изображение как значок, чтобы эту категорию можно было мгновенно распознать в списке категорий. Если используется для такой цели, описание изображения (*Alt text*) не требуется, но должна быть отмечена галочка *Без описания*.

### Сохранить и закрыть

- **Сохранить и закрыть** Чтобы завершить редактирование этой категории. Или в выпадающем списке...
  - **Сохранить и создать новую** Сохранить эту категорию и открыть новую форму редактирования для новой категории. Например, вы можете начать строить дерево категорий, добавив категорию *Приматы* с *Млекопитающими* в качестве родительской.
  - **Сохранить в меню как список** ...
  - **Сохранить в меню как блог** ...
  - **Сохранить как копию** ...

Закрытие формы редактирования приводит к странице списка **Статьи: Категории**.

![Список категорий, отфильтрованный по тегу Природа](../../../en/images/articles/categories-list.png)

### Сохранить в меню как список

Выбор этого пункта из выпадающего списка *Сохранить и закрыть* сохранит и закроет форму редактирования категории и откроет новую форму элемента меню со всеми данными, необходимыми для создания *Списка категорий* для этой категории. Вы можете изменить *Название*. Например, оно может быть *Список статей о млекопитающих*, чтобы было ясно, что это, вероятно, список статей.

На вкладке *Отображение на странице* попробуйте установить поле *Показать заголовок страницы* на *Показать*. Это покажет *Список статей о млекопитающих* как жирный заголовок в верхней части страницы, придавая ей более завершенный вид.

### Сохранить в меню как блог

Выбор этого пункта из выпадающего списка *Сохранить и закрыть* сохранит и закроет форму редактирования категории и откроет новую форму элемента меню со всеми данными, необходимыми для создания *Блога категории* для этой категории. Вы можете изменить *Название*. Например, оно может быть *Блог статей о млекопитающих*, чтобы были выделены последние статьи о млекопитающих.

На вкладке *Отображение на странице* попробуйте установить поле *Показать заголовок страницы* на *Показать*. Это покажет *Блог статей о млекопитающих* как жирный заголовок в верхней части страницы, придавая ей более завершенный вид.

Следующий скриншот показывает вид страницы блога категории в разработке.

![Страница блога категории млекопитающих](../../../en/images/articles/article-mammals-articles-blog-site-view.png)

## Советы

- Вы также можете создавать категории статей прямо из статьи.
- Помните, что вы можете назначить статью только одной категории.
- Поскольку как главные категории, так и подкатегории могут иметь
  дальнейшие подкатегории, тщательно планируйте и организуйте категории. Сложная
  иерархия категорий может стать проблемой для управления.
- Другим методом группировки контента в Joomla является использование
  компонента **Теги**, позволяющего добавлять несколько тегов к вашим статьям.
  Использование категорий и тегов может помочь минимизировать количество
  подкатегорий и предоставлять эффективный способ структурировать контент
  вебсайта и предоставить посетителям больше возможностей для навигации
  по содержимому сайта.

*Переведено с помощью openai.com*

