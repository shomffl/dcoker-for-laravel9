## Laravel9 プロジェクトの作成コマンド

```
docker-compose run php composer create-project --prefer-dist laravel/laravel . "9.*"

docker-compose up -d
```

## Inertia.js React を使用する場合

```
composer install laravel/breeze --dev

php artisan breeze:install react
```
