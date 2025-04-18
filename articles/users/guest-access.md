<!-- Filename: J4.x:Guest_Access / Display title: Гостевой доступ -->

## Уровни доступа

Посетители сайта могут просматривать элементы, такие как статьи, модули и пункты меню, потому что эти элементы по умолчанию имеют уровень доступа "Public". Этот уровень доступа также позволяет авторизованным пользователям просматривать те же элементы контента. Однако есть случаи, когда неуместно, чтобы авторизованный пользователь просматривал элемент контента. Например, пункт меню "Вход" должен быть виден пользователям, которые не вошли в систему, но не должен быть виден пользователям, которые уже вошли. Для этого существует уровень доступа "Guest". Авторизованные пользователи вместо этого должны видеть пункт меню "Выход". Такие элементы необходимо назначать уровню доступа "Registered".

В некоторых случаях также уместно ограничить доступ к статье или модулю для пользователей, которые не авторизованы, или для пользователей, которые вошли в систему.

## Доступ для гостей

Использование уровня доступа для гостей может быть иллюстрировано пунктом меню Вход:

- Выберите **Меню → Главное меню → +** из меню Администратора.
  Используйте любое меню по вашему выбору для новых пунктов.
- В форме **Меню: Новый элемент** введите подходящее название в поле
  **Название**, например, **Вход**.
- В поле **Тип пункта меню** используйте кнопку **Выбрать**, чтобы открыть
  диалоговое окно выбора типа пункта меню.
- В списке **Тип пункта меню** выберите раздел Пользователи и выберите
  элемент **Форма входа**.
- Вернувшись в форму **Меню: Новый элемент**, установите поле **Доступ**
  на **Гость**.
- Сохранить
- При необходимости выберите список Порядок и укажите элемент, **после**
  которого вы хотите, чтобы элемент Вход появился.

![форма меню входа с ограничением до доступа для гостей](../../../en/images/users/guest-access-menu-login.png)

- Сохранить и закрыть.
- Просмотрите сайт. Проверьте, что пункт меню Вход работает. Убедитесь, что он исчезает после входа в систему.

## Зарегистрированный доступ

Использование уровня доступа «Зарегистрированный» может быть проиллюстрировано элементом меню «Выход»:

- Выберите **Меню → Главное меню → +** в меню администратора.
  Используйте любое предпочитаемое вами меню для новых элементов.
- В форме **Меню: Новый элемент** введите подходящее название в поле
  **Название**, например, **Выход**.
- В поле **Тип пункта меню** нажмите кнопку **Выбрать**, чтобы открыть
  диалоговое окно выбора типа пункта меню.
- В списке **Тип пункта меню** выберите раздел «Пользователи» и выберите
  элемент **Выход**.
- Вернувшись в форму **Меню: Новый элемент**, установите поле **Доступ**
  в значение **Зарегистрированные**.
- Сохранить
- При необходимости выберите выпадающий список «Порядок» и выберите элемент, **после** которого вы хотите, чтобы появился элемент входа.

![форма меню выхода, ограниченная зарегистрированным доступом](../../../en/images/users/guest-access-menu-logout.png)

- Сохраните и закройте.
- Посмотрите сайт. Проверьте, работает ли пункт меню «Выход». Убедитесь, что он исчезает после выхода.

*Переведено с помощью openai.com*

