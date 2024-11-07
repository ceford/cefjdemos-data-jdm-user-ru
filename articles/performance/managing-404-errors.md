<!-- Filename: Managing_404_Errors / Display title: Управление ошибками 404  -->

## Почему ошибка 404 Not Found имеет значение

Самая распространенная проблема сайтов, которые испытывают трудности с рейтингом в поисковых системах, — это количество ошибок "не найдено", обычно называемых *ошибками 404*, потому что это статус-код, возвращаемый, если страница не может быть найдена.

Во-первых, есть законные причины для появления ошибок 404 — например, если у вас была страница для события, которое уже прошло, или услуги, которую вы больше не предоставляете. В таких случаях страница в конечном итоге будет удалена из индекса поисковых систем и больше не будет связана с вашим сайтом.

Проблема возникает, если у вас много ошибок 404 — например, если вы сняли с публикации категорию, содержащую сотни статей. С точки зрения поисковой системы, это не лучший опыт для их посетителей, потому что они попадают на ваш сайт, а информация, которую поисковая система заявила, что там есть, отсутствует. Именно поэтому не стоит иметь слишком много ошибок 404 на вашем сайте.

## Google Search Central

Первый шаг – выяснить, сколько у вас есть, что можно сделать с помощью [Search Central](https://developers.google.com/search) от Google. Это бесплатный набор инструментов, который позволяет анализировать ваш сайт и быстро выявлять проблемы, ошибки и различные вопросы. Рекомендуется зарегистрировать каждый сайт, которым вы управляете, в Search Central, чтобы в случае возникновения проблем вы получали уведомления.

Когда вы посещаете Search Central, там есть раздел, который показывает ошибки URL в поисковой выдаче, – это покажет вам список ошибок 404, которые Google обнаружил на вашем сайте, и график, который показывает, как это менялось со временем. Если график начинает расти, выясните, почему есть страницы, которые ранее были на вашем сайте, но теперь не могут быть найдены.

Если на вашем сайте возникла временная проблема, вы можете отметить ошибки как исправленные.

![инструменты для вебмастеров](../../../en/images/performance/404-discovery.png)

## Устранение проблем

Выявление проблемы — это только часть процесса. Как только вы обнаружили проблемные URL-адреса, примите меры (если требуется исправление!) путём либо перенаправления страницы на другую страницу сайта, либо восстановления изначальной страницы, либо исследования причин возникновения ошибки 404.

Если вам нужно перенаправить страницу, вы можете использовать плагин System - Redirect для сбора отсутствующих страниц и компонент System / Redirects для перенаправления отсутствующих страниц на существующие.

## Проблемы мониторинга

Если вы хотите отслеживать ваш трафик 404, лучший способ сделать это в Analytics — посмотреть, что происходит, когда у вас возникает ошибка 404. В большинстве случаев заголовок страницы меняется на 404, поэтому мы можем создать пользовательский сегмент, который будет фильтровать трафик с заголовком 404 и указывать, какой это посадочная страница. Это позволит вам отслеживать и проактивно управлять вашими ошибками 404 и гарантировать, что посетители вашего сайта не попадают на неработающие ссылки.

![Уведомления Analytics о трафике 404](../../../en/images/performance/404-analytics-alerts.png)

![Обзор аудитории по уведомлениям Analytics](../../../en/images/performance/404-analytics-alerts-2.png)

В Google Analytics также есть возможность настраивать уведомления. Уведомления позволяют вам получить электронное письмо, когда происходят определенные события. В данном случае мы можем настроить уведомление, чтобы быть оповещенными, если за неделю количество ошибок 404 увеличится более чем на 5% — это может означать, что у нас есть проблема с сайтом, которую необходимо исследовать.

Это отличный способ держать ситуацию под контролем, даже если вы ещё не вошли в систему, чтобы просмотреть свою панель!

![Электронное письмо с уведомлением Analytics](../../../en/images/performance/404-analytics-alerts-email.png)

## Мониторинг ошибок с помощью панели управления

Существует также панель управления, которую вы можете установить, называемая *Панель целостности данных*, которая показывает информацию об ошибках 404, а также некоторые другие метрики, которые могут быть интересны. Просто выполните поиск в Галерее Google Analytics по запросу *Панель целостности данных* и выберите, под какой профиль её установить.

![Целостность данных](../../../en/images/performance/404-data-integrity.png)

*Переведено с помощью openai.com*
