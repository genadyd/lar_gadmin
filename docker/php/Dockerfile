FROM php:8.0.5-fpm-alpine
USER root

## Arguments defined in docker-compose1.yml
#ARG user
#ARG uid

#Set working directory
WORKDIR /var/www
#install system depedencies

RUN apt-get update && apt-get install -y wget \
    git \
    zip \
    curl \
    unzip \
    exif

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

#RUN apt-get update
#RUN apt-get install -y zip exif
#RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include --with-webp-dir=/usr/include --with-jpeg-dir=/usr/include
#Get latest composer
#RUN wget -O composer-setup.php https://getcomposer.org/installer
#RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer




# copy existing application directory content
COPY ../../src /var/www
#COPY --from=composer:latest /usr/bin/composer /usr/bin/composer
## Create system user to run Composer and Artisan Commands
#RUN useradd -G www-data,$user -u $uid -d /home/$user $user
#RUN mkdir -p /home/$user/.composer && \
#    chown -R $user:$user /home/$user


USER www-data

EXPOSE 9000

CMD["php-fpm"]
