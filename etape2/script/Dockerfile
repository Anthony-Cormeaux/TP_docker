FROM php:7.4-fpm

RUN docker-php-ext-install pdo pdo_mysql

COPY src/ /app

WORKDIR /app

EXPOSE 9000

CMD ["php-fpm"]