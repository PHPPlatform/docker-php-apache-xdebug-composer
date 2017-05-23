FROM phpplatform/php-apache:5.4

RUN mkdir -p /tmp/xdebug && cd /tmp/xdebug \
    && curl -O https://xdebug.org/files/xdebug-2.4.1.tgz && tar -xzf xdebug-2.4.1.tgz && cd xdebug-2.4.1 \
    && phpize \
    && ./configure --enable-xdebug \
    && make && make install \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

