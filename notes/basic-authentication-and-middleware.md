
# Basic Authentication and Middleware

## Introduction
Authentication is a fundamental part of web application security, and Laravel provides built-in tools to handle it efficiently. Middleware acts as a filter for HTTP requests, allowing you to enforce rules like authentication, logging, and more.

---

## Authentication in Laravel

### 1. **Using Laravel Breeze**
Laravel Breeze provides a minimal and simple implementation of authentication.

#### Steps to Set Up Laravel Breeze:
1. Install Laravel Breeze via Composer:
   ```bash
   composer require laravel/breeze --dev
   ```
2. Install the Breeze scaffolding:
   ```bash
   php artisan breeze:install
   ```
3. Run migrations to set up the required authentication tables:
   ```bash
   php artisan migrate
   ```
4. Install and compile front-end assets (if using Blade views):
   ```bash
   npm install && npm run dev
   ```
5. Visit `/login` or `/register` to see the authentication pages.

---

### 2. **Manually Implementing Authentication**
If you want more control over authentication, you can implement it manually:

#### a) **Login Functionality**:
1. Create a route in `routes/web.php`:
   ```php
   Route::post('/login', [AuthController::class, 'login']);
   ```
2. Create an `AuthController`:
   ```bash
   php artisan make:controller AuthController
   ```
3. Add login logic:
   ```php
   public function login(Request $request)
   {
       $credentials = $request->only('email', 'password');

       if (Auth::attempt($credentials)) {
           return redirect()->intended('dashboard');
       }

       return back()->withErrors(['email' => 'Invalid credentials']);
   }
   ```

#### b) **Logout Functionality**:
1. Add a logout route:
   ```php
   Route::post('/logout', [AuthController::class, 'logout']);
   ```
2. Implement the `logout` method:
   ```php
   public function logout()
   {
       Auth::logout();
       return redirect('/login');
   }
   ```

---

## Middleware in Laravel

### 1. **What is Middleware?**
Middleware filters HTTP requests entering your application. For example:
- Authentication: Ensure only logged-in users access certain routes.
- Logging: Record each request.

### 2. **Built-in Middleware**
Laravel includes several middleware:
- `auth`: Ensures the user is authenticated.
- `guest`: Redirects authenticated users to a specific page.
- `throttle`: Limits the number of requests per minute.

### 3. **Creating Custom Middleware**
1. Generate middleware using Artisan:
   ```bash
   php artisan make:middleware CheckRole
   ```
2. Define logic in the middleware:
   ```php
   public function handle($request, Closure $next)
   {
       if ($request->user()->role !== 'admin') {
           return redirect('home');
       }

       return $next($request);
   }
   ```
3. Register middleware in `app/Http/Kernel.php`:
   ```php
   protected $routeMiddleware = [
       'checkRole' => \App\Http\Middleware\CheckRole::class,
   ];
   ```
4. Apply middleware to routes:
   ```php
   Route::get('/admin', [AdminController::class, 'index'])->middleware('checkRole');
   ```

---

## Hands-On Task
1. Install and set up Laravel Breeze.
2. Create custom middleware to restrict access to an "Admin Dashboard".
3. Implement login and logout functionality using `Auth` methods.
4. Apply the `auth` middleware to protect routes like `/dashboard`.

---

## Summary
In this session, we learned how to implement authentication using Laravel Breeze and manually. We also explored how to use middleware to filter requests and secure routes, ensuring a robust application security layer.

---
