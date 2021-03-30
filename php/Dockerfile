FROM php:7.4-fpm

EXPOSE 9000
#EXPOSE 9003

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN cd /usr/local/etc/php \ 
    && cp php.ini-development php.ini \
    && touch /var/log/debug.log \
    && chmod 777  /var/log/debug.log \
##    && ln -sf /dev/stderr /var/log/debug.log \
##    && echo "zend_extension=/usr/local/lib/php/extensions/no-debug-non-zts-20190902/xdebug.so" >>php.ini \
    && echo "[xdebug]" >>php.ini  \
    && echo "xdebug.mode = debug" >>php.ini \
    && echo "xdebug.client_host = host.docker.internal" >>php.ini \
    && echo "xdebug.client_port = 9003" >>php.ini \
    && echo "xdebug.show_local_vars = 1" >>php.ini \
    && echo "xdebug.idekey = VSCODE" >>php.ini \
    && echo "xdebug.connect_timeout_ms = 1000" >>php.ini \
    && echo "xdebug.log=/var/log/debug.log" >>php.ini \
    && echo "xdebug.log_level = 10" >>php.ini \
    && echo "xdebug.start_with_request = yes" >>php.ini
    ##&& echo "xdebug.discover_client_host = 1" ## scan same subnet for IDE
    ## echo "xdebug.remote_enable = 1" replaced by xdebug.mode=debug
    ## echo "xdebug.remote_connect_back= 1" replaced by xdebug.discover_client_host
