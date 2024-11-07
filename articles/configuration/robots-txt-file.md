<!-- Filename: Robots.txt_file / Display title: Файл robots.txt -->

## О роботах

Веб-роботы, также известные как краулеры, веб-сканеры или пауки, — это программы, которые автоматически перемещаются по веб-страницам. Среди множества применений, поисковые системы используют их для индексации веб-контента.

Файл robots.txt реализует 
[Протокол исключения роботов](https://ru.wikipedia.org/wiki/Протокол_исключения_роботов), 
который позволяет администратору сайта определить, какие части сайта не следует проверять определенным пользователям-агентам роботов. Например, доступ к содержимому публичных страниц обычно разрешен, но доступ к CGI, частным и временным каталогам, контент которых не должен индексироваться, часто запрещается.  

## Где разместить файл *robots.txt*

Стандартный файл *robots.txt* включен в ваш корневой каталог Joomla. Файл *robots.txt* должен находиться в корне домена или субдомена и должен называться `robots.txt`.

### Joomla в поддиректории

Файл robots.txt, расположенный в поддиректории, недействителен. Роботы проверяют наличие этого файла только в корне домена. Если сайт Joomla установлен в поддиректории, например, *example.com/joomla/*, файл *robots.txt* **должен** быть перемещен в корень сайта по адресу *example.com/robots.txt*.

**Примечание:** В файле robots.txt имя поддиректории **должно** предшествовать любым запрещенным путям Joomla. Например, правило запрета для каталога `/administrator/` **должно** быть изменено на `Disallow: /joomla/administrator/`.

## Содержимое *robots.txt* для Joomla

Это содержимое [стандартного файла robots.txt для Joomla](https://raw.githubusercontent.com/joomla/joomla-cms/refs/heads/5.2-dev/robots.txt.dist):

```
# Если сайт Joomla установлен в папке,
# например, www.example.com/joomla/, то файл robots.txt
# ДОЛЖЕН быть перемещен в корень сайта,
# например, www.example.com/robots.txt
# И название папки joomla ДОЛЖНО быть добавлено
# перед всеми путями.
# например, правило Disallow для папки /administrator/ ДОЛЖНО
# быть изменено на
# Disallow: /joomla/administrator/
#
# Для получения дополнительной информации о стандарте robots.txt см.:
# https://www.robotstxt.org/orig.html

User-agent: *
Disallow: /administrator/
Disallow: /api/
Disallow: /bin/
Disallow: /cache/
Disallow: /cli/
Disallow: /components/
Disallow: /includes/
Disallow: /installation/
Disallow: /language/
Disallow: /layouts/
Disallow: /libraries/
Disallow: /logs/
Disallow: /modules/
Disallow: /plugins/
Disallow: /tmp/
```

## Исключение роботов

Вы можете исключить каталоги или запретить доступ роботов к вашему сайту, добавив правило Disallow в файл *robots.txt*. Например, чтобы предотвратить посещение каталога */tmp* любыми роботами, добавьте следующее правило:

    Disallow: /tmp/

См. также:

- [Блокировка доступа к вашему контенту](https://support.google.com/webmasters/topic/4598466?hl=ru&amp;ref_topic=9427949)
  на Справочном центре Google.

## Проверка синтаксиса

Для проверки синтаксиса вы можете использовать валидатор для файлов *robots.txt*. Попробуйте один из следующих:

- [Проверьте ваш <em>robots.txt</em> с помощью Тестера robots.txt](https://support.google.com/webmasters/answer/6062598) на Google.
- [Проверка <em>robots.txt</em>](http://www.searchenginepromotionhelp.com/m/robots-text-tester/robots-checker.php) от Search Engine Promotion Help.

### Общая информация

- [Страницы Web Robots](http://www.robotstxt.org/) – это основной сайт для *robots.txt*.
- [Стандарт для исключения роботов](http://www.robotstxt.org/orig.html) – это оригинальный стандарт.
- [Метатег robots, data-nosnippet и спецификации X-Robots-Tag](https://developers.google.com/search/docs/advanced/robots/robots_meta_tag)

*Переведено openai.com*

