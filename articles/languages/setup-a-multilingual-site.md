<!-- Filename: J4.x:Setup_a_Multilingual_Site / Display title: Настройка многоязычного сайта  -->

## Пример данных

Joomla включает два набора примеров данных: Блог и Многоязычный. Существует третий набор для тестирования, но он предназначен только для пользователей, работающих с версией Joomla для разработчиков. Если у вас есть существующий сайт со статьями, меню и модулями, он по принципу будет похож на сайт с установленными примерами данных Блога.

В домашней панели инструментов в разделе Пример многоязычных данных написано: **Прежде чем запустить, убедитесь, что у вас установлено как минимум 2 языка с их языками содержимого и что никакие примеры данных не были установлены**. Это, вероятно, заставит вас создать многоязычный сайт, вручную выполняя необходимые шаги один за другим. Это процедура, подверженная ошибкам, в которой вы, вероятно, сделаете ошибку, особенно если вы используете несколько языков. Ошибки можно исправить, но весь процесс немного утомительный и может ввести в заблуждение.

Вы можете проигнорировать данный совет и использовать Пример многоязычных данных для настройки многоязычного сайта, если вы понимаете, как в дальнейшем внести некоторые исправления в оригинальные меню и модули.

## Начальный сайт

На вновь установленном сайте Joomla в правой боковой панели находится **Главное меню**.
Оно содержит один пункт меню под названием **Главная** типа Избранные статьи.
Также в правой боковой панели есть **Форма входа**.

Изначально избранных статей нет, поэтому основная часть страницы пуста.

## Пример данных блога

Если вы создали собственный контент для сайта, вам **не следует** устанавливать 
пробные данные блога. Однако, прочтите данный раздел, чтобы понять, как он 
соответствует вашему контенту. В противном случае:

- Выберите **Установить** в разделе мультиязычных пробных данных 
  на главной панели. Этапы установки быстро появятся и исчезнут.
- Вы должны заметить, что установлено несколько новых меню (перезагрузите
  страницу администратора и разверните меню Меню):
  - Главное меню блога.
  - Нижнее меню, содержащее пункты Войти/Выйти.
  - Специальное меню, доступное после входа.
- Выберите значок **Открыть интерфейс** на верхней панели состояния или 
  перезагрузите сайт, если он уже открыт в отдельной вкладке.

Вы должны ожидать увидеть макет, заполненный информацией из избранных статей:

- Вверху находится новое меню **Главное меню блога** для различных 
  макетов блогов и статей.
- В правой боковой панели расположены модули для формы входа, главного меню
  и RSS-ленты моего блога.
- После входа в систему в правой боковой панели появится специальное меню
  для действия только администратора.
- Пункт меню **Главная** в главном меню ведет к макету избранных статей.
- Пункт меню **Блог** ведет к макету категории блога, который несколько отличается
  от макета избранных статей.

Потратьте несколько минут на изучение пунктов меню и тех типов информации, 
к которым они ведут.

## Установка и Публикация Языков Контента

Сначала установите все языки, которые вы планируете использовать. Если вам нужно установить дополнительный язык позже, вам придется выполнить шаги по настройке для этого языка вручную, один за другим. Это будет разобрано в другом месте. В этом учебнике французский, немецкий и валлийский языки были добавлены к языку сайта по умолчанию — английскому — во время установки Joomla. Чтобы добавить языки после установки:

- Выберите **Система** → **Установить языки** в меню администратора.
- Нажмите кнопку **Установить** для каждого языка, который вы хотите использовать.

Установленные языки должны быть **Опубликованы**, чтобы они стали доступны. В меню администратора:

- Выберите **Система / Панель управления / Языки контента**
- В колонке Статус **Опубликуйте** каждый из языков, которые вы желаете использовать.

## Многоязычные демо-данные

Установка многоязычных демо-данных имеет последствия, с которыми вам придется разобраться позже:

- Меню в правой боковой панели будут сняты с публикации. Это означает, что модуль Главного меню будет снят с публикации, и не будет ссылки на макет Избранных статей. Если у вас были другие ссылки в Главном меню, они также станут недоступными.
- Специальное меню будет снято с публикации. Оно предоставляло ссылку для создания нового поста.

Многоязычные демо-данные предоставляют следующие дополнительные возможности:

- Категория статей для каждого языка.
- Статья, настроенная для каждого языка, хотя и в псевдотексте Lorem ipsum.
- Отдельное меню для каждого языка. Вы увидите это в списке **Администратор**→**Меню**.
- Модуль меню **Main Menu xx-YY** в правой боковой панели сайта, где xx-YY — это код языка, например en-GB.
- Пункт меню **Main** теперь ведет к макету блога категории для статей на выбранном языке. Он содержит только одну статью.
- В правой боковой панели есть модуль **Переключатель языка**. Он без заголовка, чтобы избежать необходимости в отдельном модуле для каждого языка с переведенными заголовками. Выбор осуществляется с помощью флага языка. Попробуйте его.

Следует заметить: слова, предоставленные Joomla, будут переведены, например, в навигационной цепочке (Breadcrumbs) и форме входа. Слова, набранные пользователями, нужно переводить вручную, например, форма входа и Главное меню. Подробнее об этом позже.

## Исправление начальных проблем

### Порядок языков

Вы можете заметить, что в переключателе языков языки расположены в обратном алфавитном порядке. Чтобы изменить порядок:

- Выберите **Система → Контент-языки** в меню Администратора.
- Используйте вертикальные иконки многоточий, чтобы перетащить языки в желаемый порядок.
- Перезагрузите сайт, и теперь в переключателе языков будут языки в вашем предпочтительном порядке.

### Порядок модулей в правой боковой панели

Порядок модулей в правой боковой панели – это вопрос личных предпочтений. Чтобы изменить порядок:

- Выберите **Контент → Модули сайта** в меню Администратора.
- Отфильтруйте по **Позиция → sidebar-right**.
- Выберите иконку столбца порядка, чтобы открыть перетаскиваемые ручки (вертикальные иконки многоточий). Иконка заголовка столбца должна быть стрелкой, указывающей вверх.
- Перетащите элементы в следующий порядок:
  - Переключатель языков
  - Главное меню (все варианты – порядок не имеет значения).
  - Специальное меню
  - Форма входа
  - Архивные статьи
  - Синдикация

### Избранные статьи

Оригинальное Главное меню не опубликовано, но пункт меню Домашняя страница, который оно содержит, можно воссоздать в другом месте. Самое удобное место – верхнее меню.

- Выберите **Меню** → **Главное меню блога** в меню Администратора.
- Выберите кнопку **Создать** на панели инструментов.
- Введите **Заголовок** в форме **Меню: Новый элемент**, например **Избранное**.
- Используйте кнопку **Выбрать** в поле **Тип элемента меню**.
- Выберите **Статьи** → **Избранные статьи** из списка **Тип элемента меню**.
- Выберите **Сохранить** на панели инструментов.
- В поле **Порядок** выберите **- Первым -**.
- На вкладке **Макет блога** установите **Вводные статьи** на 3.
- Выберите **Сохранить & Закрыть** на панели инструментов.

### Назначение модулей сайта

Оригинальный макет домашней страницы с избранными статьями был создан путём назначения выбранных модулей для отображения только на этой странице. Новую страницу с избранными нужно добавить для каждого из этих модулей.

- Выберите **Контент** → **Модули сайта** в меню Администратора.
- Найдите и выберите элемент **Изображение**.
- На вкладке **Назначение меню** найдите и отметьте элемент **Избранное** в разделе **Главное меню блога**.
- Выберите **Сохранить & Закрыть** на панели инструментов.
- Найдите и выберите элемент **Последние посты**.
- На вкладке **Назначение меню** найдите и отметьте элемент **Избранное** в разделе **Главное меню блога**.
- Выберите **Сохранить & Закрыть** на панели инструментов.

## Перезагрузка сайта

Когда вы перезагружаете сайт, первый пункт в верхнем меню будет ссылкой "Рекомендуемые", ведущей к макету "Рекомендуемые статьи". Соседний пункт "Блог" представляет собой более компактный макет "Категория - Блог". Попробуйте переключатель языков. Поставляемый Joomla текст в "хлебных крошках" и форме входа изменяется соответствующим образом. Также, в рекомендуемых статьях теперь включена одна статья из многоязычных образцов данных на выбранном языке. Она может находиться на последней странице.

### Гибридный или полностью многоязычный сайт

На этом этапе у вас есть гибридный сайт: некоторый контент доступен на всех языках, а некоторые материалы доступны на конкретном языке. Если вы хотите полностью многоязычный сайт, вам необходимо снять с публикации модуль "Блог" в верхнем главном меню и, возможно, другие модули. В некоторых случаях вы можете захотеть создать модули, специфичные для конкретного языка, например, форма входа может иметь версии с заголовками Formulaire de connexion, Login Formular и Ffurflen Mewngofnodi.

Что делать дальше — решать вам!

## Оригинальное Главное Меню

Ваш исходный модуль Главного Меню, который сейчас не опубликован, мог содержать дополнительные элементы меню. Вы можете опубликовать его. Проблема в том, что пункт "Главная" ссылается на то же самое место, что и страницы "Главная" на каждом из языковых меню, но только на английском. Вы можете обойти это следующим образом:

- Выберите **Меню** → **Главное меню** в меню администратора.
- Выберите пункт меню **Главная**.
- Перейдите на вкладку **Тип ссылки**.
- Установите **Показывать в меню** на **Нет**.
- Выберите **Сохранить и закрыть** на панели инструментов.
- Выберите **Контент** → **Модули сайта** в меню администратора.
- Найдите **Главное меню** и опубликуйте его, изменив серый крестик на
  зеленую галочку.

Видимые элементы в исходном Главном Меню теперь должны работать нормально. Если в Главном Меню нет видимых элементов, оно не будет отображаться.

## Добавление дополнительного языка

После первоначальной настройки многоязычного сайта, если вы хотите добавить еще один язык, вам придется пройти через все шаги вручную по очереди:

### Шаг 1: Установка языка

- Выберите **Система** → **Установить** → **Языки** в меню Администратора.
- Найдите необходимый язык в списке **Расширения: Языки**.
- Нажмите кнопку **Установить**.
- Появится сообщение: **Установка языкового пакета выполнена успешно.**

В этом примере дополнительным языком является испанский.

### Шаг 2: Публикация и порядок

- Выберите **Система** → **Управление** → **Языки контента** в меню Администратора.
- Включите вновь установленный язык: нажмите кнопку Статус, чтобы серый крест стал зеленой галочкой.
- Используйте значки вертикальных троеточий, чтобы перетащить языки в желаемом порядке.

### Шаг 3: Создание меню

- Выберите **Меню** → **Управление** в меню Администратора.
- Нажмите кнопку **Создать** в панели инструментов.
- Введите подходящее название и уникальное имя меню, примеры: Главное меню (es-ES) и mainmenu-es-es.
- Введите описание, пример: Главное меню для сайта на испанском языке (es-ES).

### Шаг 4: Добавление модуля меню

- Выберите **Меню** → **Управление** в меню Администратора.
- Выберите кнопку **Добавить модуль для этого меню** для вновь созданного меню.
- Введите подходящее название, пример: Главное меню es-ES.
- Выберите позицию: Sidebar-right.
- Выберите язык: испанский (es-ES).
- Выберите **Сохранить**.
- Упорядочьте модуль: в списке упорядочивания выберите элемент, после которого должен появиться новый элемент.
- Выберите **Сохранить и закрыть**.

### Шаг 5: Добавление категории

- Выберите **Контент** → **Категории** в меню Администратора.
- Нажмите кнопку **Создать** на панели инструментов.
- Введите подходящее название, пример: Categoría (es-es).
- Выберите правильный язык: испанский (es-ES).
- Выберите вкладку **Связи**.
- Для каждого языка выберите категорию. В каждом случае доступен только один выбор.
- Выберите **Сохранить и закрыть**.

### Шаг 6: Добавление элемента меню

- Выберите **Меню** → **Главное меню (es-ES)**, вновь созданное меню.
- Нажмите кнопку **Создать** на панели инструментов.
- Введите подходящее название, пример: Página de inicio.
- Используйте кнопку Выбрать в поле **Тип элемента меню**, чтобы выбрать тип элемента.
- В списке всплывающих окон выберите **Статьи** → **Блог категории**.
- В поле Выбор категории используйте кнопку Выбрать.
- В списке всплывающих категорий выберите категорию Categoría (es-es).
- Установите поле **Страница по умолчанию** в положение **Да**.
- В раскрывающемся списке **Язык** выберите **Испанский (es-ES)**.
- **Сохранить и закрыть**

### Шаг 7: Добавление статьи

Простой способ добавить статью для нового языка — это скопировать существующую статью.

- Выберите **Контент** → **Статьи** в меню Администратора.
- Выберите статью для копирования, в этом примере **Статья (en-GB)**.
- В форме **Статьи: Редактирование** измените название на **Статья (es-ES)**.
- Измените **Категорию** на **Категория (es-es) (es-ES)**.
- Измените **Язык** на испанский (es-ES).
- Выберите **Сохранить как копию** из выпадающего списка **Сохранить и закрыть** в панели инструментов. **Внимание!**
- Выберите вкладку **Связи**.
- Для каждого языка выберите статью для связи - эквивалентную статью на каждом языке.
- Выберите **Сохранить и закрыть** в панели инструментов.

## Добавление многоязычной статьи

Предположим, вы хотите создать статью на каждом из выбранных вами языков.

- Выберите **Контент**→**Статьи**→**+** в меню администратора или кнопку **Новый** на панели инструментов в списке статей.
- Введите заголовок статьи, например, **Уильям Шекспир**.
- Установите поле **Категория** в значение **Категория (en-gb) (en-GB)**.
- Установите поле **Язык** в значение **Английский (en-GB)**.
- Введите текст статьи, например, из Wikipedia:

«Уильям Шекспир (крещён 26 апреля 1564 – 23 апреля 1616) был английским драматургом, поэтом и актёром. Он широко известен как величайший писатель на английском языке и величайший драматург в мире. Его часто называют национальным поэтом Англии и "Бардом из Авона" (или просто "Бардом"). Его дошедшие до нас произведения, включая соавторские, состоят из примерно 39 пьес, 154 сонетов, трёх длинных повествовательных поэм и нескольких других стихотворений, некоторые из которых имеют неопределённую авторскую принадлежность. Его пьесы переведены на все основные современные языки и исполняются чаще, чем пьесы любого другого драматурга. Он остаётся, вероятно, самым влиятельным писателем в английском языке, а его работы продолжают изучаться и интерпретироваться заново».

- Выберите **Сохранить** на панели инструментов.
- Выберите вкладку **Ассоциации**.
- Для каждого языка:
  - Нажмите кнопку **Создать**.
  - В форме всплывающего окна **Новая статья** введите переведённый заголовок, например, **Уильям Шекспир**.
  - Установите категорию в соответствии с выбранным языком.
  - Введите переведённый текст в поле **Текст статьи** (вы можете попробовать <a href="https://translate.google.com/" rel="nofollow noreferrer noopener">https://translate.google.com/</a>).
  - Выберите **Сохранить и закрыть**.
- После создания новой статьи для каждого языка выберите **Сохранить и закрыть**.

## Главное меню

Если у вас есть ссылка на статью для всех языков в главном меню, и позже вы используете эту статью в качестве основы для связанных статей на других языках, вам нужно будет изменить ссылку в главном меню. В противном случае переключение языков с выбранной данной статьей приведет к ошибке «Страница не найдена» на выбранном языке.

- Выберите **Меню** → **Главное меню** в администраторском меню.
- Выберите пункт меню, который нужно изменить, например, **Уильям Шекспир**.
- Измените поле **Язык** на **Английский (en-GB)**.
- Выберите **Сохранить и закрыть** в панели инструментов.

Если в главном меню есть только этот пункт, то модуль исчезнет при переключении на другие языки.

*Переведено с помощью openai.com*

