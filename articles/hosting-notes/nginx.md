<!-- Filename: Nginx / Display title: Nginx  -->

<a href="http://nginx.org/"
rel="nofollow noreferrer noopener">Nginx</a> — это легковесный веб-сервер,
который обслуживает
<a href="https://en.wikipedia.org/wiki/Nginx"
rel="nofollow noreferrer noopener">около 33%</a> веб-серверов во всех доменах. Если у вас нет специальных требований, которые требуют тяжелого веб-сервера, как Apache, то лучше использовать Nginx.

Ниже приведены инструкции по запуску Joomla! с <a
href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/"
rel="nofollow noreferrer noopener">примером PHP FastCGI</a>.

## Установка Nginx

Для Ubuntu выполните *aptitude install Nginx*. Для других дистрибутивов используйте соответствующий пакетный менеджер или смотрите <a href="https://www.nginx.com/resources/wiki/start/topics/tutorials/install/" rel="nofollow noreferrer noopener">страницу установки Nginx</a>.

## Установка PHP FastCGI

Для Ubuntu прочтите <a href="https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/" rel="nofollow noreferrer noopener">пример использования PHP FastCGI</a>.

Для Gentoo PHP будет работать как служба FastCGI (FPM), поэтому сервер Nginx будет запускать PHP как отдельный процесс:

```
# echo "dev-lang/php gd gd2 curl simplexml tokenizer dom tidy sqlite xml fpm cgi" >> /etc/portage/package.use
# emerge php
```

Стандартные настройки PHP-FPM подходят для большинства серверов. Для специальных конфигураций посетите <a href="http://php.net/manual/en/install.fpm.php" rel="nofollow noreferrer noopener">сайт PHP FPM</a>.

## Настройка Nginx

Файлы конфигурации Nginx находятся в:

- `/etc/nginx/sites-available/` на Ubuntu (для сайтов, работающих на этом экземпляре Nginx)
- `/etc/nginx/nginx.conf` на Gentoo и Raspbian (Debian, оптимизированный для Raspberry Pi)

Вот пример конфигурационного файла Nginx, *joomla.conf*, который вы можете использовать для всех ваших сайтов с поддержкой Nginx.

```nginx
server {
  listen 80;
  server_name YOUR_DOMAIN;
  server_name_in_redirect off;

  access_log /var/log/nginx/localhost.access_log;
  error_log /var/log/nginx/localhost.error_log info;

  root PATH_ON_SERVER;
  index index.php index.html index.htm default.html default.htm;

  # Поддержка чистых (дружественных к поисковым системам) URL
  location / {
    try_files $uri $uri/ /index.php?$args;
  }

  # добавление глобального заголовка x-content-type-options
  add_header X-Content-Type-Options nosniff;

  # запрет на выполнение скриптов в директориях с разрешением записи
  location ~* /(images|cache|media|logs|tmp)/.*\.(php|pl|py|jsp|asp|sh|cgi)$ {
    return 403;
    error_page 403 /403_error.html;
  }

  location ~ \.php$ {
    fastcgi_pass 127.0.0.1:9000;
    fastcgi_index index.php;
    include fastcgi_params;
    fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    include /etc/nginx/fastcgi.conf;
  }

  # кэширование файлов
  location ~* \.(ico|pdf|flv)$ {
    expires 1y;
  }

  location ~* \.(js|css|png|jpg|jpeg|gif|swf|xml|txt)$ {
    expires 14d;
  }

}
```

Обратите внимание на несколько вещей:

1. Параметр *fastcgi_pass* установлен на *127.0.0.1:9000*, что соответствует порту, который FPM настроен для прослушивания. Это означает, что вы можете запускать процессы PHP на отдельных серверах. На Gentoo вы можете найти эту конфигурацию в файле */etc/php/fpm-php5.3/php-fpm.conf/*.
2. Не забудьте заменить YOUR_DOMAIN и PATH_ON_SERVER на соответствующие значения вашего домена и пути к Joomla на вашем сервере.

## Поддержка GZip

Если вам необходима поддержка сжатия GZip, добавьте следующий раздел в
секцию *http* основного конфигурационного файла Nginx:

```
gzip on;
gzip_http_version 1.1;
gzip_comp_level 6;
gzip_min_length 1100;
gzip_buffers 4 8k;
gzip_types text/plain application/xhtml+xml text/css application/xml application/xml+rss text/javascript application/javascript application/x-javascript;
gzip_proxied any;
gzip_disable "MSIE [1-6]\.";
```

## Источники

- <a href="https://wiki.gentoo.org/wiki/Nginx"
rel="nofollow noreferrer noopener">Nginx в Gentoo</a>
- <a href="https://kevinworthington.com/nginx-for-windows/"
  rel="nofollow noreferrer noopener">Nginx для Windows</a>
- <a
  href="https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview"
  rel="nofollow noreferrer noopener">Nginx в Ubuntu</a>
- <a
  href="https://www.debianadmin.com/howto-install-nginx-webserver-in-debian.html"
  rel="nofollow noreferrer noopener">Nginx в Debian</a>
- <a href="https://www.php.net/manual/en/install.fpm.php"
  rel="nofollow noreferrer noopener">Установка и настройка PHP-FPM</a>
- <a
  href="https://docs.nginx.com/nginx/admin-guide/web-server/compression/"
  rel="nofollow noreferrer noopener">Сжатие и распаковка</a>
- <a href="https://www.nginx.com/blog/creating-nginx-rewrite-rules/"
  rel="nofollow noreferrer noopener">Создание правил перезаписи в NGINX</a>
- <a href="http://nginx.org/en/docs/http/request_processing.html"
  rel="nofollow noreferrer noopener">Как Nginx обрабатывает запрос</a>

*Переведено с помощью openai.com*

