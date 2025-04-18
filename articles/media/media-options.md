<!-- Filename: J4.x:Media:_Options / Display title: Медиа: Опции -->

## Введение

Страница *Медиа: Параметры* используется для управления загрузкой и хранением медиафайлов, как изображений, так и различных файлов. **Будьте осторожны:** некоторые типы файлов имеют связанные с ними проблемы безопасности — они могут стать путем для проникновения хакера.

Чтобы перейти к форме *Медиа: Параметры*, выберите кнопку **Параметры** на панели инструментов на странице Медиа. Поля в этой форме хорошо прокомментированы и имеют значения по умолчанию, которые должны быть подходящими для почти всех сайтов. Обычно вам нужно использовать форму параметров, только если вы хотите хранить файлы отдельно от изображений или если у вас есть необычный формат файла, который не включен в список по умолчанию.

## Скриншот

![Форма настроек медиа](../../../en/images/media/media-options.png)

## Путь к файлам и папкам

Эти элементы раздельны в форме конфигурации, но оба указывают на папку *images* в новой установке Joomla. Если вы хотите хранить медиафайлы, не являющиеся изображениями (например, PDF, таблицы и текстовые файлы) отдельно, выполните следующие шаги:

1. Создайте папку с именем *files* в корне вашей установки Joomla.
2. Включите плагин *FileSystem - Local* и настройте его, как описано в статье о [Местоположениях медиафайлов](jdocmanual?article=user/media/media-file-locations).
3. Введите название папки, *files*, в поле *Path to Files Folder* в форме медиаопций.

В форме опций введите название папки в поле **Path to Files Folder**. Убедитесь, что вы не используете имя существующей основной папки Joomla.

После настройки вы сможете выбирать между папками изображений и файлов в локальной части представления медиа.

![Страница медиа](../../../en/images/media/media-sample-data-cassiopeia.png)

## Дополнительные типы изображений или документов

Вы можете обнаружить, что изображение или документ не удается загрузить. Если это произошло, убедитесь, что его расширение входит в число *разрешенных расширений*, что его расширение относится к *законным типам расширений* для медиа, и что оно входит в число *законных типов MIME* (вам может понадобиться это проверить). Все три условия должны быть выполнены, иначе загрузка будет отклонена.
*Переведено openai.com*

