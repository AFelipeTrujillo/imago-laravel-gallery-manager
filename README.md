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

# Models and migrate files

## Categories
```
php artisan make:model Category -m
```
__2022_02_28_232821_create_categories_table__
```
Schema::create('categories', function (Blueprint $table) {
    $table->id();
    $table->string('title', 45);
    $table->timestamps();
});
```