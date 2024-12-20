<!-- Filename: Smart_Search_on_large_sites / Display title: Умный поиск на больших сайтах  -->

## Индексация сайта

Смарт Поиск работает путем создания и поддержания независимого индекса поисковых терминов в ряде таблиц базы данных. Проблема для крупных сайтов заключается в том, что процесс индексации может быть достаточно тяжелым по использованию ЦП, памяти и диска. Даже после первоначального создания индекса, инкрементные обновления также могут быть тяжелыми. Хорошая новость заключается в том, что выполнение запросов к индексу — это относительно быстрая и легкая операция.

Смарт Поиск подходит для большинства сайтов на Joomla. Однако поиск представляет особенные вызовы для крупных сайтов. Следует помнить, что Смарт Поиск является чистой реализацией поисковой системы на PHP, и для особенно больших сайтов может быть лучше использовать автономную поисковую систему, такую как Solr.

Для использования Смарт Поиска на крупном сайте, вам, вероятно, потребуется настроить некоторые параметры конфигурации. Далее приводятся общие советы о том, на что обратить внимание и что попробовать изменить. Существуют несколько известных нерешенных проблем, связанных с работой Смарт Поиска на крупных сайтах, которые, надеемся, будут решены в будущих версиях. Они также описаны здесь.

## Всегда используйте индексатор CLI

Поскольку начальный процесс индексирования может занять длительное время, лучше запускать индексатор из командной строки, чтобы избежать проблем с истечением времени сеанса браузера. Индексатор CLI не прервется, независимо от того, сколько времени потребуется для завершения, и его можно легко прервать, если возникнут проблемы. Кроме того, сообщения об ошибках видны при использовании индексатора CLI, в то время как они скрыты при запуске из Администратора.

Чтобы использовать CLI, откройте терминал, перейдите в папку cli в корневой директории вашего сайта и выполните следующую команду:

```
php joomla.php finder:index
```

## Пакетная обработка

Индексатор разбивает работу по индексированию на пакеты элементов контента. По умолчанию размер пакета установлен на уровне 30, что означает, что до 30 элементов контента будут индексироваться за один пакет. Увеличение размера пакета потенциально может сделать процесс индексирования быстрее, но это потребует больше памяти и, возможно, больше временного дискового пространства.

## Проблемы с нехваткой памяти

Если индексатор сталкивается с нехваткой памяти, попробуйте вносить следующие изменения по одному, пока проблема не будет решена.

1. Уменьшите размер пакета. Если у вас особенно большие элементы контента, индексатор может столкнуться с нехваткой памяти даже для одного элемента контента, поэтому сначала попробуйте уменьшить его до 5, и если проблема с нехваткой памяти всё ещё сохраняется, уменьшите до 1.
2. Если у вас есть возможность выделить больше памяти для индексатора, сделайте это. Вы можете увеличить объём памяти, выделяемой командному индексатору, используя дополнительный параметр в командной строке. Например, чтобы увеличить предел памяти до 256 Мб, используйте следующую команду, заменив *256M* на то количество памяти, которое вы можете безопасно выделить для процесса на вашей системе.<br>
   *php -d memory_limit=256M finder_indexer.php*
3. Уменьшите лимит таблицы в памяти. По умолчанию это 30000 терминов, что означает, что как только временная таблица *#__finder_tokens* в памяти достигнет этого количества строк, индексатор переключится на использование таблицы на диске вместо таблицы в памяти. Возможно, у вас недостаточно памяти для обработки полной или почти полной таблицы в памяти, поэтому уменьшение лимита заставит индексатор переключиться на диск раньше и таким образом использовать меньше памяти. Попробуйте 10000 или даже гораздо меньшие числа.
4. Измените используемый для таблиц *__finder_tokens* и *#__finder_tokens_aggregate* движок базы данных с MEMORY на InnoDB. Это может серьёзно повлиять на производительность, так как больше процессов индексирования будет использовать диск вместо памяти, но это может позволить индексатору завершить работу без нехватки памяти. Ожидайте, что процесс индексирования будет выполняться намного дольше. Однако на производительность поиска это никак не повлияет.
5. Попробуйте определить, какие элементы контента вызывают нехватку памяти у индексатора. Если это не очевидно, можно попробовать отключить все плагины "Умный поиск", кроме одного. Запуск индексатора с включённым только одним плагином за раз должен показать, какие типы контента вызывают проблему. В крайнем случае рассмотрите возможность разбить несколько исключительно больших элементов контента на отдельные элементы. Если проблема связана с пользовательским типом контента, посмотрите код плагина и рассмотрите возможность индексирования меньшего количества доступного контента на элемент.

## Проблемы с нехваткой дискового пространства

Таблицы индекса Smart Search могут быстро увеличиваться в размере! Таблицы *#__finder_links_termsX* (где *X* — это одна шестнадцатеричная цифра) содержат одну строку на термин/фразу на элемент контента, и одна статья Joomla, содержащая 1000 слов, обычно приводит к добавлению примерно 3000 строк в эти таблицы. Вторая статья аналогичного размера добавит аналогичное количество строк, даже если обе статьи содержат одни и те же слова. Сайт с десятками тысяч статей, некоторые из которых могут содержать тысячи слов, скорее всего, столкнется с ситуацией, когда эти таблицы маппинга содержат миллионы строк. В таких условиях не редкость, когда индексационные таблицы занимают несколько гигабайт дискового пространства.

В текущей версии Smart Search вы мало что можете сделать с этой проблемой. Однако, надеемся, что в следующем выпуске вы сможете регулировать количество слов на фразу, которая будет индексироваться. В настоящее время этот параметр установлен на уровне 3, что означает, что каждое индексируемое слово также индексируется как часть пары соседних слов и как часть троицы соседних слов. Это полезно для функции автодополнения и в целом улучшает качество результатов поиска. На сайтах, где проблема нехватки дискового пространства актуальна, было бы полезно уменьшить этот параметр до 2 или даже до 1, чтобы таблицы маппинга были соответственно меньше.

## Заметки

1. В настоящее время нет блокировки параллельности, чтобы предотвратить выполнение индексации более чем одним процессом одновременно. Это почти наверняка приведет к повреждению индекса. Даже если кто-то будет сохранять изменения в элементе контента во время полной индексации, это может потенциально повредить индекс.

*Переведено openai.com*  

