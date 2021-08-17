FROM    ubuntu:16.04

RUN        apt-get update\
        #
        # php
        #
        # installing software-properties-common to be able to add-apt-repository
        && apt-get install software-properties-common -y\
        # on repository ppa:ondrej/php support php7.2 for ubuntu16.04 dropped since April 2021
        # that why using another repository
        && add-apt-repository ppa:jason.grammenos.agility/php -y\
        && apt-get update\
        && apt-get install php7.2 php7.2-fpm -y\
        # set php-fpm to listen port 9000
        && echo "listen = 9000" >> /etc/php/7.2/fpm/pool.d/www.conf\
        #
        # imagick
        #
        # downloading non-interactive pear installer
        && apt-get install wget -y\
        && wget https://pear.php.net/install-pear-nozlib.phar\
        # installing additional php extensions to be able to install pear
        && apt-get install php7.2-cli php7.2-xml php7.2-dev -y\
        # installing pear ot be able to run pecl
        && php install-pear-nozlib.phar\
        # installing pkg-config to be able to run pecl
        && apt-get install pkg-config -y\
        # installing libmagickwand-dev to be able to install imagick via pecl
        && apt-get install libmagickwand-dev -y\
        && pecl install -f imagick-3.4.3\
        && echo "extension=imagick.so" >> /etc/php/7.2/fpm/php.ini
