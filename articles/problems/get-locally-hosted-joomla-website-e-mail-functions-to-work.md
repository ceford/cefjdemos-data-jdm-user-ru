<!-- Filename: Get_locally_hosted_Joomla!_website_e-mail_functions_to_work / Display title: Локальная почта -->

## Локальный Хостинг

Большинство интернет-провайдеров блокируют порт 25, поэтому вы не сможете отправлять электронные письма с собственного SMTP-сервера компьютера. Это сделано для блокировки спамеров. Если вы не собираетесь заниматься спамом, вы можете использовать почтовый сервер своего интернет-провайдера.

Чтобы использовать функцию отправки электронной почты с SMTP-сервера вашего интернет-провайдера, даже если вы размещаете свой сайт Joomla на своём компьютере, войдите на свой сайт Joomla как Суперпользователь и перейдите на вкладку **Сервер** на странице **Глобальная конфигурация**. В разделе **Почта** ваши данные должны выглядеть следующим образом:

    From Email: someone@example.com (обычно ваш адрес)
    From Name: SomeName

    Mailer: SMTP
    SMTP Host: smtp.charter.net (то, что ваш интернет-провайдер рекомендует использовать для их SMTP-серверов)
    Sendmail Path: /usr/sbin/sendmail
    SMTP Port: 25
    SMTP Security: STARTTLS
    SMTP Auth: Да (или Нет)
    SMTP Username: johndoe (имя пользователя на одном из ваших почтовых аккаунтов у вашего интернет-провайдера)
    SMTP Password: trr33459 (пароль на одном из ваших почтовых аккаунтов у вашего интернет-провайдера)
Отправьте тестовое сообщение, чтобы убедиться, что всё работает.

Поля Username, Password и Host для SMTP совпадают с теми, которые вы вводите при добавлении аккаунта в Outlook Express, Eudora или любой другой почтовый клиент, который вы используете на своём компьютере.

Вы можете столкнуться с проблемами из-за расширений, которые изменяют адрес *From* в отправляемых письмах. Например, расширение ProjectFork иногда отправляет письма, как будто они отправлены от лица, управляющего проектом. Это может стать проблемой, поскольку некоторые SMTP-серверы интернет-провайдеров не позволяют использовать адрес "from", который не соответствует имени пользователя (например, Rogers в Канаде). Вы получите такое сообщение: "PHPMAILER_FROM_FAILEDname@whatever.com." Решением может стать использование всегда действительного адреса электронной почты от вашего интернет-провайдера для ваших пользователей.

