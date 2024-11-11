
# Basic Authentication and Middleware

## Introduction
Authentication is a core feature of web applications, allowing users to log in, register, and access protected content. Laravel provides a simple, built-in way to implement authentication using `auth` scaffolding.

In this section, we’ll set up authentication with Laravel’s `auth` Bootstrap scaffolding and address compatibility issues with Vite.js in Laravel 9+.

---

## Setting Up Authentication with Auth Scaffolding (Bootstrap)

### Step 1: Install Laravel UI
1. Install the Laravel UI package using Composer:
   ```bash
   composer require laravel/ui
   ```

2. Generate the authentication scaffolding with Bootstrap:
   ```bash
   php artisan ui bootstrap --auth
   ```

3. Install dependencies and compile assets:
   ```bash
   npm install
   npm run dev
   ```

---

### Step 2: Run Migrations
Run the database migrations to create the necessary tables for authentication:
```bash
php artisan migrate
```

This will create tables like `users` in your database.

---

### Step 3: Resolve Vite.js Compatibility Issues in Laravel 9+
If you're using Laravel 9 or later, you may encounter compatibility issues with Vite.js when using Laravel UI. Follow these steps to resolve the issue:

#### 1. Install Laravel Mix
Replace Vite with Webpack Mix, which works seamlessly with Laravel UI:
```bash
npm install laravel-mix --save-dev
npm install sass sass-loader --save-dev
```

Create a `webpack.mix.js` file in the root directory:
```javascript
const mix = require('laravel-mix');

mix.js('resources/js/app.js', 'public/js')
   .sass('resources/sass/app.scss', 'public/css');
```

#### 2. Remove Vite Configuration
1. Delete the `vite.config.js` file.
2. Update the `package.json` scripts section:
   ```json
   "scripts": {
       "dev": "npm run development",
       "build": "npm run production",
       "development": "mix",
       "production": "mix --production"
   }
   ```
3. Remove Vite dependencies:
   ```bash
   npm uninstall vite laravel-vite-plugin
   ```

#### 3. Compile Assets
Compile assets using Laravel Mix:
```bash
npm run dev
```

---

### Step 4: Test Authentication
1. Start the Laravel development server:
   ```bash
   php artisan serve
   ```
2. Visit the following URLs in your browser:
   - **Register**: `/register`
   - **Login**: `/login`
   - **Logout**: `/logout`

You now have a fully functional authentication system with Bootstrap styling.

---

## Other Authentication Options in Laravel

1. **Laravel Breeze**:
   - Minimal and simple scaffolding for authentication.
   - Uses Tailwind CSS for styling.
   - Ideal for quick setups.

   Installation:
   ```bash
   composer require laravel/breeze --dev
   php artisan breeze:install
   npm install && npm run dev
   ```

2. **Laravel Jetstream**:
   - Advanced authentication system with additional features like two-factor authentication, API tokens, and team management.
   - Uses Tailwind CSS.

   Installation:
   ```bash
   composer require laravel/jetstream
   php artisan jetstream:install livewire
   npm install && npm run dev
   ```

3. **Fortify**:
   - Provides authentication backend logic without UI.
   - Ideal for custom authentication systems where you build your own frontend.

4. **Passport**:
   - Designed for API authentication using OAuth2.
   - Ideal for building APIs that require secure token-based authentication.

5. **Sanctum**:
   - Lightweight API authentication for SPAs, mobile apps, and simple token-based APIs.

---

## Middleware in Laravel
Middleware filters HTTP requests entering your application. For example:
- Authentication: Ensure only logged-in users access certain routes.
- Logging: Record each request for debugging purposes.

---

### Creating Custom Middleware
1. Generate middleware using Artisan:
   ```bash
   php artisan make:middleware CheckAdmin
   ```

2. Define the logic in the middleware:
   ```php
   public function handle($request, Closure $next)
   {
       if (auth()->check() && auth()->user()->role !== 'admin') {
           return redirect('/');
       }
       return $next($request);
   }
   ```

3. Register the middleware in `app/Http/Kernel.php`:
   ```php
   protected $routeMiddleware = [
       'checkAdmin' => \App\Http\Middleware\CheckAdmin::class,
   ];
   ```

4. Apply the middleware to routes:
   ```php
   Route::get('/admin', [AdminController::class, 'index'])->middleware('checkAdmin');
   ```

---

## Hands-On Task
1. Set up authentication using `auth` scaffolding with Bootstrap.
2. Protect routes like `/dashboard` using the `auth` middleware.
3. Create a custom middleware to restrict access to admin-only routes.

---

## Summary
In this session, we learned how to:
1. Set up authentication using Laravel’s built-in `auth` scaffolding with Bootstrap.
2. Resolve Vite.js compatibility issues for Laravel 9+.
3. Explore other authentication options like Breeze, Jetstream, and Passport.
4. Use middleware to filter requests and protect routes.

This ensures your Laravel application is secure and user-friendly.
