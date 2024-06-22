<!-- Filename: Template_Considerations_During_Migration / Display title: Соображения по шаблонам во время миграции -->

<img
src="https://docs.joomla.org/images/thumb/4/47/Copyedit.png/25px-Copyedit.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/47/Copyedit.png/38px-Copyedit.png 1.5x, https://docs.joomla.org/images/thumb/4/47/Copyedit.png/50px-Copyedit.png 2x"
data-file-width="200" data-file-height="200" width="25" height="25"
alt="Copyedit.png" />This Article Needs Your Help

*This article is tagged because it* **NEEDS UPDATING***. You can help
the Joomla! Documentation Wiki by <a
href="https://docs.joomla.org//docs.joomla.org/index.php?title=Template_Considerations_During_Migration/ru&amp;action=edit"
class="external text" target="_blank"
rel="noreferrer noopener">contributing to it</a>.
<span class="small">More pages that need help similar to this one are
here.</span>
<span class="small">**NOTE-If you feel the need is satistified, please
remove this notice.**</span>*
**Reason:** See section 3.4 and 4

Шаблоны во время миграции доставляют людям расстройство, но в этом нет
необходимости. Немного объяснений - и все может стать ясно.

## Вступление

Шаблоны являются расширениями. Также как расширениями являются
компоненты, модули и плагины, - также и какой-либо шаблон - это
расширение.

При организации какой-либо миграции Вы должны решить как поступить с
Вашим нынешним шаблоном (который определяет \[то как\] выглядит и
ощущается Ваш веб-сайт).

Большей частью \[ситуация\] с Вашим шаблоном подпадет под один из
следующих сценариев:

- Вы используете какой-либо шаблон, приобретенный у какого-нибудь клуба
  шаблонов.
- Вы используете некоторый шаблон, приобретенный у какого-нибудь
  провайдера шаблонов как одно-разовая покупка.
- Ваш шаблон был создан для Вас индивидуально.
- Вы используете какой-либо шаблон по умолчанию, поставляемый с
  установкой \[системы\] Joomla (шаблонами по умолчанию в Joomla 1.5
  являются Rhuk_milkyway, JA Purity и Beez и в Joomla! 2.5 шаблонами по
  умолчанию являются Atomic и две разных версии \[шаблона\] Beez)

## Анализ сценария со своим шаблоном

Прежде чем решать что делать, Вы должны проанализировать будете ли Вы
сохранять нынешний облик своего веб-сайта. Если Вы желаете \[его\]
изменить, то \[сейчас\] - это \[самое\] время решить это. Возможно,
самой весомой причиной, \[по которой\] Вы захотите изменить свой шаблон,
будет задействовать более новые технологии современных шаблонов.
Респонзивные шаблоны не находились в \[распоряжении версии\] 1.5 (разве
что Вы недавно нанимали кого-нибудь, чтобы сделать Ваш шаблон \[версии\]
1.5 дружелюбным переносным устройствам) и даже в начале серии 2.5
мобильные версии шаблонов были худоваты и их респонзивность - не очень.

Давайте рассмотрим эти сценарии по одному:

### You are using Protostar

Protostar is not compatible with Joomla 4.x. The migration will work on
the one-click from Joomla 3.10.x to 4.x but the template will disappear
and be replaced with Cassiopeia upon migration. You will need to plan on
using Cassiopeia or some other template in Joomla 4.

#### Why can't you carry forward Protostar into Joomla 4?

Protostar is based on an old version of Bootstrap (Bootstrap 2) and
jQuery (1.x). The versions of these components are outdated and have
known security issues (Joomla 3 maintained forked versions of these
libraries with security patches applied) - and Joomla 4 has updated
these to the latest version - Bootstrap 5. However this means that
templates need to be updated to use the new HTML syntax that Bootstrap 5
requires.

### Вы используете какой-либо шаблон, приобретенный у некоторого клуба шаблонов

Этот \[сценарий\] самый легкий - в большинстве случаев. Если Вы
приобрели какой-либо шаблон у некоторого клуба, обратитесь к данной
компании и проверьте, нет ли у них версии \[этого\] Вашего шаблона для
Joomla 3.x. Если есть, то \[это\] отлично и осталось немного о чем
подумать. Если Вы переходите с 1.5 на 3.х, \[то\] проверьте, если для
Вас это важно, является ли та версия под Joomla 3.0 респонзивной. Если
Вы переходите с 1.5 на 3, то \[существует\] большая вероятность
\[того\], что между версиями \[Вашего шаблона для Joomla\] 1.5 и \[для\]
3 имеются некоторые различия. Если Вы хотите, чтобы Ваш шаблон \[на
версии 3\] выглядел также, \[то\] будьте готовы внести \[в него\]
некоторые индивидуальные изменения.

Если Вы переходите с 2.5 на 3.х, то проверьте упаковал ли разработчик
\[Вашего шаблона его\] версии для 2.5 и 3.х в один и тот же пакет. Если
нет, то проверьте у разработчика указания по обновлению \[его шаблона\]
с Joomla 2.5 на 3.х. Если \[версии шаблона\] для 2.5 и 3.х находятся в
одном и том же пакете, то Вы золотой. Если нет, то Вы все еще, возможно,
золотой. Это все зависит от маршрута обновления этого самого
разработчика.

### Вы используете какой-либо шаблон, который был приобретен у какого-либо провайдера шаблонов как одно-разовая покупка

Если Вы преобрели какой-либо шаблон у какого-нибудь провайдера шаблонов
как одно-разовую покупку, обратитесь к данному провайдеру и проверьте,
имеется ли версия \[шаблона\] для Joomla 3.x. Если нет, то Вам,
возможно, не повезло. Вы все еще можете попытаться связаться с
кем-нибудь из этой компании и проверить, не смогут ли они обновить его
для Вас и сделать его совместимым с Joomla 3.х.

Если эта \[попытка\] провалится, то тогда Вам будет нужно:

1.  либо выбрать какой-либо новый шаблон
2.  либо конвертировать этот шаблон для его совместимости с Joomla 3.x
    (примечание: может не быть респонзивным)

Первый пункт объясняет сам себя. Вы можете выбрать какой-либо шаблон у
какого-либо коммерческого провайдера или индивидуально изменить шаблон
по умолчанию "Protostar" (смотрите больше по "Protostar" ниже), который
устанавливается вместе с \[системой\] Joomla. Второй пункт не так прост.
Для того чтобы конвертировать свой нынешний шаблон для совместимости с
Joomla 3, смотрите следующий раздел.

## Конвертирование шаблона или миграция шаблона

### Конвертирование шаблонов с 1.5 на 3

-  Миграция шаблона с Joomla 1.5 на
  3.x

### Конвертирование шаблона с 1.5 на 2.5

-  Перенос шаблона с Joomla 1.5 на Joomla
  2.5
- <a
  href="http://magazine.joomla.org/issues/issue-may-2012/item/740-How-to-convert-Joomla-15-template-to-Joomla-25"
  class="external free" target="_blank"
  rel="noreferrer noopener">http://magazine.joomla.org/issues/issue-may-2012/item/740-How-to-convert-Joomla-15-template-to-Joomla-25</a>

### Конвертирование шаблонов с 2.5 на 3

-  Конвертирование шаблона предыдущей версии
  Joomla
- <a
  href="http://stackoverflow.com/questions/16055707/convert-joomla-2-5-template-to-3-0"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">http://stackoverflow.com/questions/16055707/convert-joomla-2-5-template-to-3-0</a>
- <a href="https://www.youtube.com/watch?v=E13QMWgvwlA"
  class="external free" target="_blank"
  rel="nofollow noreferrer noopener">https://www.youtube.com/watch?v=E13QMWgvwlA</a>

### 3.10.x to 4 Template Conversions

This section needs content. If you have knowledge on converting
templates built for Joomla 3 to make them compatible with Joomla 4,
please write a magazine article or post a YouTube or something that can
be linked from this area. Thanks in advance.

### Для Вас разработан индивидуальный шаблон

Если какой-либо шаблон для Вашего веб-сайта на 1.5 или 2.5 был
разработан специально для Вас, то его будет необходимо конвертировать
для совместимости с Joomla 3. Смотрите ссылки в предыдущем разделе. Если
для совместимости Вашего нынешнего шаблона с версией Joomla 3.x Вам
нужно нанять кого-либо, то воспользуйтесь директорией ресурсов Joomla! в
одной из категорий: <a
href="http://resources.joomla.org/en/providers-by-category/category/custom-templates"
class="external text" target="_blank" rel="noreferrer noopener">Template
Development</a> or <a
href="http://resources.joomla.org/en/providers-by-category/category/migration-and-upgrade-services"
class="external text" target="_blank" rel="noreferrer noopener">миграции
и обновления</a>.

### Вы используете какой-либо шаблон по умолчанию, который \[был установлен\] с установкой Вашей \[системы\] Joomla

Шаблоном по умолчанию в Joomla 1.5 являются Rhuk_milkyway, JA Purity и
Beez. Шаблоном по умолчанию в Joomla 2.x являются Atomic и две разные
версии \[шаблона\] Beez. Возможно, Вы его или значительно изменили, или
не \[изменили вообще\]. Если Вы используете какой-либо шаблон по
умолчанию \[версии\] 2.5 и переходите на Joomla 3.x, то Вы сможете
сделать это одним щелчком. Если Вы используете один из шаблонов по
умолчанию для 1.5, то тогда для перехода на Joomla 3.x Вам будет нужно
выполнить одно из выше приведенных указаний (если кто-либо найдет эту
информацию некорректной, пожалуйста, примите участие и исправьте ее).

Прежде чем решать, желаете ли Вы конвертировать свой шаблон \[для
версии\] 1.5 на Joomla 3, Вы возможно, пожелаете серьезно подумать над
поиском какого-либо шаблона, схожего с Вашим нынешним. Весьма вероятно,
что будет дешевле и быстрей использовать какой-либо новый, чем
конвертировать старый. Если Вы желаете конвертировать старый \[шаблон\],
но не имеете \[таких\] навыков, \[то\] посетите страницу официального <a
href="http://resources.joomla.org/en/providers-by-category/category/migration-and-upgrade-services"
class="external text" target="_blank" rel="noreferrer noopener">каталога
ресурсов "Joomla! Resource Directory™"</a>.

Protostar, the template that ships with Joomla 3.x is **not** compatible
with Joomla 4.x. You will need to go through one of the steps above to
update it for Joomla 4.x.

### Когда выбирать шаблон

- Изучайте комании, \[выпускающие\] шаблоны, по одной иначе это станет
  чрезвычайным грузом для Вас.
- Если Вы почувствуете себя под чрезвычайным грузом, сделайте перерыв,
  даже если для этого будет нужно прерваться на один день
- Попытайтесь пропускать чрезвычайно перегруженные и кричащие шаблоны.
  Шаблон нужен Вам для \[того\], чтобы вложить в него Ваше содержимое, а
  не заниматься всем \[тем\], что делает данный шаблон.
- Взгляните на те позиции модулей и \[различные\] вариации этих шаблонов
- При поиске шаблона пейте много воды и делайте легкую зарядку примерно
  через каждый час

## Использование шаблона Protostar, шаблона по умолчанию в Joomla 3.x

Этот раздел не закончен. Если у Вас имеются знания на эту тему, то,
пожалуйста, примите участие и дополните этот документ. В данное время
поиск в Google по индивидуально подстройке Protostar показывает много
страниц вне документации Joomla!.
