FROM ubuntu:21.04

RUN apt-get update -y && \
    apt-get install tzdata -y && \
    apt-get install apache2 -y && \
    apt-get install nano -y 

COPY ./laravel_app.conf /etc/apache2/sites-available/laravel_app.conf

RUN sed 's/localhost/laravel.dev/1' /etc/hosts

RUN apt-get install -y software-properties-common \
    && add-apt-repository ppa:ondrej/php \
    && add-apt-repository ppa:ondrej/apache2 \
    && apt-get update -y \ 
    && apt-get install -y \
    php8.0 \
    libapache2-mod-php8.0  \
    php8.0-common \
    php8.0-bcmath \
    php-json \
    php8.0-mbstring \
    openssl \
    php8.0-tokenizer \
    php8.0-xml \
    php8.0-zip \
    php8.0-soap \
    php8.0-mysql \
    php-curl \
    php8.0-curl && \
    # git and composer 
    apt-get install -y \
    git \
    composer

RUN a2ensite laravel_app.conf && \
    a2dissite 000-default.conf

RUN a2enmod rewrite

WORKDIR /var/www/laravel_app


# RUN git clone https://github.com/anwarendo/backend.git .

# COPY .env /var/www/laravel_app/.env

# RUN composer install && \
#     php artisan key:generate && \
#     chmod -R 777 /var/www/laravel_app && 
     



ENTRYPOINT [ "apachectl", "-D", "FOREGROUND"]