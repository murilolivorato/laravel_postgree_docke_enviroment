
# Setting Up a Laravel Development Environment with Docker and Docker Compose
## Instructions -
https://medium.com/@murilolivorato/setting-up-a-laravel-development-environment-with-docker-and-docker-compose-a-step-by-step-5e37670ae640

## Run those commands
- docker-compose up -d --build
- docker-compose run --rm composer install
- docker-compose run --rm artisan key:generate

## MIGRATE
- docker-compose run --rm artisan db:wipe
- docker-compose run --rm artisan migrate --path=/database/migrations/db00_general --path=/database/migrations/db01_location --path=/database/migrations/db02_user --path=/database/migrations/db03_property --path=/database/migrations/db04_new_property --path=/database/migrations/db05_customer_property_interactivity --path=/database/migrations/db06_post

## MIGRATE ONE CLASS
- docker-compose run --rm artisan migrate --path=/database/migrations/db03_property/2024_08_19_191446_create_prop_prop_draft_step_table.php
- docker-compose run --rm artisan migrate --path=/database/migrations/db03_property/2024_08_19_191722_create_prop_prop_draft_copy_table.php

# KERNEL
now it is on app .php

## DB SEED
- docker-compose run  --rm  artisan db:seed --class ResetDataSeeder
- docker-compose run  --rm  artisan db:seed --class GeneralSeeder

- docker-compose run  --rm  artisan db:seed --class LocationDataSeeder
 
- docker-compose run  --rm  artisan db:seed --class UsersDataSeeder

- docker-compose run  --rm  artisan db:seed --class PropsDataDependenciesSeeder
- docker-compose run  --rm  artisan db:seed --class PropsDataSeeder

- docker-compose run  --rm  artisan db:seed --class PropNewDataDependenciesSeeder
- docker-compose run  --rm  artisan db:seed --class PropNewDataSeeder

- docker-compose run  --rm  artisan db:seed --class PostsDataDependenciesDataSeeder
- docker-compose run  --rm  artisan db:seed --class PostsDataSeeder

- docker-compose run  --rm  artisan db:seed --class LocationSyncDataSeeder
- docker-compose run  --rm  artisan db:seed --class CustomerInteractionDataSeeder

## INSTALAÇÃO PASSPORT CLIENT
- docker-compose run --rm  artisan passport:client --personal

### PERGUNTAS PARA A INSTALAÇÃO
What should we name the personal access client? [Laravel Personal Access Client]:
> Auth

## INSTALAÇÃO PASSPORT CLIENT -- PASSWORD PARA USER PUB
docker-compose run --rm  artisan passport:client --password --name=UserPub --provider=user_pubs


## INSTALAÇÃO PASSPORT CLIENT -- PASSWORD PARA USER PUB
docker-compose run --rm  artisan passport:client --password --name=UserCustomer --provider=user_customers

## INSTALAÇÃO PASSPORT CLIENT -- PASSWORD USER USER ADMIN
docker-compose run --rm  artisan passport:client --password --name=UserAdmin --provider=user_admins

##  LIMPE O CACHE
- docker-compose run --rm  artisan config:clear

## GERE AS KEYS
docker-compose run --rm  artisan passport:keys

##  TEST
- docker-compose run --rm  artisan config:clear
- docker-compose run --rm  pest



# DEPENDECIES INSTALLED

## PRE-REDIS
- docker-compose run  --rm  composer require predis/predis

##  PASSPORT
- docker-compose run  --rm  composer require laravel/passport
- docker-compose run  --rm  artisan passport:install --uuids
- docker-compose run  --rm artisan passport:client --password
- docker-compose run  --rm artisan passport:keys
- docker-compose run  --rm artisan vendor:publish --tag=passport-config

docker-compose run  --rm  composer require passport-api
## IMAGE INTERVENTION
- docker-compose run  --rm   require intervention/image

## HASH ID
- docker-compose run  --rm   require vinkla/hashids
- docker-compose run  --rm  artisan vendor:publish

## API
- docker-compose run  --rm  artisan install:api --passport

## PROVIDER
- docker-compose run  --rm  artisan make:provider AuthServiceProvider
- docker-compose run  --rm  artisan make:provider RouteServiceProvider

## VIEW
- docker-compose run  --rm  artisan install:api- docker-compose run  --rm  artisan install:api
- docker-compose run  --rm  artisan config:publish
> view

## MAKE MIDDLEWARE
- docker-compose run  --rm  artisan make:middleware MustBeAdminstrator
- docker-compose run  --rm  artisan make:middleware RedirectIfAuthenticated
- docker-compose run  --rm  artisan make:middleware Authenticate
- 
## MAKE EXEPTION
- docker-compose run  --rm artisan make:exception HandlerException

## VIEW
- docker-compose run  --rm  composer require laravel/breeze
- docker-compose run  --rm  artisan breeze:install
##  PEST PHP
- docker-compose run  --rm  composer remove phpunit/phpunit
- docker-compose run  --rm  composer require pestphp/pest --dev --with-all-dependencies
- composer require pestphp/pest-plugin-laravel --dev
- INICIALIZE O PEST, ENTRE NO CONTAINER PHP E DE O COMANDO
-  ./vendor/bin/pest --init


