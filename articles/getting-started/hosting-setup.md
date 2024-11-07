<!-- Filename: J4.x:Hosting_Setup / Display title: Настройка хостинга  -->

## Введение

Эта страница предоставляет некоторые рекомендации для тех, кто совсем не знаком с технологией хостинга. Вы можете создать веб-сайт на своем собственном ноутбуке или настольном компьютере. Это называется локальным хостингом и является отличным способом экспериментировать с новыми функциями, при этом он полностью бесплатен. Чтобы сделать контент вашего веб-сайта доступным для остального мира, вам понадобится аккаунт на хостинговом сервисе, за который придется платить.

## Поддерживающее программное обеспечение

Joomla! — это приложение, которое зависит от трех элементов поддерживающего программного обеспечения: язык сценариев PHP, база данных (одна из MySQL, MariaDB или PostgreSQL) и веб-сервер (один из Apache, Nginx, Microsoft IIS или ...). Минимальные версии указаны в следующих таблицах:

### Требования для Joomla! 5.x

| Программное обеспечение | Рекомендуемая | Минимальная |
|--------------------|-----------------|-------------|
| PHP                | 8.3             | 8.1.0       |
| **Базы данных**    |                 |             |
| MySQL              | 8.1             | 8.0.13      |
| MariaDB            | 11.1.0          | 10.4.0      |
| PostgreSQL         | 16.0            | 12.0        |
| **Веб-серверы**    |                 |             |
| Apache             | 2.4             | 2.4         |
| Nginx              | 1.25            | 1.21        |
| Microsoft IIS      | 10              | 10          |

### Требования для Joomla! 4.x

| Программное обеспечение | Рекомендуемая | Минимальная |
|--------------------|-----------------|-------------|
| PHP                | 8.2             | 7.2.5       |
| **Базы данных**    |                 |             |
| MySQL              | 8.0             | 5.6         |
| PostgreSQL         | 11.0            | 11.0        |
| **Веб-серверы**    |                 |             |
| Apache             | 2.4             | 2.4         |
| Nginx              | 1.18            | 1.10        |
| Microsoft IIS      | 10              | 8           |

## Услуги хостинга

Коммерческие услуги хостинга предоставляют все необходимое для поддержки веб-сайта. Некоторые из них также предлагают установку популярных приложений в один клик, таких как системы управления контентом, форумы, вики и так далее. Но, пожалуйста, обратите внимание: специалисты форума Joomla не рекомендуют использовать установку Joomla в один клик.

Каждая хостинговая служба предлагает разные тарифные планы на различных уровнях цен. Чем больше вы платите, тем больше дискового пространства и пропускной способности вы получаете, вместе с большим количеством адресов электронной почты, баз данных и так далее. Некоторые также предоставляют бесплатное доменное имя. В основном, за доменное имя и небольшую ежегодную плату за регистрацию приходится платить.

## Бесплатный хостинг

Бесплатного хостинга не существует! Однако партнерский хостинг-сервис Joomla
предлагает бесплатный веб-сайт Joomla в домене joomla.com. Это дает вам
возможность попробовать создать свой собственный полностью функциональный сайт Joomla
абсолютно бесплатно. Это похоже на тарифный план совместного хостинга, но с ограничениями
и частыми призывами перейти на платный план. Кроме того, бесплатный план должен быть
продлен каждые 30 дней, иначе он будет закрыт. В следующей статье показаны
шаги, необходимые для настройки бесплатного сайта Joomla.

* [Бесплатный хостинг Joomla](jdocmanual?article=user/hosting/free-hosting "")

Если вам понравится Joomla, вы можете перейти на платный план или найти
другой хостинг-сервис, который бы соответствовал вашим потребностям и бюджету.
```

## Виртуальный хостинг

Вы можете приобрести минимальный тарифный план хостинга примерно за £/$/€50 в год. Этот уровень тарифного плана часто называют виртуальным хостингом и он подходит для всего, что не связано с конфиденциальными данными. Бизнесу следует обратиться за специализированной консультацией по выбору подходящих тарифных планов хостинга. Выбор хостинг-сервиса не лишён проблем. Самый дешёвый может иметь чрезмерно ограничительные настройки *php.ini*, которые не отображаются в их рекламе. У некоторых может быть плохая репутация за поддержку.

Если вы выберете план виртуального хостинга, проверьте следующее:

- Поддержка PHP приложений, таких как Joomla, WordPress и Mediawiki.
- Дисковое пространство: 500 МБ является абсолютным минимумом. 1 ГБ или более будет лучше, если вы планируете использовать много изображений.
- Количество баз данных: Joomla использует одну, но вскоре вы обнаружите, что вам нужно 5 или 10 и более. Некоторые планы предлагают неограниченное количество в рамках общего объёма выделяемого дискового пространства.
- Размер базы данных: с помощью Smart Search база данных может расти очень быстро. Если на виртуальном хостинге есть ограничение на размер базы данных, важно выяснить, каково оно. Это может привести к тому, что сайт будет не работать.
- Количество адресов электронной почты: в достаточном количестве!
- Количество HTTP и DB подключений к серверу, которые некоторые виртуальные хостеры ограничивают.
- Резервное копирование: как это делается и есть ли документ Условий обслуживания (TOS), в котором указано, кто несет ответственность за резервное копирование.

Также проверьте панель управления и платформу, которые предлагаются. Судя по сообщениям на форумах, большинство используют cPanel на Linux. Хостинг-сервис должен предоставлять всё базовое программное обеспечение для поддержки веб-сайта:

- Веб-сервер Apache 2.4+ - *каталожные индексы* должны быть отключены. Также поддерживаются:
  - Nginx 1.18+ (меньше пользователей, поэтому меньше поддержки на форуме)
  - Microsoft IIS\[6\] (меньше пользователей, поэтому меньше поддержки на форуме)
- База данных MySQLi 8.1+ или клон MariaDB с поддержкой InnoDB. Также поддерживается:
  - PostgreSQL 11.0+ (меньше пользователей, поэтому меньше поддержки на форуме).
- PHP 8+ рекомендуется.
- Инструмент управления базой данных phpMyAdmin.

Перед покупкой проверьте следующие минимальные требования PHP для Joomla:

- *memory_limit* - Минимум: 256 МБ
- *upload_max_filesize* - Минимум: 64 МБ
- *post_max_size* - Минимум: 64 МБ
- *max_execution_time* - Рекомендуется: 30
- *allow_url_fopen* - true

Многие из этих параметров могут быть установлены пользователем в cPanel. Спросите, возможно ли это.

Если вы приобрели доменное имя, ваш хостинг-сервис настроит его для вас. Они также должны предоставить вам IP-адрес для использования, пока регистрация вашего домена не распространится на серверы доменных имён (DNS), обычно через несколько часов.

Следующая статья показывает, чего следует ожидать, если вы приобретете тарифный план хостинга, который включает в себя интерфейс пользователя cPanel.

* [Хостинг cPanel](jdocmanual?article=user/hosting/cpanel-hosting "Хостинг cPanel")

## VPS Хостинг

План хостинга на виртуальном частном сервере (VPS) предоставляет полный доступ к серверу, который использует совместное оборудование. Он ведет себя как выделенный компьютер. Вы можете останавливать и запускать сервер, перезагружать его и устанавливать собственное программное обеспечение точно так же, как вы бы сделали это на настольном компьютере. Вы можете создавать учетные записи для отдельных пользователей, как в обычном хостинге. Обычно, вы можете разрешить некоторые функции, которые обычно не допускаются в аккаунтах общего хостинга.

Планы выделенного и облачного хостинга схожи по принципу, но предлагают либо выделенные ресурсы, либо ресурсы, адаптированные под ваши нужды.

Эти продвинутые планы здесь не рассматриваются.


## Локальный хостинг

Большинство людей, которые занимаются разработкой сайтов, хранят локальные копии на ноутбуке или настольном компьютере для тестирования обновлений или новых расширений, либо для испытания новых дизайнов. Настройка локального сайта для разработки требует некоторых технических знаний, но следовать простым инструкциям довольно легко.

Следующие статьи описывают, как настроить локальный хостинг на различных типах настольных или портативных компьютеров:

* [Локальный хостинг на Windows](jdocmanual?article=user/hosting/local-hosting-on-windows "Локальный хостинг на Windows") только для Windows
* [Локальный хостинг с XAMPP](jdocmanual?article=user/hosting/local-hosting-with-xampp "Локальный хостинг с XAMPP") для Linux, Mac и Windows.
* [Локальный хостинг на Linux](jdocmanual?article=user/hosting/local-hosting-on-linux "Локальный хостинг на Linux")
