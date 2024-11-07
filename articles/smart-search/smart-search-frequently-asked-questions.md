<!-- Filename: Smart_Search_Frequently_Asked_Questions / Display title: Часто задаваемые вопросы о умном поиске   -->

## Почему стоит использовать Smart Search?

Поисковые технологии значительно улучшились за годы, прошедшие с момента запуска Joomla, однако стандартный, базовый компонент поиска с тех пор мало изменился. Он все еще очень примитивен и не обладает теми функциями поиска, к которым привыкли пользователи интернета, особенно с учетом распространенности таких продвинутых поисковых систем, как Google. Smart Search позволяет вам внедрить некоторые из этих более продвинутых функций поиска на ваш веб-сайт.

## Зачем создавать плагин умного поиска?

Как правило, если у вас есть тип содержимого, который не обрабатывается основными компонентами Joomla, и вы хотите дать посетителям вашего сайта возможность искать это содержимое, вам нужно будет написать плагин умного поиска для его поддержки. Например, допустим, у вас есть компонент, который хранит информацию о различных видах животных. Компонент поддерживает таблицу базы данных, содержащую поля, такие как научное название, общепринятое название, классификация и описание. В этом случае вам нужно будет создать плагин, который расскажет индексатору умного поиска, как индексировать данные в этой таблице. Помимо индексирования отдельных слов и фраз, вы можете также добавить в плагин каждую запись в карту содержимого, которая в данном случае может включать
<a href="https://ru.wikipedia.org/wiki/Таксономия_(биология)"
rel="nofollow noreferrer noopener">царство, тип, класс, отряд и
семейство биологических классификаций</a>. Карты содержимого затем могут использоваться для фильтрации результатов поиска.

## Можно ли выбрать несколько узлов в выпадающем списке фильтров?

Да, это полностью поддерживается самим Smart Search. Вы можете использовать любой пользовательский интерфейс, который захотите разработать для фильтров. Просто взгляните на код, предоставляемый в стандартном модуле и компоненте Frontend, и вы увидите, как это сделать.

## У меня большой сайт. Могу я использовать Smart Search?

Большим сайтам может быть более выгодно использовать выделенную самостоятельную поисковую систему, такую как Solr, вместо чистой PHP-реализации, используемой в Smart Search. В этой первой итерации расширенного поиска в Joomla вероятно выявление проблем, связанных с масштабируемостью и производительностью. Существует также потенциальная возможность возникновения условий гонки при обновлении индекса при частых изменениях содержания. Ожидается, что эти проблемы будут решены более полно в будущей версии Joomla.

## Почему у Smart Search так много таблиц?

Smart Search добавляет довольно много новых таблиц в установку Joomla, включая 16 «таблиц сопоставления». Эти таблицы сопоставления решают связь многие-ко-многим между поисковыми терминами и элементами контента, которые их содержат. Теоретически эти 16 таблиц можно объединить в одну таблицу, и это окажет незначительное влияние на небольшие сайты. Однако на более крупных сайтах это существенно повлияет на производительность, поскольку таблица сопоставления будет иметь очень большое количество записей, и обновление такой большой таблицы может занять много времени.

## Почему интеллектуальный поиск использует так много дискового пространства?

Поддержание индекса поисковых терминов требует значительного объёма дискового пространства, которое увеличивается по мере того, как в элементах контента содержится больше терминов. Поскольку фразы также индексируются, чем длиннее фразы, тем больше требуется дискового пространства. В Joomla 2.5 для интеллектуального поиска максимальная длина фразы зафиксирована на уровне 3 терминов как разумный компромисс между удобством поиска и использованием дискового пространства. Вероятно, это будет параметр, который можно будет настраивать в будущих версиях интеллектуального поиска.

## Почему записи в таблицах отображения распределены неравномерно?

Возможно, удивительно, что количество записей в каждой из таблиц отображения даже приблизительно не одинаково. Конечно, производительность была бы лучше при равномерном распределении, не правда ли? На самом деле нет, существует компромисс между производительностью вставки и производительностью поиска: равномерное распределение хорошо для первого, но плохо для последнего. Это область постоянных исследований, и количество таблиц и алгоритм распределения могут изменяться с учетом опыта.

## Почему есть отдельный плагин Smart Search Content?

Это просто удобство, которое облегчает включение или отключение всех плагинов Smart Search одной операцией. Это было признано желательным, потому что Smart Search по умолчанию не включен в Joomla 2.5.

## Почему плагины Smart Search используют отдельные события, такие как *onFinderContentAfterSave*?

Smart Search использует собственные события, такие как onFinderContentAfterSave, а не общие эквиваленты, такие как onContentAfterSave, исключительно для удобства, чтобы можно было легко включить или отключить индексирование Smart Search, активировав или деактивировав единственный плагин.

## Почему умный поиск не включен по умолчанию в Joomla 2.5 и Joomla 3.x?

Поскольку Joomla 2.5 является последней в серии 1.x/2.x, она должна поддерживать высокую степень обратной совместимости с предыдущими выпусками этой серии. Так как умный поиск является совершенно новой функцией и не имеет никакого сходства с обычным компонентом поиска в этой или более ранних версиях, было сочтено важным, чтобы пользователи, обновляющие свои сайты с более ранних версий, не были вынуждены менять способ работы поиска на своих сайтах. Действительно, активация умного поиска — это дело, которое должно быть сделано с тщательным обдумыванием.

## Почему нет поискового API?

Основное внимание в текущей версии Smart Search было уделено переносу кода из старого компонента JXtended Finder в последнюю версию Joomla. Поскольку этот код уже считался стабильным и существовало лишь небольшое окно возможностей для его переноса, было решено, что серьёзная переработка Finder выходит за рамки релиза Joomla 2.5. В результате код использует плагины, чтобы избежать любых изменений в основном коде CMS, вместо разработки полноценного поискового API. Мы планируем создать такой API в будущих версиях Joomla.

## Может ли умный поиск выполнять фасетный поиск?

Да. Продвинутый поиск, доступный на странице результатов поиска, и модуль умного поиска предоставляют пример того, как можно фильтровать результаты поиска, чтобы получить фасетный поиск. Ничто не мешает вам создать свои собственные вариации на основе этих базовых идей. Например, вы можете изменить простые выпадающие списки, чтобы принимать множественный выбор, или заменить их массивом флажков.

## Почему не поддерживаются поисковые запросы с подстановочными знаками?

Старая система поиска Joomla использовала очень примитивный метод поиска, который полагался на поиск с использованием полных текстов (FULLTEXT), предоставленный базой данных. Это было очень неэффективно, но обеспечивало простой способ обработки поисковых запросов с подстановочными знаками. Умный Поиск (Smart Search) предоставляет функцию автозаполнения, которая фактически является поиском с подстановочными знаками терминов в индексе, но полноценный поиск с подстановочными знаками не поддерживается из-за потенциальной возможности перегрузки сервера в случае злоупотребления этой функцией. В большинстве случаев поиск с подстановочными знаками используется для учета вариантов написания поискового термина. Например, поиск *juggl\** с целью охватить упоминания о *juggling* (жонглирование), а также о *juggler* (жонглер). Умный поиск пытается избежать необходимости использования подстановочных знаков, вместо этого поддерживая морфологию слов, где слова с одинаковой основой считаются эквивалентными, так что поиск по *juggler* также найдет варианты *juggling* без необходимости использования подстановочных знаков.

## Можно ли использовать интеллектуальный поиск на многоязычных сайтах?

Да, но есть некоторые проблемы, которые необходимо решить, особенно в отношении поддержки азиатских языков.

- Чтобы содержимое индексировалось правильно, необходимо убедиться, что весь контент представлен в формате UTF-8.
- Функция *Имели в виду?* использует функцию Soundex для поиска фонетически похожих поисковых фраз. Однако Soundex не работает хорошо для неанглийских языков и для многих языков не работает вообще. В настоящее время мы исследуем альтернативные методы предоставления этой функции.

Если вы используете интеллектуальный поиск на многоязычном сайте и сталкиваетесь с какими-либо проблемами, пожалуйста, сообщите о них в трекере, чтобы мы могли лучше понять проблемы, которые необходимо решить.

## Будут ли плагины Finder для *jXTended* работать с Smart Search?

Нет. Вам нужно обновить плагины Finder, чтобы они работали с Smart Search. Однако эти изменения не должны быть сложными в реализации и в большинстве случаев приведут к значительному сокращению кода. Если вы посмотрите на текущие плагины Smart Search, то увидите, что обновление плагина Finder довольно просто.

*Переведено с помощью openai.com*
