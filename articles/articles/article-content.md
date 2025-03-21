<!-- Filename: J4.x:Adding_a_New_Article / Display title: Статья: Редактировать - Содержание -->

## Введение

Статья *Добавление статьи* была рассмотрена в статье *Начало работы*. Это первый из серии статей, предоставляющих более подробную информацию о форме *Редактирование статьи*. Она охватывает вкладку *Контент* и некоторые аспекты редактора TinyMCE, который является редактором по умолчанию, предоставляемым в Joomla.

На следующем скриншоте показана форма редактирования с уже сохраненной статьей.

![Форма редактирования контента](../../../en/images/articles/articles-edit-content.png)

## Ввод данных

Форма редактирования статьи имеет панели с вкладками. Для новой статьи по умолчанию выбрана вкладка **Содержимое**. В противном случае выбирается последняя открытая вкладка.

### Поле `Title`

Поле **Заголовок** является *обязательным* и используется везде, где отображается заголовок статьи. Это единственное поле, которое должно содержать текст, чтобы сохранить форму редактирования.

Заголовки должны быть короткими, но описательными, по содержанию статьи, так как они появляются в списках и пунктах меню, где пространство ограничено.

Заголовки не обязательно должны быть уникальными, хотя это желательно. Например, если вы выберете *Сохранить как копию* из выпадающего списка *Сохранить и закрыть*, процесс сохранения сохранит текущую статью и создаст новую с номером, добавленным к заголовку и псевдониму. Вы можете удалить номер из заголовка, но не из псевдонима и *сохранить* копию. Это создаст две статьи с одинаковым отображаемым заголовком.

### Поле `Alias`

Поле *Псевдоним* обычно оставляют пустым. Когда статья сохраняется, псевдоним генерируется из заголовка, переводя его в нижний регистр и заменяя не алфавитно-цифровые символы на дефисы.

Если вы измените заголовок статьи, вы можете удалить псевдоним и будет создан новый. Если псевдоним использовался для ссылки на статью во внутренних и внешних ссылках, это нарушит связи. Поэтому лучше не менять псевдоним старой статьи.

### Вкладка `Content` - Текст статьи

На скриншоте выше показан текст статьи в визуальном WYSIWYG редакторе, который выглядит как текстовый процессор. Однако вы должны знать, что текст статьи хранится в формате HTML, а поле ввода данных на самом деле является текстовым полем, содержащим этот HTML. Вы можете увидеть это сами, выбрав кнопку *Переключить редактор* под областью редактирования. Редактор на самом деле является JavaScript приложением, которое повторно отображает HTML, чтобы его было легко читать и изменять.

#### Запрещенные HTML Теги и Атрибуты

И Joomla, и редактор TinyMCE имеют настройки, запрещающие некоторые HTML теги и атрибуты. Например, список запрещенных Joomla по умолчанию включает *iframe*, поэтому, если вы попытаетесь включить этот тег в статью, он будет бесшумно удален при сохранении. Текстовые фильтры настраиваются в *Глобальной конфигурации*. Плагин TinyMCE имеет опцию *Использовать текстовый фильтр Joomla*. Если его установить в положение *Отключено*, он перечисляет *script, applet, iframe* как *Запрещенные элементы*.

#### Панели инструментов редактора

Над текстовой областью расположены ряды панелей инструментов. Две отображены по умолчанию. Остальные можно переключить, выбрав символ многоточия (...) в конце второй панели инструментов. Панели инструментов можно настроить на отображение различных строк и содержимого строк для разных групп пользователей.

Здесь слишком много инструментов, чтобы описывать каждый из них. Это создало бы стог сена, в котором придется искать иголку. Просто исследуйте!

Однако, есть некоторые функции, требующие дополнительного объяснения.

#### CMS Content

Эта кнопка открывает выпадающий список, который позволяет включать элементы в статью, полученные из других мест CMS.

- **Article** Эта ссылка открывает всплывающий список статей. Выберите статью, чтобы включить ссылку на эту статью в текущей статье.
- **Contact** Включите ссылку на контакт в текущую статью.
- **Field** Включите поле в статью. Оно представлено как `{field 1}`.
- **Media** Включите изображение или файл из всплывающего окна компонента Media.
- **Menu** Включите ссылку на элемент меню из всплывающего списка Menus.
- **Page Break** Появится запрос на *Заголовок страницы* и *Псевдоним содержания*. Эта функция используется для разбивки длинных документов на несколько страниц.
- **Read More** Разделитель *Read More...* вставляется в позицию курсора. Выберите разрыв между абзацами перед выбором.

#### Внешние ссылки

Элемент **Insert** на первой панели инструментов имеет опции вставки *ссылки...*, *изображения...* или *медиа...*. Это для внешних элементов, поэтому будьте готовы указать URL элемента, который будет использоваться.

### Вкладка `Content` - Настройки

Вкладка **Содержимое** в основном занята редактором TinyMCE.

Рядом с содержимым расположены поля для управления публикацией, способом и местом отображения статьи и тем, кто может её увидеть после публикации. В большинстве случаев эти настройки могут быть оставлены по умолчанию.

1. **Status** *Опубликовано*, *Не опубликовано*, *Архивировано* или *Удалено* - по умолчанию выбрано *Опубликовано*.
2. **Category** Это *обязательное* поле, но по умолчанию оно будет *Не категоризировано*. Вы можете выбрать категорию из списка или ввести несколько символов из имени категории, чтобы сократить список категорий на выбор.
3. **Featured** Переключайте между *Нет* и *Да*, чтобы отображать статью на главной странице, если используется компоновка *Избранные статьи*.
4. **Access** Уровень доступа можно изменить, чтобы ограничить статью для групп пользователей, назначенных на определенные *уровни доступа*: *Общедоступный*, *Гость*, *Зарегистрированный*, *Специальный* или *Суперпользователи*.
5. **Tags** Начните вводить, чтобы найти и выбрать предопределенные теги или добавьте новый, введя его и **нажав Enter**.
6. **Note** Любой комментарий к этой статье, который будет виден под заголовком в списке статей.
7. **Version Note** Добавьте комментарии, чтобы указать, что изменилось в этой версии. Они отображаются в модальном диалоге *Версии*, и поле остается пустым после сохранения.

### Другие вкладки

**Вы можете не увидеть все следующие вкладки**, так как администратор сайта может скрыть некоторые, чтобы помочь поддерживать согласованность макета статей в рамках веб-сайта. Вы также можете увидеть дополнительные вкладки для *пользовательских полей* если они были настроены.

1. **Images and Links** позволяет установить вводное и избранное изображение и/или ссылки для отображения в предварительно заданных позициях. Это может использоваться, если ваша статья будет отображаться в блоге категории.
2. **Options** позволяет указать компоновку статьи и связанную информацию, такую как заголовок, категория, теги, детали публикации и т. д. Обычно устанавливается глобально, но может быть индивидуально настроено для конкретной статьи с помощью этих опций.
3. **Schema** это метод добавления метаданных в статью. Используется роботами, но не виден людям.
3. **Publishing** позволяет установить даты и время публикации для планирования публикации статьи. По умолчанию, когда статья сохранена, она будет опубликована сразу же. Вы также можете установить метаданные для статьи.
4. **Configure Edit Screen** позволяет отображать или скрывать параметры для статьи.
5. **Permissions** показывает разрешения для каждой группы пользователей, которые контролируют, что можно или нельзя делать.

Существуют отдельные статьи по каждой из этих вкладок.

## Сохранение статьи

После того как вы добавили необходимую информацию и контент, вы можете сохранить статью. Существует несколько способов сделать это в зависимости от того, что вы хотите сделать дальше в Joomla.

Чтобы сохранить статью, вы можете выбрать *Сохранить* или *Сохранить и закрыть*. Последняя опция имеет выпадающие варианты *Сохранить и создать новую*, *Сохранить в меню* и *Сохранить как копию*.

- **Сохранить** Сохраните статью и оставьте её открытой для дальнейшего редактирования.
  Хорошей практикой является регулярное сохранение вашей работы над более длинными статьями.
- **Сохранить и закрыть** Сохраните статью и перейдите к списку статей. Кнопка "Сохранить и закрыть" имеет дополнительные выпадающие параметры:
  - **Сохранить и создать новую** Сохраните статью, а затем откройте страницу **Статьи: Новая**. 
    Этот вариант экономит время при добавлении нескольких статей.
  - **Сохранить в меню** Сохраните статью и откройте страницу **Меню: Новый элемент**.
  - **Сохранить как копию** Сохраните статью, затем откройте страницу **Статьи: Редактирование** с числом в скобках, добавленным к названию, и тем же числом после тире, например, -2, в поле псевдонима. Вы можете изменить заголовок и изменить или удалить псевдоним новой, уже созданной статьи.

Системное сообщение укажет на успешное сохранение статьи.

### Ошибки при попытке сохранить:

- Если вы не заполнили обязательные поля, появится красное сообщение об ошибке, указывающее на недостающую информацию, которую необходимо добавить.
- Вы увидите сообщение об ошибке, если у статьи уже существует псевдоним. Вы можете решить эту проблему, изменив поле псевдонима.

## Подсказки

- Если вы не обладаете правами суперпользователя или администратора, уделите время тому, чтобы понять, как настроен сайт. То, что вы сохранили статью, не означает, что она будет видна на сайте. Если используются страницы категоризированного блога, то назначение правильной категории отобразит статью. В противном случае статье необходимо назначить элемент меню. Вы можете сделать это в самой статье или через меню **Меню** Администратора.
- Старайтесь, чтобы заголовки статей были короткими и конкретными.
- Хотя это и можно делать, если несколько пользователей добавляют статьи на сайт, старайтесь избегать создания новых категорий и тегов в статьях. Орфографические ошибки и различия могут легко помешать статьям отображаться там, где это было задумано. Создание категорий и тегов на соответствующей странице списка обеспечивает единообразие по всему сайту.
- При необходимости используйте заметки к статьям. Они могут быть очень полезны, особенно когда несколько человек добавляют статьи.
- Где бы вы ни находились в Joomla, вы можете добавить статью, не заходя на начальную панель — используйте меню администратора Joomla.

