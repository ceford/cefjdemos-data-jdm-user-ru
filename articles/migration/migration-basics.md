<!-- Filename: jdocmanual?manual=user&heading=migration&filename=migration-basics.md / Display title: Основы миграции -->

## Терминология

Документы Joomla! используют различные термины для обозначения перехода от старой версии к новой:

* **Миграция или мини-миграция** - это термин, который обычно применяется к переходу от старой версии к новой *Основной* версии, иногда через несколько промежуточных *Основных* версий.
* **Обновление** - этот термин обычно применяется к переходу от одной недавней версии к следующей версии в последовательности *Минорных* версий.
* **Обновление системы** - это термин, который обычно используется для процесса Обновления с использованием компонента Joomla Update. Это слово отображается в интерфейсе администратора в Joomla! 3, 4 и 5. В этой статье далее будет использоваться термин *Обновление системы*.

Также стоит знать, что Joomla следует стандарту Семантического Версионирования. Вкратце, учитывая номер версии в формате MAJOR.MINOR.PATCH, например, 5.1.0:

* **MAJOR** версия допускает нарушения обратной совместимости.
* **MINOR** версия допускает добавление функционала, совместимого с предыдущими версиями в рамках Основной версии.
* **PATCH** версия допускает исправления ошибок с сохранением обратной совместимости.

Могут быть дополнительные суффиксы, такие как *альфа*, *бета* или *rc*, но не в стабильных версиях, предназначенных для использования в производственных средах.

## Причины для обновления

Причины для обновления многочисленны и разнообразны:

* **Безопасность** Хотя Joomla! признается как очень безопасная CMS, иногда обнаруживаются уязвимости, которые устраняются в небольших или патчевых выпусках.
* **Изменения хостинга** Joomla использует язык сценариев *PHP* и сервер баз данных, такой как *MySQL*, *MariaDB* или *PostGreSQL*. Они проходят через изменения, и хостинговые службы должны быть в курсе обновлений. Поэтому вы можете обнаружить, что более старая версия Joomla больше не работает или прекращает работать, если вы смените хостинговую службу.
* **Изменения дизайна** Вы можете пожелать сделать ваш сайт более привлекательным, лучше работать с мобильными устройствами и более высоко оцениваться поисковыми системами. Возможно, вам придется соответствовать юридическим требованиям *доступности*.
* **Функциональность** Вы можете захотеть использовать расширение Joomla, предоставляющее некоторые функции, которых нет в основных расширениях Joomla. Выбор может быть ограничен вашей текущей основной версией.

## Резервное копирование перед обновлением

**Это действительно важно!** Даже если вы успешно выполнили несколько промежуточных обновлений, возможно, что-то может пойти не так в процессе обновления. Это может привести к неисправности вашего сайта. Стандартный совет, предлагаемый на форумах, — вернуться к последней резервной копии, выяснить, почему резервное копирование не удалось, исправить это и затем повторить попытку.

**Akeeba Backup** — это бесплатный инструмент, доступный в каталоге расширений Joomla (JED), к которому у вас есть прямой доступ через Систему / Установить расширения / Установить из веба. Его загрузка и установка занимают всего одну-две минуты. Он анализирует вашу систему для настройки профиля с помощью Мастера настройки. Затем он создает резервную копию, которую вы можете скачать для безопасного хранения.

## Самооценка

Перед выполнением *основного* или *незначительного* обновления версии вам необходимо оценить вашу систему и существующие сторонние расширения на совместимость с целевой версией Joomla. Полезно составить список установленных вами сторонних расширений. В Joomla 4 и 5 в списке *Система / Расширения / Управление* есть фильтр для выбора **Неосновные расширения**. Это отсутствует в Joomla 3.

Вы также можете использовать **Ассистент по сообщениям на форуме**. Это инструмент, предназначенный для анализа сайта и составления отчета, подходящего для публикации на форумах Joomla, чтобы помочь экспертам форума диагностировать проблемы с вашим сайтом. Однако у него есть частный пользовательский интерфейс, который сообщает вам все о вашем сайте. Его списки расширений (компоненты и т. д.) указывают, какие из них являются *сторонними*.

Проблемы, возникающие во время обновлений, обычно связаны с тем, что сторонние расширения не совместимы по коду с вашей целевой версией Joomla. Вы должны проверить каждое расширение на совместимость и **удалить** те, которые, как известно, несовместимы. Возможно, позже вы сможете установить совместимые версии.

Вы должны установить один из шаблонов сайта по умолчанию в качестве вашего **шаблона по умолчанию**:

* Шаблоны по умолчанию для Joomla! 1.5: Rhuk_milkyway, JA Purity, Beez.
* Шаблоны по умолчанию для Joomla! 2.5: Atomic, Beez3 и Beez25.
* Шаблоны по умолчанию для Joomla! 3: Protostar и Beez3.
* Шаблон по умолчанию для Joomla! 4: только Cassiopeia.

## Локальное тестирование

Если это возможно, лучше всего настроить локальную среду тестирования на вашем ноутбуке или рабочей станции дома, чтобы протестировать процедуру обновления. Вы можете использовать резервную копию вашего онлайн-сайта, чтобы заполнить ваш тестовый сайт. Ваш домашний сайт должен быть способен запускать копию вашего рабочего сайта и обладать достаточными спецификациями PHP и базы данных, чтобы запускать обновленный сайт. Существует отдельная статья, описывающая, как настроить домашнюю среду тестирования.

## Дополнительная информация

Существует ряд статей, описывающих конкретные сценарии обновления, которые не включены в это руководство, поскольку они устарели или повторяются.

* https://docs.joomla.org/Why_Migrate
* https://docs.joomla.org/Migration_Step_by_Step_Self_Assessment
* https://docs.joomla.org/J3.x:Updating_Joomla_(Install_Method)
* https://docs.joomla.org/J3.x:Updating_Joomla_(Update_Method)
* https://docs.joomla.org/Planning_Migration_-_Joomla_1.5_to_4
* https://docs.joomla.org/Planning_for_Migration
* https://docs.joomla.org/Pre-Update_Check
* https://docs.joomla.org/Template_Considerations_During_Migration
* https://docs.joomla.org/J3.x:Update_fails_with_an_error_message
* https://docs.joomla.org/Converting_an_existing_website_to_a_Joomla!_website
* https://docs.joomla.org/Potential_backward_compatibility_issues_in_Joomla_4
