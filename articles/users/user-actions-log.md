<!-- Filename: J4.x:User_Actions_Log / Display title: Журнал действий пользователя -->

## Введение

Компонент журнала действий пользователей (com_actionlogs) предоставляет инфраструктуру для создания журнала аудита активности на сайте. Действия, которые регистрируются в журнале, могут быть точно настроены администратором сайта. Сторонние расширения могут интегрироваться с компонентом, чтобы добавлять собственные сообщения или использовать систему для обработки стандартных действий администратора.

**Примечание:** Только суперадминистраторы имеют доступ к компоненту журнала действий пользователей.

## Журнал Действий Пользователя

Чтобы просмотреть список Журнала Действий Пользователя:

- Выберите **Пользователи → Журнал Действий Пользователя** в меню Администратора.

![страница списка журнала действий пользователя](../../../en/images/users/user-actions-log-list.png)

На этой странице Суперпользователь получает общий обзор всех действий пользователей, выполненных на сайте.

- Экспортировать выбранные в CSV: эта кнопка экспортирует только выбранные элементы в видимом списке.
- Экспортировать все в CSV: эта кнопка экспортирует все записи. Фильтры игнорируются.
- Удалить: эта кнопка удаляет выбранные элементы.
- Очистить журнал: эта кнопка удаляет все записи журнала.
- Опции: форма конфигурации для установки параметров ведения журнала.

## Параметры

Форма настройки параметров лога действий пользователя позволяет суперпользователю выбирать, какие события записывать и включать ли IP-адреса в данные лога.

![страница параметров лога действий пользователя](../../../en/images/users/user-actions-log-options.png)

## Плагины

Система ведения журнала действий использует несколько плагинов:

### Журнал действий - Joomla

Когда включен, этот плагин записывает основные действия пользователей, такие как вход/выход, обновление статьи, добавление модуля. Плагин не имеет параметров.

### Система - Журнал действий пользователей

Когда включен, этот плагин определяет количество дней, после которых журналы будут удалены. Значение ноль означает, что журналы никогда не будут автоматически удаляться.

### Конфиденциальность - Журналы действий

Когда включен, этот плагин экспортирует данные журнала действий по запросу пользователя о конфиденциальности.

## Модуль Последние Действия

Этот модуль отображается только для Суперпользователей на Главной Панели.

![модуль журнала действий пользователя](../../../en/images/users/user-actions-log-module.png)

## Как подключить расширение к системе

Пожалуйста, не стесняйтесь исправлять или улучшать этот раздел.

### Скрипт установки компонента

Добавьте расширение в таблицу (`#__action_logs_extensions`), чтобы оно
отобразилось в конфигурации Логов Действий Пользователя.
```php
            $extension = 'com_mycomponent';
            $db = Factory::getDbo();
            $db->setQuery(' INSERT into #__action_logs_extensions (extension) VALUES ('.$db->Quote($extension).') ' );
            try {
                // Если произойдет ошибка, будет выброшено исключение RuntimeException
                $result = $db->execute();
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Добавьте конфигурацию расширения в таблицу (`#__action_log_config`), чтобы данные о ваших действиях были зафиксированы.
```php
           $logConf = new stdClass();
            $logConf->id = 0;
            $logConf->type_title = 'transaction';
            $logConf->type_alias = $extension;
            $logConf->id_holder = 'id';
            $logConf->title_holder = 'trans_desc';
            $logConf->table_name = '#__mycomponent_transaction';
            $logConf->text_prefix = 'COM_MYCOMPONENT_TRANSACTION';

            try {
                // Если произойдет ошибка, будет выброшено исключение RuntimeException
                // Вставьте объект в таблицу.
                $result = Factory::getDbo()->insertObject('#__action_log_config', $logConf);
            } catch (RuntimeException $e) {
                Factory::getApplication()->enqueueMessage($e->getMessage());
                return false;
            }
```
Конечно, было бы лучше выполнить проверку, чтобы убедиться, что запись уже не существует.

### Помощник компонента

В этом примере помощник компонента используется для сохранения действий.
```php
       /**
         * Записать детали транзакции в лог
         * @param   object  $user    Чтобы не запрашивать текущего пользователя снова.
         * @param   int     $tran_id  ID транзакции, который был создан или обновлён
         * @param   int     $id  Переданный идентификатор из формы для определение новой записи
         * @return  boolean True
         */
        public static function recordActionLog($user = null, $tran_id = 0, $id = 0)
        {
                // получите детали компонента, такие как идентификатор
            $extension =  MycomponentHelper::getExtensionDetails('com_mycomponent');
            // получите данные транзакции для использования в логе для быстрой ссылки
            $tran = MycomponentHelper::getTransaction($tran_id);
            $con_type = "transaction";
            if ($id === 0) { $type = 'New '; } else { $type = 'Update '; }

            $message = array();
            $message['action'] = $con_type;
            $message['type'] = $type . $tran->tran_type . ' - '.$tran->tran_desc . ' $' . $tran->tran_amount;
            $message['id'] = $tran->id;
            $message['title'] = $extension->name;
            $message['extension_name'] = $extension->name;
            $message['itemlink'] = "index.php?option=com_mycomponent&task=transaction.edit&id=".$tran->id;
            $message['userid'] = $user->id;
            $message['username'] = $user->username;
            $message['accountlink'] = "index.php?option=com_users&task=user.edit&id=".$user->id;

            $messages = array($message);

            $messageLanguageKey = Text::_('COM_MYCOMPONENT_TRANSACTION_LINK');
            $context = $extension->name.'.'.$con_type;

            $fmodel = MycomponentHelper::getForeignModel('Actionlog', 'ActionlogsModel');

            $fmodel->addLog($messages, $messageLanguageKey, $context, $user->id);

            return true;
        }

        /**
         * Получение модели из другого компонента для использования
         * @param   string  $name    Имя модели. Необязательно. По умолчанию - собственная для безопасности.
         * @param   string  $prefix  Префикс класса. Необязательно.
         * @param   array   $config  Конфигурационный массив для модели. Необязательно.
         * @return object   Модель
         */
        public function getForeignModel($name = 'Transaction', $prefix = 'MycomponentModel', $config = array('ignore_request' => true))
        {
            \Joomla\CMS\MVC\Model\ItemModel::addIncludePath(JPATH_ADMINISTRATOR . '/components/com_actionlogs/models', 'ActionlogsModelActionlog');
            $fmodel = \Joomla\CMS\MVC\Model\ItemModel::getInstance($name, $prefix, $config);

            return $fmodel;
        }
```
### Форма транзакции на фронтенде

Теперь, коли основа заложена, нужно лишь запустить процесс.
Мы фиксируем информацию о транзакции, которая создается или обновляется, и у нас есть модель, называемая `transactionform.php`. Именно в методе Save мы хотим записать лог.
```php
       // Код выше этой точки проверяет и делает то, что должен делать, и затем после успешного сохранения записи мы проверяем настройку параметра, чтобы увидеть, требуется ли логирование, и передаем ключевые элементы в recordActionLog.
            $table = $this->getTable();

            if ($table->save($data) === true) {

                /* ---------------------------------------------------------------- */
                // Запустить логирование транзакции, если это требуется
                $act_log = $params->get('act_log', 0);
                if ($act_log && $table->id) {
                    // Собрать информацию и записать новый лог действия
                    MycomponentHelper::recordActionLog($user, $table->id, $data['id']);
                }
                /* ---------------------------------------------------------------- */

                return $table->id;
            } else {
                return false;
            }
```
### Языковой файл

Наконец, чтобы помочь в Логах Действий на админской стороне
Joomla, мы хотим задать несколько ключевых элементов данных, которые будут отображаться в языковом файле en-GB/com_mycomponent.ini.
```ini
    COM_MYCOMPONENT_TRANSACTION_LINK="Пользователь {username} создал транзакцию ( {type} )"
```

*Переведено с помощью openai.com*

