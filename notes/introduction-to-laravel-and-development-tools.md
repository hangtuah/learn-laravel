## What is Laravel?

Laravel is a tool that helps developers build websites and web applications more easily. It is written in PHP, a
programming language used for making dynamic websites. Laravel was created by Taylor Otwell in 2011 and is known for
being simple, organized, and powerful.

---

## Key Features of Laravel

Here are some of the things that make Laravel special:

1. **MVC Architecture**: Laravel organizes your code into Models, Views, and Controllers, making it clean and easy to
   manage.
2. **Eloquent ORM**: Laravel helps you talk to your database using simple code instead of complicated SQL queries.
3. **Blade Templating Engine**: Makes it easy to create reusable webpage designs.
4. **Artisan CLI**: A command-line tool that helps with tasks like creating files and running database migrations.
5. **Built-in Authentication**: Laravel comes with tools to handle user login, registration, and roles.
6. **Rich Ecosystem**: Laravel has many additional tools like Laravel Nova (admin panel) and Laravel Passport (API
   security).

---

## Development Tools

To start with Laravel, you will need the following tools:

### 1. PHP

- Laravel requires PHP version 8.3 or higher.

### 2. Composer

- Composer is a tool that manages the packages (libraries) Laravel needs. You can download it
  from [https://getcomposer.org/](https://getcomposer.org/).

### 3. Local Server

- Laravel needs a server to run. You can use tools like:
    - **XAMPP** (Windows/Mac/Linux)
    - **Laragon** (Windows)
    - **MAMP** (Mac)

### 4. Code Editor

- A code editor is where you write your Laravel code. Popular options include:
    - **Visual Studio Code** (free)
    - **PHPStorm** (paid, powerful for PHP)
    - **Sublime Text** (free/trial)

---
## Installation Guides

Here are the installation guides for setting up the necessary tools for Laravel development:

1. [XAMPP Installation Guide](installation-guides/install-xampp-windows.md)
2. [Composer Installation Guide](installation-guides/install-composer-windows.md)
3. [Visual Studio Code Installation Guide](installation-guides/install-vscode-windows.md)
4. [Git Bash Installation Guide](installation-guides/install-gitbash-windows.md)


---

## Installing Laravel

Follow these steps to install Laravel and choose your desired version:

1. Install using Composer:
   ```bash
   composer create-project --prefer-dist laravel/laravel project_name "^10.0"
   ```
2. Run the Laravel server:
    ```bash
    php artisan serve
    ```
3. Open http://localhost:8000 in your web browser to see your Laravel project.