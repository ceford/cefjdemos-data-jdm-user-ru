<!-- Filename: contacts.md / Display title: Контакты  -->

## Введение

Контакт — это совокупность личной информации об индивидууме. Вы можете захотеть сделать такую информацию доступной на вашем веб-сайте как для публичного, так и для частного отображения. Например, вы можете захотеть указать ключевых членов вашей организации или сообщества. Компонент Joomla! Contact предназначен для этой цели. Он позволяет разместить на вашем сайте информацию о людях и их личные данные, необязательно зарегистрированных пользователей. Вы также можете позволить любому, либо только зарегистрированным пользователям, отправлять электронные письма этим людям.

В качестве примера использования личных данных вы можете обратиться к странице Википедии о парламентских комитетах Великобритании. Там вы увидите списки комитетов с всплывающей информацией о каждом председателе. Если вы перейдете по ссылке на любой комитет, то увидите список членов с выбранной информацией о каждом индивидууме. Чтобы сделать нечто подобное в Joomla, вы могли бы настроить категории и подкатегории для каждого комитета. Например:

```
Палата общин
- Бизнес
- Культура
- ...
Палата лордов
- Коммуникации
- Конституция
- ...
```
Каждый член комитета имеет дополнительную информацию, которая отсутствует в данных по умолчанию, — политическую принадлежность, такую как Консервативная партия, Лейбористская партия или Шотландская национальная партия, и избирательный округ, область страны, которую они представляют. Эти элементы могут быть собраны с помощью настраиваемых полей.

Требуется тщательность в сборе и отображении личной информации. Индивидуумы могут быть очень чувствительны к тому, что какая-либо информация предоставлена в интернете.

## Контактные данные

Контакты создаются через страницу списка Контактов. Выберите кнопку `Создать` в панели инструментов, чтобы добавить новую запись. Также существует плагин **User - Contact Creator**, который автоматически создает контакт, когда регистрируется новый пользователь.

В форме **Контакты: Редактирование** введите имеющиеся у вас данные о контакте.

![скриншот ввода данных](../../../en/images/contacts/contact-data-entry.png)

**Примечания:**

На скриншоте позиция **Должность** введена как *Председатель*, что имело смысл в контексте списка членов комитета, но не имеет смысла в контексте списка Избранных контактов, состоящего из всех Председателей всех Комитетов. Это нужно уточнить: *Председатель Комитета по культуре, медиа и спорту*.

Поля **Первое...**, **Второе...** и **Третье поле сортировки** должны содержать слова для каждой записи, чтобы обеспечить сортировку в порядке, определенном пользователем, например, в обычном порядке фамилия-имя. Это будет подробно рассмотрено позже в этой статье.

На вкладке **Разная информация** содержится текстовое поле для редактирования с кратким личным заявлением.

Вкладка **Дополнительно** содержит пользовательские поля *Партия* и *Избирательный округ*.

Вкладка **Форма** содержит настройки для формы обратной связи по электронной почте. Если адрес электронной почты не введен, это поле не отображается.

## Отображение Контакта

Компонент Контакт предоставляет четыре пункта меню для отображения контактных данных:

* Один Контакт
* Избранные Контакты
* Список Контактов в Категории
* Список Всех Контактов в Дереве Категорий

Хорошей идеей будет попробовать каждый тип меню, чтобы увидеть, как выглядит вывод.
Некоторые примеры:

### Список Всех Категорий в Дереве Категорий Контактов

В этом случае дерево категорий состоит из родительской категории и двух подкатегорий:
```
Палата Общин
- Комитет по Бизнесу
- Комитет по Культуре
```
![все категории в дереве категорий](../../../en/images/contacts/contact-all-committees.png)

Вторая строка каждой записи исходит из Описания Категории.

Если вы выберете одну из ссылок Комитета, страница Комитета может выглядеть так:

![контакты в категории](../../../en/images/contacts/contact-culture-committee.png)

Макет не совсем такой, как хотелось бы. Было бы хорошо включить миниатюрное изображение каждого человека и лучшее оформление деталей. Это можно сделать с помощью переопределения шаблона (позже).

### Список Контактов в Категории

Для Комитета по Бизнесу есть пункт меню Список Контактов в Категории.
Это приводит к использованию другого макета:

![список категорий контактов](../../../en/images/contacts/contact-category-list.png)

Лучше, но все еще не совсем правильно! Потребовалось переопределение стиля для уменьшения стиля изображения. Опять же, кажется, что переопределение шаблона могло бы быть полезным.

### Избранные Контакты

В этом примере председатели всех комитетов были помечены как избранные.

![избранные контакты](../../../en/images/contacts/contact-featured.png)

## Порядок сортировки

Порядок, в котором отображаются контакты, можно задать в параметрах компонента Контакт или в элементе меню. Последний переопределяет первый, если он установлен. Доступные настройки следующие:
* **Имя** Имя контакта. Это может быть непригодно для алфавитного порядка.
* **Имя для сортировки** Это три поля *Поле сортировки* в форме данных Контакта, упомянутых ранее.
* **Упорядочение** Это порядок, в котором контакты отображаются в списке Контактов.
* **Упорядочение избранных контактов** Избранные контакты появляются перед другими контактами, но в остальном они отображаются в порядке списка.

*Переведено с помощью openai.com*

