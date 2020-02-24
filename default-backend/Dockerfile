FROM php:7.0-apache
COPY ./index.html /var/www/html/
COPY ./beautiful.jpeg /var/www/html/
RUN a2enmod rewrite
EXPOSE 80
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
