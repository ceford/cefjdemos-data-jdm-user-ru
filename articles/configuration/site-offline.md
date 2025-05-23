<!-- Filename: J4.x:Site_Offline / Display title: Сайт не работает -->

## Только для пользователей сайта

Могут возникнуть ситуации, когда вам нужно сделать ваш сайт Joomla!
недоступным для посетителей на короткое время. Для этого имеется простой 
переключатель **Сайт оффлайн**, который можно изменить с **Нет** на **Да** 
по мере необходимости. Когда установлено значение *Да*, все посетители сайта 
видят страницу с сообщением об отключении и формой входа. Стандартную форму 
отключения можно настроить с помощью изображения:

![Экраны отключения сайта](../../../en/images/configuration/site-offline.png)

Переключатель "Сайт оффлайн" не применяется к интерфейсу администратора,
и пользователи, которые могут войти в бэкенд, могут продолжать входить в
фронтенд. Вход на фронтенде запрещен только для пользователей групп "Зарегистрированный",
"Автор", "Редактор" и "Издатель".

## Включить офлайн-режим

- Выберите **Домашняя панель → Глобальная конфигурация** в меню администратора.
- На вкладке **Сайт** установите переключатель **Сайт недоступен** в положение **Да**.
- Затем вы можете выбрать один из следующих вариантов
  - **Использовать пользовательское сообщение**, что означает текст в поле пользовательского сообщения. Или…
  - **Сообщение по умолчанию для языка сайта**, которое звучит как **Этот сайт временно недоступен из-за проведения технических работ. Пожалуйста, зайдите позже.** на английском или его эквивалент на выбранном языке сайта. Это также позволяет выбрать изображение. Или…
  - **Скрыть**, чтобы не показывать никакого сообщения.
- Выберите **Сохранить и Закрыть** на панели инструментов.
- Проведите необходимые работы по обслуживанию.
- Вернитесь к форме глобальной конфигурации.
- Установите переключатель «Сайт недоступен» в положение **Нет**.
- Выберите **Сохранить и Закрыть** на панели инструментов.

## Все пользователи

Вы можете ограничить доступ к вашему сайту, защитив паролем директорию Joomla. Только пользователи, знающие имя пользователя и пароль для доступа к директории, смогут получить доступ к сайту. Вы можете создать более одного такого пользователя. С помощью панели управления хостингом cPanel:

- Войдите в вашу учетную запись cPanel.
- В разделе "Файлы" выберите **Приватность каталогов**.
- Если корень вашего сайта находится в поддиректории public_html
  - Выберите директорию public_html
- Выберите кнопку "Редактировать" для директории, содержащей ваш сайт
  (public_html, если ваш сайт находится в корне веб-сервера).
- Установите флажок **Защитить этот каталог паролем.**
- Введите имя для защищенной директории: по умолчанию может быть достаточно.
- Нажмите кнопку **Сохранить**.
- Появится страница с сообщением об успешном выполнении и ссылкой "Вернуться", выберите её.
- Создайте пользователя для доступа к защищенной директории.
- Введите имя пользователя
- Введите пароль и повторите его (запомните или запишите его).
- Нажмите **Сохранить**.

Теперь проверьте, что для доступа к директории через веб требуется пароль. При посещении вашего сайта вам будет предложено ввести имя пользователя и пароль для доступа к директории. Они могут полностью отличаться от вашего имени пользователя и пароля Joomla.

Чтобы удалить защиту паролем с директории:

- Войдите в вашу учетную запись cPanel.
- В разделе "Файлы" выберите **Приватность каталогов**.
- Если корень вашего сайта находится в поддиректории public_html
  - Выберите директорию public_html
- Выберите кнопку **Редактировать** для директории, содержащей ваш сайт (public_html, если ваш сайт находится в корне веб-сервера). Теперь отобразится символ замка и "Да" под заголовком "Приватность".
- **Снимите флажок** **Защитить этот каталог паролем.**
- Нажмите кнопку **Сохранить**.

Чтобы убедиться, что защита паролем была снята, используйте другой браузер для доступа к вашему сайту или закройте и снова откройте ваш существующий браузер, а затем снова получите доступ к вашему сайту.

*Переведено с помощью openai.com*

