# Setup Docker Laravel (10,11, 12)

### Step by step

Clone Repository

```sh
git clone https://github.com/especializati/latest-laravel-docker-starter.git
```

Clone the Laravel Files

```sh
git clone https://github.com/laravel/laravel.git your-project-name
```

Copy the docker-compose.yml, Dockerfile and docker/ directory to your project

```sh
cp -rf latest-laravel-docker-starter/* your-project-name/
```

```sh
rm -rf latest-laravel-docker-starter
```

```sh
cd your-project-name/
```

```sh
rm -rf .git .github
```

Create the .env File

```sh
cp .env.example .env
```

Update .env file environment variables with this one

```dosini
APP_NAME="Your Project Name"
APP_URL=http://localhost:8989
APP_ENV=local
APP_KEY=
APP_DEBUG=true

LOG_CHANNEL=stack
LOG_DEPRECATIONS_CHANNEL=null
LOG_LEVEL=debug

DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=root

BROADCAST_DRIVER=log
CACHE_DRIVER=redis
FILESYSTEM_DISK=local
QUEUE_CONNECTION=redis
SESSION_DRIVER=redis
SESSION_LIFETIME=120

MEMCACHED_HOST=127.0.0.1

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379

MAIL_MAILER=smtp
MAIL_HOST=mailpit
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS="hello@example.com"
MAIL_FROM_NAME="${APP_NAME}"

AWS_ACCESS_KEY_ID=
AWS_SECRET_ACCESS_KEY=
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=
AWS_USE_PATH_STYLE_ENDPOINT=false

PUSHER_APP_ID=
PUSHER_APP_KEY=
PUSHER_APP_SECRET=
PUSHER_HOST=
PUSHER_PORT=443
PUSHER_SCHEME=https
PUSHER_APP_CLUSTER=mt1

VITE_PUSHER_APP_KEY="${PUSHER_APP_KEY}"
VITE_PUSHER_HOST="${PUSHER_HOST}"
VITE_PUSHER_PORT="${PUSHER_PORT}"
VITE_PUSHER_SCHEME="${PUSHER_SCHEME}"
VITE_PUSHER_APP_CLUSTER="${PUSHER_APP_CLUSTER}"
```

Upload the project containers

```sh
sudo docker-compose up -d
```

Access the container

```sh
sudo docker-compose exec app bash
```

Install project dependencies

```sh
composer install
```

Generate Laravel project key

```sh
php artisan key:generate
```

DB migrate and seed

```sh
php artisan migrate:fresh --seed
```

Access the project
[http://localhost:8989](http://localhost:8989)

# if you face any problem related to phpmyadmin access, please follow bellow command

# php myadmin access issue

```sh
sudo docker-compose exec db mysql -u root -p
```

Then hit Enter when ask for password

Create new user

```sh
CREATE USER 'admin'@'%' IDENTIFIED BY 'admin';
```

Give permission

```sh
GRANT ALL PRIVILEGES ON *.* TO 'admin'@'%';
```

Flush Priviledge

```sh
FLUSH PRIVILEGES;
```

# If getting error regarding network / ip related issue

Allow Connections from All IPs:

```sh
sudo docker-compose exec db mysql -u root -p
```

Then hit Enter when ask for password

```sh
GRANT ALL PRIVILEGES ON database_name.* TO 'admin'@'%' IDENTIFIED BY 'admin';
```

OR

Specify Docker Container IP Range:

```sh
GRANT ALL PRIVILEGES ON database_name.* TO 'user1'@'172.17.%' IDENTIFIED BY 'password';
```
