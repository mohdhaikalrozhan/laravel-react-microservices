# Use the PHP 8.4 base image
FROM php:8.4

# Update package manager and install required dependencies
RUN apt-get update -y && apt-get install -y \
    libzip-dev \
    libonig-dev \
    libpq-dev \
    libxml2-dev \
    zip \
    unzip \
    git

# Install PHP extensions
RUN docker-php-ext-install pdo mbstring pdo_mysql

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Set the working directory
WORKDIR /var/www

# Copy the application files to the container
COPY . .

# Install PHP dependencies
RUN composer install

# Expose the port and start the application
CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port=8000"]
EXPOSE 8000
