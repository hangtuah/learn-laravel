
# Routes, Controllers, and Views

## Introduction
Laravel follows the **Model-View-Controller (MVC)** architecture, where:
- **Routes** define the application’s URL structure and map HTTP requests to controllers.
- **Controllers** handle the application logic and process user requests.
- **Views** are used to generate HTML responses.

---

## Routes in Laravel
Routes are defined in the `routes/web.php` file for web-based requests.

### Key Concepts:
1. **Basic Route**:
   A simple route that returns a string:
   ```php
   Route::get('/hello', function () {
       return 'Hello, World!';
   });
   ```

2. **Route Parameters**:
   Capture dynamic values from the URL:
   ```php
   Route::get('/user/{id}', function ($id) {
       return "User ID: $id";
   });
   ```

3. **Named Routes**:
   Assign names to routes for easy referencing:
   ```php
   Route::get('/profile', function () {
       return 'User Profile';
   })->name('profile');
   ```

4. **Route Groups**:
   Group routes with shared attributes like middleware:
   ```php
   Route::middleware(['auth'])->group(function () {
       Route::get('/dashboard', function () {
           return 'Dashboard';
       });
   });
   ```

---

## Controllers in Laravel
Controllers handle requests and return responses. They are created in the `app/Http/Controllers` directory.

### Key Concepts:
1. **Creating a Controller**:
   Use the Artisan command to create a controller:
   ```bash
   php artisan make:controller UserController
   ```

2. **Defining Controller Methods**:
   Add methods to handle logic for specific routes:
   ```php
   namespace App\Http\Controllers;

   use Illuminate\Http\Request;

   class UserController extends Controller
   {
       public function show($id)
       {
           return "User ID: $id";
       }
   }
   ```

3. **Connecting Routes to Controllers**:
   Map routes to controller methods:
   ```php
   Route::get('/user/{id}', [UserController::class, 'show']);
   ```

---

## Views in Laravel
Views are stored in the `resources/views` directory and are used to generate the user interface.

### Key Concepts:
1. **Creating a View**:
   Create a Blade template file (e.g., `welcome.blade.php`):
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>Laravel App</title>
   </head>
   <body>
       <h1>Welcome to Laravel!</h1>
   </body>
   </html>
   ```

2. **Returning a View**:
   Return a view from a route or controller:
   ```php
   Route::get('/welcome', function () {
       return view('welcome');
   });
   ```

3. **Passing Data to Views**:
   Pass variables to views using the `view()` function:
   ```php
   Route::get('/user/{name}', function ($name) {
       return view('user', ['name' => $name]);
   });
   ```

4. **Blade Syntax**:
   Use Blade directives for dynamic content:
   ```blade
   <h1>Hello, {{ $name }}!</h1>
   @if($name == 'Admin')
       <p>Welcome, Admin!</p>
   @endif
   ```

---

## Hands-On Task
1. Define a route in `web.php` that displays a "Hello, Laravel!" message.
2. Create a `UserController` with a method that returns "User Profile".
3. Connect a route to the `UserController` method.
4. Create a `welcome.blade.php` file to display a welcome message.
5. Pass a variable (e.g., user name) to a Blade view and display it dynamically.

---

## Summary
In this session, we explored how Laravel handles routes, controllers, and views. These components work together to structure the application and respond to user requests effectively.

---
