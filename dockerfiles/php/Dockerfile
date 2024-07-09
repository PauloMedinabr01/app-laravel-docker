# Usa a imagem base do PHP 8.3 FPM Alpine 3.20
FROM php:8.3-fpm-alpine3.20

# Define o diretório de trabalho
WORKDIR /var/www

# Instala dependências do sistema e extensões PHP em uma única camada
RUN apk add --no-cache \
    bash \
    curl \
    libpng-dev \
    libzip-dev \
    zlib-dev \
    && docker-php-ext-install gd zip pdo pdo_mysql

# Instala o Composer mais recente
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Instala o Node.js e o NPM mais recentes
RUN apk add --no-cache nodejs npm

# Copia os arquivos da aplicação para o diretório de trabalho
COPY . /var/www

# Define as permissões para o diretório 'storage' e 'bootstrap/cache'
RUN chown -R www-data:www-data /var/www/storage \
    && chown -R www-data:www-data /var/www/bootstrap/cache \
    && chmod -R 775 /var/www/storage \
    && chmod -R 775 /var/www/bootstrap/cache

# Expõe a porta do PHP-FPM para o host
EXPOSE 9000

# Comando padrão para iniciar o PHP-FPM
CMD ["php-fpm"]
