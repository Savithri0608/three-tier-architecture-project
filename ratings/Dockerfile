#
# Build the app
#
FROM php:8.3-apache

# Install required packages and PHP extensions
RUN apt-get update && apt-get install -y --no-install-recommends \
    unzip libzip-dev git curl zlib1g-dev libicu-dev libonig-dev libxml2-dev \
    && docker-php-ext-install pdo_mysql opcache zip intl \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Enable Apache modules
RUN a2enmod rewrite status

# Enable AutoProfile for Instana (still opt-in if supported)
RUN echo "instana.enable_auto_profile=1" > "/usr/local/etc/php/conf.d/zzz-instana-extras.ini"

# Configure Apache
COPY status.conf /etc/apache2/mods-available/status.conf

# Set working directory
WORKDIR /var/www/html

# Copy app files
COPY html/ /var/www/html/

# Install Composer (from official Composer image)
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Install Symfony dependencies
RUN composer install --no-interaction --no-dev --optimize-autoloader

# Set appropriate permissions (safer than chmod 777)
RUN chown -R www-data:www-data /var/www \
    && find var -type d -exec chmod 775 {} \; \
    && find var -type f -exec chmod 664 {} \;

# Expose port 80 (already done implicitly by Apache base image)
EXPOSE 80
