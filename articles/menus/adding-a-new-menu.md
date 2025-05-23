<!-- Filename: J4.x:Adding_a_New_Menu / Display title: Добавление нового меню  -->

## Введение

Для того, чтобы получить доступ к содержимому на вашем сайте Joomla!, элементы должны быть назначены к Меню. Стандартная установка Joomla! создаёт для вас **Главное Меню**. Во многих случаях вы будете использовать только одно меню, но вы можете иметь и несколько. Это позволяет создавать Меню для различных типов контента, скрытого контента, контента, специфичного для ролей пользователей и многого другого.

Существуют три шага в создании используемого меню:

1. Создание Меню. Это контейнер для Пунктов Меню.
2. Создание Модуля Меню. Это позволяет разместить Меню на странице.
3. Создание Пунктов Меню. Это элементы, выбираемые пользователем, приводящие к конкретным страницам.

Этот скриншот показывает доступные меню на многоязычном сайте. В первоначальной установке Joomla! существует одно *Главное Меню*.

![Список меню](../../../en/images/menus/menus-manage.png)

Список позволяет вам выбрать любую из зелёных или красных кнопок, чтобы перейти непосредственно к списку пунктов меню в этом меню и состоянии.

Этот учебник охватывает шаги, связанные с созданием Меню на сайте Joomla!.

## Создать новое меню

Используйте один из следующих шагов, чтобы создать новое меню:

- В меню администратора выберите *Значок панели управления меню*, чтобы перейти на панель управления меню, затем выберите **Управление**. Или...
- В меню администратора раскройте раздел *Меню* и выберите **Управление**.
- Нажмите кнопку **+ Новое** на панели инструментов.
- В форме ввода данных для меню заполните следующие поля:
  - **Заголовок**: Подходящее название для меню. Оно используется для идентификации меню в менеджере меню.
  - **Уникальное имя**: Это должно быть уникальное идентификационное имя, используемое Joomla! для идентификации этого меню. Пробелы не допускаются, но вы можете использовать символ '-', например, resources-menu.
  - **Описание**: Хотя это поле не обязательно, оно часто бывает полезным на сайте с множеством меню. Описание отображается ниже *Заголовка* в списке меню, как показано выше.<br>
    ![Новое меню](../../../en/images/menus/menus-new.png)
- **Сохранить и закрыть**

В списке Меню вновь созданное меню имеет кнопку с надписью **Добавить модуль для этого меню**, что является следующим этапом в создании меню. Вы можете начать добавлять элементы меню и вернуться позже, чтобы создать модуль меню.

## Создание модуля для меню

В списке Меню столбец *Связанные модули* позволяет выбрать любой существующий модуль меню для редактирования. Вы можете просмотреть его и затем *Закрыть*, не внося никаких изменений. Для вашего нового меню выберите кнопку **Добавить модуль для этого меню**, чтобы открыть модальное окно, содержащее форму ввода данных модуля Меню.

![Форма ввода данных модуля Меню](../../../en/images/menus/menus-module.png)

Поля для заполнения:

* Поле **Заголовок** обязательно для заполнения, поэтому создайте описательный заголовок.
* Кнопка **Показать заголовок** справа используется для *Показа* или *Скрытия* заголовка модуля, что является распространенной функцией всех модулей.
* Поле **Выбрать меню** должно отображать название только что созданного вами Меню.
* Поле **Позиция** используется для выбора позиции в вашем шаблоне, где вы хотите, чтобы отображалось ваше меню.
* Выберите **Сохранить и закрыть**, как только будет добавлена необходимая информация.

В форме *Настройки редактирования модуля* доступно множество опций. Они упомянуты в справочном экране, доступном в форме *Модуль: Редактирование*. Это та же форма, но на обычной странице вместо модального окна. Доступ к ней осуществляется через меню администратора, маршрут Содержимое / Модули сайта в список модулей сайта.

Примечание: внешний вид Меню, как вы хотите, зависит от стиля вашего шаблона.

## Добавление пунктов в меню

Чтобы создать ссылки в вашем меню, вам нужно добавить **пункты меню**. В Joomla есть много *типов пунктов меню*, и компоненты сторонних разработчиков могут добавлять новые типы. В этом учебнике будет добавлена ссылка на отдельную статью.

Вы можете создать статью заранее или во время процесса создания меню. В любом случае, статья должна существовать до того, как можно будет создать пункт меню для неё. В этом примере статья также будет связана с *Ресурсами*. Она предназначена для содержания списка ссылок на файлы PDF.

В списке **Меню**, в столбце **Пункты меню**, выберите значок для недавно созданного меню, в этом примере это *Ресурсы*. Изначально в меню нет пунктов, поэтому в списке будет указано *Нет соответствующих результатов*.

- Выберите кнопку **Создать** на панели инструментов, чтобы создать новый пункт меню.
- В поле **Заголовок** добавьте заголовок, который вы хотите видеть в меню.
- В поле **Тип пункта меню** выберите кнопку **Выбрать**, чтобы открыть модальное окно с списком компонентов. Каждый компонент имеет раскрывающийся список с доступными типами пунктов меню.
  - Выберите **Статьи**, затем **Отдельная статья**.
- В поле **Выбрать статью**: **Либо:**
  - Используйте кнопку **Выбрать**, чтобы выбрать существующую статью. Откроется список статей для выбора. **Либо:**
  - Используйте кнопку **Создать**, чтобы создать новую статью. Вам нужно будет ввести только заголовок статьи. Лучше оставить подробное содержимое на потом.
- Убедитесь, что в поле **Меню** выбрано новое меню.
- Поле **Статус** должно быть установлено на **Опубликовано**.
- Выберите **Сохранить и закрыть**.

![Форма ввода данных для пункта меню](../../../en/images/menus/menus-single-article.png)

Добавьте больше пунктов в новое меню по мере необходимости.

После того, как пункты добавлены в меню, убедитесь, что оно отображается на сайте в правильной позиции.

![Отображение меню](../../../en/images/menus/menus-display.png)

*Переведено сайтом openai.com*

