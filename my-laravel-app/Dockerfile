# Use an official PHP runtime as a parent image
FROM php:8.0-fpm

# Set the working directory in the container
WORKDIR /var/www/html

# Install system dependencies and PHP extensions
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    libzip-dev \
    && docker-php-ext-install zip

# Install Composer globally
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy the Composer files into the container
COPY composer.json composer.json
COPY composer.lock composer.lock



# Copy the rest of your application code into the container
COPY . .

# Expose port 9000 to interact with PHP-FPM
EXPOSE 9000

# Start PHP-FPM
CMD ["php-fpm"]