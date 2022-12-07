
Описание как развернуть проект  docker+postgres+php+nginx+redis
-
#### Прежде чем начать, убедитесь, что в вашей системе установлен docker-compose.

**1**. Установите проект в папку project.
```shell script
composer create-project laravel/laravel project
```

**2**. Запустите докер контейнеры 

```shell script
docker compose build && docker compose up -d
```

**3**. Расширение прав доступа на редактирование и добавление файлов
```shell script
sudo chmod 777 -R project/
```

**4**. В контейнер php введите следующие команды:

```shell script
docker exec -it test_php bash
````
```shell script
composer require predis/predis
```

**5**. Подключение redis

* .env
```shell script
CACHE_DRIVER=redis

REDIS_CLIENT=predis
REDIS_HOST=test1_redis:6379
REDIS_PASSWORD=null
REDIS_PORT=6379
```
* app.php
```shell script
'store'  => 'redis'
```
* cache.php
```shell script
'default' => env('CACHE_DRIVER', 'redis')
```
**6**. Подключение postgres

* .env
```shell script
DB_CONNECTION=pgsql
DB_HOST=postgres
DB_PORT=5432
DB_DATABASE=test_postgres
DB_USERNAME=root
DB_PASSWORD=root
```
* database.php

```shell script
'default' => env('DB_CONNECTION', 'pgsql'),
```

**6**. Проект доступен по адресу

```shell script
http://myhost.loc/
```
* pgAdmin
```shell script
http://localhost:5050
```