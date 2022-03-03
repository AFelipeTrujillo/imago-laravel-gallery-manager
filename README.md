# imago-laravel-gallery-manager
Imago (image in Latin) is a small image manager and create your own gallery with Laravel.

# Bussines Rules (User Stories)
## Version 1
* The user must be able to create an account with their email and password
* The application must manage three roles, administrator user and editor
* Editor users can upload images from PC or URL
* Editor users can add a category to the image and multiple tags
* In the application there must be a public gallery with all the images of the users
* In the application there must be a view with the images by category and tags


# Imago Entity Relationship Model
![Imago ER Model](https://raw.githubusercontent.com/AFelipeTrujillo/imago-laravel-gallery-manager/main/Imago.entity%E2%80%93relationship-model.png)

# Physical Data Model

![Imago EER Model Mysql Workbech](https://github.com/AFelipeTrujillo/imago-laravel-gallery-manager/blob/main/Imago.entity%E2%80%93relationship-model-workbench.png?raw=true)

# Stack

* PHP
* Laravel
* Taildwild CSS: is basically a utility-first CSS framework for rapidly building custom user interfaces
* Jetstream: is a beautifully designed application starter kit for Laravel and provides the perfect starting point for your next Laravel applicatio
* Liveware: is a full-stack framework for Laravel that makes building dynamic interfaces simple, without leaving the comfort of Laravel

## Installation 
```
laravel new imago
composer require laravel/ui
php artisan ui bootstrap --auth
npm install && npm run dev 
```

# Models and migrate files

## Categories
```
php artisan make:model Category -m
```
📋 __2022_02_28_232821_create_categories_table__
```
Schema::create('categories', function (Blueprint $table) {
    $table->id();
    $table->string('name', 45);
    $table->timestamps();
});
```

## Tags
Create model, controller, seeder and factory
```
php artisan make:model Tag -mcsf
```
📋 __2022_02_28_234102_create_tags_table__
```
Schema::create('tags', function (Blueprint $table) {
    $table->id();
    $table->string('name', 45);
    $table->timestamps();
});
```

## Roles
Create model, controller, seeder and factory
```
php artisan make:model Role -mcsf
```
📋 __2022_03_01_013234_create_roles_table__
```
Schema::create('roles', function (Blueprint $table) {
    $table->id();
    $table->string('name', 45);
    $table->timestamps();
});
```

## Images
Create model, controller, seeder and factory
```
php artisan make:model Image -mcsf
```
```
Schema::create('images', function (Blueprint $table) {
    $table->id();
    $table->string('title',45);
    $table->string('url',255);
    $table->unsignedBigInteger('user_id')->nullable();
    $table->unsignedBigInteger('category_id')->nullable();
    # One - to - Many
    $table->foreign('user_id')->references('id')->on('users')->onDelete('set null');
    # One - to - Many
    $table->foreign('category_id')->references('id')->on('categories')->onDelete('set null');
    $table->timestamps();
});
```