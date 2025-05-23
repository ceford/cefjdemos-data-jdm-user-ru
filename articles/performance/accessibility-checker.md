<!-- Filename: jdocmanual?manual=user&heading=performance&filename=accessibility-checker.md / Display title: Средство проверки доступности   -->

## Система - Проверка доступности Joomla

Это основной плагин, который можно использовать для проверки доступности при создании
содержимого статьи. Следующий скриншот показывает некоторые настройки плагина:

![Настройки формы плагина](../../../en/images/performance/performance-jooa11y-plugin-form.png)

С параметром **Показывать всегда**, установленным в положение *Вкл.*, значок отчета появляется на каждой
странице сайта. Это полезно для разработки, но никогда не должно оставаться включенным
для рабочего сайта. Установите его в положение **Выкл.**!

С параметром *Показывать всегда*, установленным в положение *Вкл.*, на каждой странице сайта
в нижнем правом углу отображается значок с количеством проблем. Следующий скриншот
показывает значок, выбранный для отображения панели информации. Она включает в себя
очертания страницы, комментарии по читаемости и предупреждения, которые можно выбрать по одному.
Первый вопрос был выбран.

![Проверка доступности сайта](../../../en/images/performance/performance-jooa11y-site-display.png)

Форма *Статьи: Редактировать* имеет кнопку **Проверка доступности** на панели инструментов.
Она показывает проверку для отдельной статьи во всплывающем окне:

![Проверка доступности редактора](../../../en/images/performance/performance-jooa11y-admin-display.png)

## Исправление проблем

Проверка доступности — это инструмент для выявления проблем. Он не исправляет проблемы. Это ваша задача. У проверяющего есть некоторые настройки, которые вы можете переключать Вкл/Выкл по мере необходимости. Они включают Контраст, Ярлыки форм, Ссылки (продвинутые) AAA, Читаемость AAA, Темный режим и Цветной фильтр с моделированием четырех типов дефектов цветоощущения.

Для получения дополнительной информации смотрите обзор Sa11y.

Например, о читаемости говорится:

>Sa11y может оценить показатель читаемости всех абзацев и содержания списков. Хороший показатель читаемости указывает на то, что ваше письмо понятно и легко воспринимается. Он основан на средней длине предложений и слов на вашей странице, используя формулу, известную как тест легкости чтения Флеша (Википедия). "Хороший" показатель чтения находится между 60 и 100. Иногда может быть трудно добиться хорошего показателя читаемости. Большинство ваших страниц могут иметь оценку "трудно". Помните, что эта функция используется только для оценки читаемости вашего контента. Она должна использоваться только как справочная информация, а не как показатель соответствия. Sa11y рассчитывает показатель читаемости на основе всего содержимого абзацев (`<p>` теги) и списков (`<li>` теги). Низкий показатель не влияет на состояние прохождения или неудачи Sa11y.

*Переведено с помощью openai.com*

