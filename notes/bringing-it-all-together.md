
# Bringing It All Together

## Introduction
In this final session, we’ll combine everything learned in this course to build a fully functional Laravel project. The project will include:
1. Routes, controllers, and views.
2. Database interactions using Eloquent ORM.
3. Authentication and middleware for security.
4. Frontend asset management with Laravel Mix.

---

## Project Overview

### **Project Name**: Simple Blog Application

### **Features**:
- User authentication (register, login, and logout).
- A dashboard to manage blog posts.
- CRUD (Create, Read, Update, Delete) operations for blog posts.
- Comments on posts.

---

## Step-by-Step Implementation

### Step 1: Set Up the Project
1. **Create a new Laravel project**:
   ```bash
   laravel new simple-blog
   ```
2. **Install Laravel UI**:
   ```bash
   composer require laravel/ui
   php artisan ui bootstrap --auth
   npm install && npm run dev
   ```
3. **Run migrations**:
   ```bash
   php artisan migrate
   ```

---

### Step 2: Create Models, Migrations, and Controllers
1. **Create the Post model and migration**:
   ```bash
   php artisan make:model Post -m
   ```
2. **Define the posts table schema** in `database/migrations/xxxx_xx_xx_create_posts_table.php`:
   ```php
   Schema::create('posts', function (Blueprint $table) {
       $table->id();
       $table->string('title');
       $table->text('content');
       $table->unsignedBigInteger('user_id');
       $table->timestamps();

       $table->foreign('user_id')->references('id')->on('users')->onDelete('cascade');
   });
   ```
3. **Run the migration**:
   ```bash
   php artisan migrate
   ```

4. **Create the PostController**:
   ```bash
   php artisan make:controller PostController
   ```

---

### Step 3: Set Up Routes
Define routes in `routes/web.php`:
```php
use App\Http\Controllers\PostController;

Route::middleware(['auth'])->group(function () {
    Route::get('/dashboard', [PostController::class, 'index'])->name('dashboard');
    Route::get('/posts/create', [PostController::class, 'create'])->name('posts.create');
    Route::post('/posts', [PostController::class, 'store'])->name('posts.store');
    Route::get('/posts/{post}/edit', [PostController::class, 'edit'])->name('posts.edit');
    Route::put('/posts/{post}', [PostController::class, 'update'])->name('posts.update');
    Route::delete('/posts/{post}', [PostController::class, 'destroy'])->name('posts.destroy');
});
```

---

### Step 4: Build Views
1. **Dashboard View**:
   - Display a list of posts by the logged-in user.

2. **Create and Edit Post Views**:
   - Forms for creating and editing posts using Blade templates.

Example for `create.blade.php`:
```blade
@extends('layouts.app')

@section('content')
<div class="container">
    <h1>Create a New Post</h1>
    <form action="{{ route('posts.store') }}" method="POST">
        @csrf
        <div class="form-group">
            <label for="title">Title</label>
            <input type="text" name="title" class="form-control" required>
        </div>
        <div class="form-group">
            <label for="content">Content</label>
            <textarea name="content" class="form-control" rows="5" required></textarea>
        </div>
        <button type="submit" class="btn btn-primary">Submit</button>
    </form>
</div>
@endsection
```

---

### Step 5: Add Middleware for Authorization
Use middleware to ensure only the post owner can edit or delete a post.

In `PostController`:
```php
public function __construct()
{
    $this->middleware(function ($request, $next) {
        $post = $request->route('post');
        if ($post && $post->user_id !== auth()->id()) {
            return redirect()->route('dashboard')->with('error', 'Unauthorized action.');
        }
        return $next($request);
    })->only(['edit', 'update', 'destroy']);
}
```

---

### Step 6: Add Styling with Laravel Mix
1. Install Bootstrap via NPM:
   ```bash
   npm install bootstrap
   ```
2. Update `resources/sass/app.scss` to include Bootstrap:
   ```scss
   @import '~bootstrap/scss/bootstrap';
   ```
3. Compile assets:
   ```bash
   npm run dev
   ```

---

### Hands-On Task
1. Build the Simple Blog Application following the steps above.
2. Test all features:
   - Register and log in.
   - Create, edit, and delete posts.
   - View the dashboard.
3. Push the final project to GitHub and share the link for review.

---

## Summary
In this session, we brought together all the concepts learned in this course to build a functional Laravel application. You now have a solid foundation to develop modern web applications using Laravel.

Happy coding! 🚀
