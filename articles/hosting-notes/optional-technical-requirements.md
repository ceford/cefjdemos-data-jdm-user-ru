<!-- Filename: J4.x:Optional_Technical_Requirements / Display title: Дополнительные технические требования -->

На этой странице перечислены *дополнительные* технические требования, которые не обязательны для установки и работы Joomla!, но необходимы для некоторых внутренних API. Список создан для Joomla 4.

| Элемент                   | Описание                                                                                                                                         |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Приложение**            |                                                                                                                                                 |
| JApplicationDaemon        | Требуется наличие `ext/pcntl` и `ext/posix` в PHP                                                                                              |
| **Архивы**                |                                                                                                                                                 |
| BZ2                       | Требуется наличие `ext/bz2` в PHP                                                                                                              |
| GZip                      | Требуется наличие `ext/zlib` в PHP                                                                                                             |
| Zip                       | Требуется наличие `ext/zip` или `ext/zlib` в PHP                                                                                               |
| **Кэш**                   |                                                                                                                                                 |
| APC                       | Требуется наличие `ext/apc` в PHP 5.3 или 5.4, `ext/apcu` в PHP 5.5 или 5.6, не поддерживается в PHP 7.x (Примечание: ЭТО НУЖНО ПРОВЕРИТЬ)      |
| APCu                      | Требуется наличие ext/apcu в PHP 5.3+                                                                                                           |
| CacheLite                 | Требуется наличие пакета PEAR Cache_Lite (тестировалось на версии 1.7.16, будет работать с 1.8)                                                |
| Memcache                  | Требуется наличие `ext/memcache` в PHP и сервер Memcache (Примечание: расширение Memcache не совместимо с PHP 7.x)                             |
| Memcached                 | Требуется наличие `ext/memcached` в PHP и сервер Memcached                                                                                     |
| Redis                     | Требуется наличие `ext/redis` в PHP и сервер Redis                                                                                             |
| Wincache                  | Требуется наличие `ext/wincache` в PHP (только для Windows)                                                                                    |
| XCache                    | Требуется наличие `ext/xcache` в PHP                                                                                                           |
| **Клиентские адаптеры**   |                                                                                                                                                 |
| LDAP                      | Требуется наличие `ext/ldap` в PHP                                                                                                             |
| HTTP/Curl                 | Требуется наличие `ext/curl` в PHP                                                                                                             |
| HTTP/Socket               | Требуется включение функции `fsockopen()` в PHP                                                                                                |
| HTTP/Stream               | Требуется наличие функции `fopen()` в PHP и включен параметр `allow_url_fopen`                                                                 |
| **Криптография**          |                                                                                                                                                 |
| JCrypt                    | Требуется наличие `ext/mcrypt` в PHP для всех шифров, кроме SodiumCipher, который требует `ext/sodium`                                         |
| JKeychain                 | Требуется наличие `ext/openssl` в PHP                                                                                                          |
| **База данных**           |                                                                                                                                                 |
| Microsoft SQL Azure       | Требуется наличие `ext/sqlsrv` в PHP (расширение PHP 5.x поддерживает только Windows, доступна версия, совместимая с Linux для PHP 7.x)        |
| Microsoft SQL Server      | Требуется наличие `ext/sqlsrv` в PHP (расширение PHP 5.x поддерживает только Windows, доступна версия, совместимая с Linux для PHP 7.x)        |
| MySQL                     | Требуется наличие `ext/mysql` в PHP (не поддерживается в PHP 7.x)                                                                              |
| MySQLi                    | Требуется наличие `ext/mysqli` в PHP                                                                                                           |
| Oracle                    | Требуется наличие `ext/pdo` в PHP с поддержкой Oracle (доступно только для 3PD; CMS с ним не запустится)                                       |
| PDO MySQL                 | Требуется наличие `ext/pdo` в PHP с поддержкой MySQL                                                                                           |
| PostgreSQL                | Требуется наличие `ext/pgsql` в PHP                                                                                                            |
| SQLite                    | Требуется наличие `ext/pdo` в PHP с поддержкой SQLite (доступно только для 3PD; CMS с ним не запустится)                                       |
| **Изображения**           |                                                                                                                                                 |
|                           | Требуется наличие `ext/gd` в PHP                                                                                                               |
|                           | Требуется наличие `ext/fileinfo` в PHP                                                                                                         |
| **Сессия**                |                                                                                                                                                 |
| APC                       | Требуется наличие `ext/apc` в PHP 5.3 или 5.4, `ext/apcu` в PHP 5.5 или 5.6, не поддерживается в PHP 7.x (Примечание: ЭТО НУЖНО ПРОВЕРИТЬ)      |
| Memcache                  | Требуется наличие `ext/memcache` в PHP и сервер Memcache (Примечание: расширение Memcache не совместимо с PHP 7.x)                             |
| Memcached                 | Требуется наличие `ext/memcached` в PHP и сервер Memcached                                                                                     |
| Wincache                  | Требуется наличие `ext/wincache` в PHP (только для Windows)                                                                                    |
| XCache                    | Требуется наличие `ext/xcache` в PHP                                                                                                           |
| **ДОПОЛНИТЕЛЬНЫЕ УЛУЧШЕНИЯ** |                                                                                                                                             |
| **Строки**                |                                                                                                                                                 |
| mbstring                  | Включение `ext/mbstring` в PHP для библиотеки phputf8 для использования нативных функций                                                       |

*Переведено openai.com*
