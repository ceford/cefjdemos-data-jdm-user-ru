<!-- Filename: J4.x:Updating_from_an_existing_version / Display title: Обновление версии   -->

## Введение

**Помните: всегда делайте резервную копию вашего сайта перед обновлением.**

Рекомендуемый способ обновления установок Joomla! — использовать *Компонент обновления Joomla*.

Стандартная установка Joomla 4 и выше включает в себя полезную панель уведомлений на главной панели после входа в систему. Вы можете сразу увидеть, доступно ли обновление и номер версии.

Сообщение об обновлении, которое появляется на панели уведомлений, зависит от *Канала обновлений*, установленного на странице *Параметры обновления Joomla*, и текущей *Минорной* версии. При установке **Канала обновлений** на **По умолчанию** уведомления о обновлениях выдаются в рамках текущей *Мажорной* версии. При установке параметра на *Joomla Next* вы можете обновиться до последней текущей версии, а затем выбрать кнопку **Проверить наличие обновлений**, чтобы узнать, доступна ли следующая *Мажорная* версия.

Хотя Joomla уведомит вас о доступности обновления, необходимо выполнить обновление самостоятельно. Это простой процесс, который следует выполнить как можно раньше, чтобы поддерживать сайт в актуальном состоянии.

## Доступ к компоненту обновления

Если панель уведомлений отображается на главной панели, выберите кнопку
**x.y.z доступно - обновить сейчас!** чтобы перейти к компоненту обновления.

![уведомление об обновлении joomla в главной панели](../../../en/images/migration/version-update-notification-home-dashboard.png)

Или же, чтобы получить доступ к компоненту обновления из меню администратора,
выберите **Система** для перехода через **Системную панель управления**.

![уведомление об обновлении joomla в системной панели](../../../en/images/migration/version-update-notification-system-dashboard.png)

Системная панель управления имеет *панель обновлений*, которая включает ссылку Joomla,
которая покажет номер доступной версии обновления. Выберите ссылку **Joomla**, чтобы перейти к компоненту обновления.

## Проведение обновления

Joomla! 4 и 5 предоставляют проверку перед обновлением для обновлений до минорных версий. Этот вид компонента обновления Joomla показывает технические характеристики сервера, на котором находится сайт, а также основные и сторонние расширения, которые используют сервер обновлений, в виде списка.

**Примечание:** Экран *Проверка перед обновлением* не отображается, если сайт находится на текущей **минорной** версии.

![joomla проверка перед обновлением](../../../en/images/migration/version-update-pre-update-check.png)

Тщательно проверяйте результаты проверки и принимайте меры по устранению любых выявленных проблем перед обновлением. Возможно, потребуется обновить, отключить или удалить несовместимые расширения перед обновлением Joomla.

Нередко можно увидеть предупреждения о *Рекомендуемых настройках*, так как они часто связаны с сервером и хостингом. Скорее всего, они существовали, когда вы устанавливали Joomla, и, скорее всего, не будут препятствовать завершению обновления.

*Напоминаем, что настоятельно рекомендуется сделать резервную копию, если вы ее еще не сделали!*

Под кнопкой обновления есть ссылка. В большинстве случаев вы можете игнорировать эту ссылку. Она предоставляет возможность вручную загрузить файлы обновления, если ваш сервер находится за межсетевым экраном или не может связаться с серверами обновлений Joomla.

Когда вы проверили проверку перед обновлением и уверены, выберите **Обновить**.

### Подтверждение обновления

![страница начала обновления](../../../en/images/migration/version-update-start-update.png)

Установите флажок, чтобы подтвердить, что вы сделали резервную копию и проверили совместимость расширений, а затем нажмите **Начать обновление**.

### Ход обновления

![страница хода обновления](../../../en/images/migration/version-update-progress.png)

Как только обновление начнется, появится индикатор выполнения, показывающий процесс обновления файлов Joomla.

### Завершение

![страница завершения обновления](../../../en/images/migration/version-update-completion.png)

Когда индикатор выполнения достигнет 100%, системное сообщение подтвердит, что ваш сайт был обновлен, и укажет номер версии. Номер версии также обновится в верхней панели инструментов, рядом с названием сайта.

Нажмите кнопку **Назад**, и вы вернетесь к компоненту обновления Joomla, где можно будет снова проверить наличие обновлений.

## Проверки после обновления

После завершения обновления, следует провести некоторые проверки, чтобы убедиться, что всё прошло как ожидалось, ошибок нет, и что отсутствуют изменения, требующие дальнейших действий.

### Проверка интерфейса

Перейдите на интерфейс сайта и убедитесь, что он работает и отображается так же, как он выглядел до обновления. Используйте комбинацию *Shift + Обновить*, чтобы заставить браузер перезагрузить любые изменения в таблицах стилей и скриптах.

### Системные проверки

В меню боковой панели выберите **Система**, чтобы перейти на панель Системы. Это даст обзор текущего состояния вашего Joomla сайта.

![панель системы после обновления](../../../en/images/migration/version-update-after-update.png)

В этом примере мы видим, что после обновления у нас есть два элемента, которые требуют внимания. Они помечены ярлыком с числом. Число указывает, сколько элементов требуют внимания. Нажимая на каждый, вы сможете их исправить.

**Примечание**: Панель Системы выполняет проверку каждый раз при загрузке страницы. Помните, что настройки кеширования браузера могут на это воздействовать. Хорошей практикой является очистка кеша браузера, проверяя с помощью *Shift + Обновить*.

### Проверка базы данных

Перейдите в **Система → Обслуживание → База данных**. Если ваша база данных актуальна, вы должны увидеть экран, похожий на этот:

![проверка базы данных после обновления без проблем](../../../en/images/migration/version-update-after-update-database-check-no-problems.png)

Если ваша база данных не актуальна, вы увидите экран с перечислением найденных проблем, похожий на этот:

![проверка базы данных после обновления с проблемами](../../../en/images/migration/version-update-after-update-database-check-problems.png)

В этом случае выберите *Имя* проблемного расширения, а затем кнопку Обновить структуру в панели инструментов. Joomla обновит вашу базу данных, чтобы исправить перечисленные проблемы, и затем перезагрузит экран. Если исправление прошло успешно, отображение покажет, что база данных актуальна.

**Примечание:** Если какие-либо ошибки всё ещё существуют, убедитесь, что все таблицы базы данных проверены.

## Обнаружение системы

В некоторых случаях, когда вы обновляете Joomla до новой версии, добавляются новые основные расширения. Если возникли проблемы с обновлением базы данных, эти расширения могли быть установлены неправильно. Чтобы проверить это, перейдите в **Система → Обнаружение**. Затем выберите значок Обнаружение на панели инструментов. Экран должен выглядеть следующим образом:

![Экран Обнаружения без расширений для установки](../../../en/images/migration/version-update-after-update-discover.png)

Если это так, вы знаете, что любые новые расширения, добавленные во время обновления, были правильно установлены в базе данных.

Если есть неустановленные расширения, они будут отображаться на экране аналогично следующему:

![Экран Обнаружения с найденными расширениями для установки](../../../en/images/migration/version-update-after-update-discover-found.png)

В этом случае установите флажки и нажмите на значок Установить на панели инструментов. Joomla установит расширение(я) и затем отобразит экран, показывающий, что никаких расширений не обнаружено. На этом этапе новые расширения были установлены в базу данных.

## Устранение неполадок

Если у вас возникли вопросы, проблемы или ошибки до, во время или после обновления, пожалуйста, задайте их на [Форуме по миграции и обновлению до Joomla! 4.x](https://forum.joomla.org/viewforum.php?f=812).

Если у вас возникли проблемы или ошибки во время процесса обновления, вот несколько советов.

- Очистите кэш вашего браузера. Возможно, были изменения в CSS или Javascript, которые потребуется перезагрузить вашему веб-браузеру после обновления.
- Если после обновления появляются сообщения об ошибках базы данных, обязательно проверьте ссылку **Система → Панель управления → База данных**. В некоторых случаях, если возникла ошибка базы данных, это может помешать выполнению всех обновлений базы данных. В этом случае вы можете выполнить их через ссылку База данных, а затем использовать метод **Система → Установка → Обнаружение**, чтобы проверить и установить любые новые расширения.
- Процесс обновления создаёт или добавляет информацию в файл журнала с именем administrator/logs/joomla_update.php, который вы можете открыть с помощью текстового редактора, чтобы увидеть шаги, записанные в журнале. В нём будут показаны основные шаги (загрузка zip, установка, выполнение SQL-запросов, очистка), что-то вроде этого:

```
2024-04-17T09:13:16+00:00	INFO 127.0.0.1	update	Обновление начато пользователем Джимми (139). Старая версия 5.0.3.
2024-04-17T09:13:18+00:00	INFO 127.0.0.1	update	Загрузка файла обновления с ...
2024-04-17T09:13:28+00:00	INFO 127.0.0.1	update	Файл Joomla_5.1.0-Stable-Update_Package.zip загружен.
2024-04-17T09:13:28+00:00	INFO 127.0.0.1	update	Начало установки новой версии.
2024-04-17T09:13:40+00:00	INFO 127.0.0.1	update	Завершение установки.
2024-04-17T09:13:40+00:00	INFO 127.0.0.1	update	Начало обновлений SQL.
2024-04-17T09:13:40+00:00	INFO 127.0.0.1	update	Текущая версия базы данных (схема) 5.0.0-2023-09-11.
... Множество отдельных SQL-запросов
2024-04-17T09:13:41+00:00	INFO 127.0.0.1	update	Конец обновлений SQL.
2024-04-17T09:13:41+00:00	INFO 127.0.0.1	update	Удаление расширений
2024-04-17T09:13:41+00:00	INFO 127.0.0.1	update	Удаление удалённых файлов и папок.
2024-04-17T09:13:44+00:00	INFO 127.0.0.1	update	Очистка после установки.
2024-04-17T09:13:44+00:00	INFO 127.0.0.1	update	Обновление до версии 5.1.0 завершено.
```

*Переведено с помощью openai.com*
