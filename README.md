# Ambiente de desenvolvimento PHP, Laravel, MySQL e Nginx.

## Requisitos

### Para rodar o projeto é necessário ter instalado:

Docker e Docker Compose para rodar o ambiente de desenvolvimento.

Git para clonar o repositório do projeto.

## Instalação do ambiente de desenvolvimento

Clone o repositório do projeto:

```bash
git clone git@github.com:PauloMedinabr01/app-laravel-docker.git
```

Aqui você encontrara um projeto Laravel com Starter Kit Blade, MySQL e Nginx, um Dockerfile para o ambiente de desenvolvimento,
um docker-compose.yml para subir o ambiente de desenvolvimento e um arquivo nginx.conf para configurar o servidor Nginx.
Configure o arquivo .env com seus dados de conexão com o banco de dados.

Entre na pasta do projeto:

```bash
cd app
```

Criar o container da aplicação. Também pode ser usado para reconstruir o container.

```bash
docker compose up -d --build
```

Os containers criados são:

- application: container com o Laravel e Starter Kit Blade/Alpine.
- mysql: container com o MySQL.
- nginx: container com o Nginx.

Para parar o ambiente de desenvolvimento, execute o comando:

```bash
docker compose down
```

Para acessar o container application, execute o comando:

```bash
docker exec -it application bash
```

Rode as migrações e as seeds:

```bash
php artisan migrate
php artisan db:seed
```

Para acessar o container mysql, execute o comando:

```bash
docker exec -it mysql bash
```

Acesse a aplicação em http://localhost:8084
