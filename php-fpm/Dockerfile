FROM arm32v7/php:8.0-fpm-alpine

COPY wait-for-it.sh /usr/bin/wait-for-it.sh

RUN chmod u+x /usr/bin/wait-for-it.sh

RUN apk --update --no-cache add git

RUN docker-php-ext-install pdo_mysql

COPY --from=composer /usr/bin/composer /usr/bin/composer

WORKDIR /var/www

CMD composer install ; ./usr/bin/wait-for-it.sh database:3306 -- bin/console doctrine:migrations:migrate ;  php-fpm ; php -v

EXPOSE 9000
