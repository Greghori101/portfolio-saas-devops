FROM php:8.2-fpm

# Install dependencies
RUN apt-get update && apt-get install -y \
    libpq-dev \
    zip unzip curl git \
    && docker-php-ext-install pdo pdo_pgsql

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Set working dir
WORKDIR /var/www

# Copy code
COPY ../../portfolio-saas-back /var/www

# Permissions
RUN chown -R www-data:www-data /var/www \
    && chmod -R 755 /var/www

# Laravel commands
RUN composer install --no-interaction --prefer-dist \
    && cp .env.example .env \
    && php artisan key:generate

EXPOSE 8000
CMD ["php-fpm"]
