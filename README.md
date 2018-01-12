# Docker Images for PHP Development

This repo contains DockerFiles to build docker images containing software components (PHP + Apache + Composer + XDebug) 

The Images are built in this order

    - docker-library/php is forked into PHPPlatform/docker-php-apache in github
    - created new branches to support older version of php in PHPPlatform/docker-php-apache
    - phpplatform/php-apache docker images are automatically built in docker hub , linked to PHPPlatform/docker-php-apache github repo
    - This repo uses images from phpplatform/php-apache to add Composer and Xdebug
    - docker images are built automatically at phpplatform/php-apache-composer-xdebug in Docker HUb

