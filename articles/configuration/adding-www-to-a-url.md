<!-- Filename: Adding_www_to_a_url / Display title: Добавление www к URL -->

## Регулярные выражения Apache .htaccess

Для простого решения добавьте следующее в ваш файл `.htaccess`:

```bash
    RewriteEngine On
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$ [NC]
    RewriteRule (.*) https://www.example.com/$1 [R=301,L]
```

В этом случае URL вида `https://example.com/index.php?item=1` будет
перенаправлен на `https://www.example.com/index.php?item=1`.

В приведенном выше примере:

* `RewriteCond` определяет условие проверки.
* `%{HTTP_HOST}` использует переменную хоста из запроса (example.com).
* `!` означает НЕ, а `^` означает НАЧАЛО, то есть не начинается с www.example.com
* `(` и `)` захватывают все, что находится между скобками, для использования в подстановке.
* `\` превращает следующий символ из управляющего в фактический символ.
* `.` обычно означает любой символ, но с `\` означает точку.
* `?` делает соответствие необязательным.
* `$` означает КОНЕЦ (необязательного совпадения).
* `[NC]` означает No Case, то есть регистронезависимая проверка.
* `RewriteRule` действует, если URL не начинается с www.
* `(.*)` — это шаблон, в данном случае один символ, повторенный 0 или более раз, что означает часть пути URL. Сохраняется как $1.
* `https://www.example.com/` — это замена для части хоста URL.
* `$1` — сохраненный путь.
* `[]` содержит флаги — инструкции о том, что делать.
* `R=301` — это инструкция отправить заголовок "Moved Permanently".
* `L` означает Last in set — так как совпадение найдено, игнорировать любые последующие правила.

Более полное решение, исправляющее несколько других проблем канонизации одновременно:

```bash
    RewriteEngine On
    #
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.html?\ HTTP/
    RewriteRule ^(([^/]+/)*)index\.html?$ http://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{THE_REQUEST} !^POST
    RewriteCond %{THE_REQUEST} ^[A-Z]{3,9}\ /([^/]+/)*index\.php\ HTTP/
    RewriteCond %{SERVER_PORT}>s ^(443>(s)|[0-9]+>s)$
    RewriteRule ^(([^/]+/)*)index\.php$ http%2://www.example.com/$1 [R=301,L]
    #
    RewriteCond %{HTTP_HOST} !^(www\.example\.com)?$
    RewriteRule (.*) http://www.example.com/$1 [R=301,L]
```

Если вы хотите понять, что все это означает, вы можете прочитать эти статьи:

* [Введение в Apache mod_rewrite](https://httpd.apache.org/docs/2.4/rewrite/intro.html)
* [Введение в переадресацию .htaccess](https://www.danielmorell.com/guides/htaccess-seo/redirects/introduction-to-redirects)

*Переведено openai.com*

