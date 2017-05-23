FROM phpplatform/php-apache:5.3

RUN mkdir -p /tmp/xdebug && cd /tmp/xdebug \
    && curl -O https://xdebug.org/files/xdebug-2.2.5.tgz && tar -xzf xdebug-2.2.5.tgz && cd xdebug-2.2.5 \
    && phpize \
    && ./configure --enable-xdebug \
    && make && make install \
    && mkdir -p /usr/local/etc/php/conf.d/ \
    && echo "export PHP_INI_SCAN_DIR=/usr/local/etc/php/conf.d" >> ~/.bashrc \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

RUN apt-get install wget -yqq && wget https://composer.github.io/installer.sig -O - -q | tr -d '\n' > installer.sig \
    && php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php -r "if (hash_file('SHA384', 'composer-setup.php') === file_get_contents('installer.sig')) { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
    && php composer-setup.php \
    && php -r "unlink('composer-setup.php'); unlink('installer.sig');" \


CMD ["apache2", "-DFOREGROUND"]

