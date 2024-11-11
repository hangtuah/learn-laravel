
# Bringing It All Together

## Introduction
In this final session, we will combine all the concepts learned throughout the course to build a simple Laravel project. The project will include routes, controllers, views, database interactions, authentication, and version control.

---

## Project Overview
### **Project Name**: Simple Blog Application
A basic blog application where users can:
1. Register and log in.
2. Create, read, update, and delete blog posts.
3. View a list of posts on the home page.

---

## Step-by-Step Guide

### 1. **Set Up the Laravel Project**
1. Create a new Laravel project:
   ```bash
   laravel new simple-blog
   ```
2. Initialize a Git repository:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```

---

### 2. **Set Up Authentication**
1. Install and set up Laravel Breeze:
   ```bash
   composer require laravel/breeze --dev
   php artisan breeze:install
   php artisan migrate
   npm install && npm run dev
   ```
2. Test authentication by visiting `/login` and `/register`.

---

### 3. **Create the Posts Table**
1. Create a migration for the `posts` table:
   ```bash
   php artisan make:migration create_posts_table
   ```
2. Define the schema in the migration file:
   ```php
   Schema::create('posts', function (Blueprint $table) {
       $table->id();
       $table->string('title');
       $table->text('content');
       $table->timestamps();
   });
   ```
3. Run the migration:
   ```bash
   php artisan migrate
   ```

---

### 4. **Set Up the Post Model**
1. Create the `Post` model:
   ```bash
   php artisan make:model Post
   ```
2. Define the `$fillable` property in the model:
   ```php
   protected $fillable = ['title', 'content'];
   ```

---

### 5. **Create Controllers**
1. Create a `PostController`:
   ```bash
   php artisan make:controller PostController
   ```
2. Define the following methods in the controller:
   - `index`: Display all posts.
   - `create`: Show the form to create a new post.
   - `store`: Save a new post to the database.
   - `edit`: Show the form to edit a post.
   - `update`: Update an existing post.
   - `destroy`: Delete a post.

---

### 6. **Define Routes**
1. Add routes in `routes/web.php`:
   ```php
   use App\Http\Controllers\PostController;

   Route::middleware(['auth'])->group(function () {
       Route::get('/posts', [PostController::class, 'index'])->name('posts.index');
       Route::get('/posts/create', [PostController::class, 'create'])->name('posts.create');
       Route::post('/posts', [PostController::class, 'store'])->name('posts.store');
       Route::get('/posts/{post}/edit', [PostController::class, 'edit'])->name('posts.edit');
       Route::put('/posts/{post}', [PostController::class, 'update'])->name('posts.update');
       Route::delete('/posts/{post}', [PostController::class, 'destroy'])->name('posts.destroy');
   });
   ```

---

### 7. **Build Views**
1. Create Blade templates for:
   - `index.blade.php`: Display a list of posts.
   - `create.blade.php`: Form to create a new post.
   - `edit.blade.php`: Form to edit a post.

2. Use Blade directives to display data and handle forms:
   ```blade
   @foreach($posts as $post)
       <h2>{{ $post->title }}</h2>
       <p>{{ $post->content }}</p>
   @endforeach
   ```

---

### 8. **Test the Application**
1. Register a user and log in.
2. Create, edit, and delete posts using the application.
3. Ensure routes, forms, and views work as expected.

---

### 9. **Version Control**
1. Add changes to Git:
   ```bash
   git add .
   git commit -m "Implemented blog functionality"
   ```
2. Push the project to a GitHub repository:
   ```bash
   git remote add origin https://github.com/username/simple-blog.git
   git push -u origin main
   ```

---

## Hands-On Task
1. Build the complete blog application step by step.
2. Push the final project to a GitHub repository.
3. Share the repository link with the instructor for review.

---

## Summary
This session demonstrated how to apply all the concepts learned throughout the course to build a functional Laravel project. By combining routes, controllers, views, Eloquent ORM, authentication, and Git, you now have the skills to develop modern web applications.

---
