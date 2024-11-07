<!-- Filename: Auto_redirect_guests_to_login / Display title: Автоматическая переадресация гостей на страницу входа -->

## Желаемая функциональность

Предположим, у вас есть некоторые пункты меню, которые требуют, чтобы пользователь был авторизован, например, *Отправить статью*. Вы хотите, чтобы все пользователи могли видеть этот ограниченный пункт меню, независимо от того, вошли они в систему или нет. Желаемое поведение следующее.

* Если пользователь авторизован, он переходит непосредственно к ограниченному пункту меню.
* Если пользователь не авторизован, ему предъявляется форма для входа, и после успешного входа пользователь переходит на ограниченную страницу.
* Если пользователь не зарегистрирован, ему предлагается зарегистрироваться или перейти на другую страницу.

## Решение

Вот как это делается в Joomla!.

1. Создайте новое меню из списка **Меню**, назовите его, например, **Скрытое меню**.
2. Добавьте любые пункты меню, которые будут доступны только зарегистрированным пользователям (например, *Отправить статью*). Установите для этих пунктов меню требуемые уровни доступа — **Зарегистрированный**.
3. НЕ создавайте модуль для *Скрытого меню*. Оно не будет отображаться ни на одной странице, поэтому модуль не нужен.
4. Создайте свое *реальное* меню, назовите его, например, **Меню сайта**, и пункт меню, который будет отображаться для всех пользователей, например, *Отправить статью*.
    - Пункт меню будет иметь тип пункта меню **Алиас пункта меню**, который можно найти в типах пунктов меню **Системные ссылки**.
    - Его параметр *Пункт меню* будет ссылаться на пункт меню *Отправить статью* в *Скрытом меню**.
    - Уровень доступа для этого пункта меню будет **Общедоступный**, так как все должны иметь возможность его видеть и использовать.
5. Создайте модуль для *Меню сайта* так же, как вы делаете для любого меню.
6. Если вам нужны подменю, убедитесь, что вы добавили пункты подменю в **Меню сайта**, а не в **Скрытое меню**.

Теперь, когда гость (незарегистрированный пользователь) заходит в пункт меню *Отправить статью*, его перенаправляет на страницу входа. Если вход выполнен успешно, пользователь перенаправляется на ограниченную страницу **Отправить статью**. Если пользователь уже вошел в систему, перенаправление происходит сразу.

## Пример

Для следующих пунктов меню:

1. Главная
2. Блог
3. Вики
4. Каталог
5. Объявления
6. Вопросы и ответы
7. Магазин
8. Контакты

Все пункты меню должны быть видимы всем на клиентской стороне, но пункты 3, 4, 5, 6 и 7 должны быть доступны только **Зарегистрированным** пользователям.

В этом случае пункты меню с 3 по 7 находятся в *скрытом* меню с параметром **Доступ** установленным на **Зарегистрированным**. Пункты 3 по 7 имеют *Алиасы* пунктов меню в *реальном* меню с параметром **Доступ** установленным на **Публично**.
