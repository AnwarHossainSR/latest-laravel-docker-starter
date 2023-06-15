# Setup Docker Laravel (8,9,10)

### Step by step

Clone Repository

```sh
git clone https://github.com/especializati/setup-docker-laravel.git
```

Clone the Laravel Files

```sh
git clone https://github.com/laravel/laravel.git your-project-name
```

Copy the docker-compose.yml, Dockerfile and docker/ directory to your project

```sh
cp -rf laravel-docker-starter/* your-project-name/
```

```sh
rm -rf laravel-docker-starter
```

```sh
cd your-project-name/
```

```sh
rm -rf .git
```

Create the .env File

```sh
cp .env.example .env
```

Update .env file environment variables

```dosini
APP_NAME="Especializa Ti"
APP_URL=http://localhost:8989

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=root

CACHE_DRIVER=redis
QUEUE_CONNECTION=redis
SESSION_DRIVER=redis

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379
```

Upload the project containers

```sh
docker-compose up -d
```

Access the container

```sh
docker-compose exec app bash
```

Install project dependencies

```sh
composer install
```

Generate Laravel project key

```sh
php artisan key:generate
```

Access the project
[http://localhost:8989](http://localhost:8989)
