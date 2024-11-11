
# Database Basics with Laravel

## Introduction
Laravel makes working with databases easy and efficient with tools like migrations, seeders, and the Eloquent ORM. In this session, we’ll explore how to configure a database, create migrations, and interact with data.

---

## Configuring the Database
1. **Set up the `.env` file**:
   Define your database credentials in the `.env` file:
   ```env
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=your_database_name
   DB_USERNAME=your_database_user
   DB_PASSWORD=your_database_password
   ```

2. **Test the connection**:
   Run the following Artisan command to check if Laravel connects to the database:
   ```bash
   php artisan migrate
   ```

---

## Migrations in Laravel
Migrations are version control for your database, allowing you to create and modify tables programmatically.

### Key Concepts:
1. **Creating a Migration**:
   Use Artisan to generate a migration file:
   ```bash
   php artisan make:migration create_users_table
   ```

2. **Defining the Schema**:
   Edit the generated migration file in `database/migrations`:
   ```php
   public function up()
   {
       Schema::create('users', function (Blueprint $table) {
           $table->id();
           $table->string('name');
           $table->string('email')->unique();
           $table->timestamps();
       });
   }
   ```

3. **Running Migrations**:
   Apply migrations to your database:
   ```bash
   php artisan migrate
   ```

4. **Rolling Back Migrations**:
   Revert the last batch of migrations:
   ```bash
   php artisan migrate:rollback
   ```

---

## Eloquent ORM Basics
Eloquent is Laravel's built-in Object-Relational Mapping (ORM) system that makes it easy to interact with your database.

### Key Concepts:
1. **Creating a Model**:
   Generate a model using Artisan:
   ```bash
   php artisan make:model User
   ```

2. **Basic Queries**:
   Use Eloquent methods to interact with the database:
    - Retrieve all records:
      ```php
      $users = User::all();
      ```
    - Find a record by ID:
      ```php
      $user = User::find(1);
      ```
    - Create a new record:
      ```php
      $user = new User;
      $user->name = 'John Doe';
      $user->email = 'john@example.com';
      $user->save();
      ```
    - Update a record:
      ```php
      $user = User::find(1);
      $user->name = 'Jane Doe';
      $user->save();
      ```
    - Delete a record:
      ```php
      $user = User::find(1);
      $user->delete();
      ```

---

## Database Seeders
Seeders are used to populate your database with sample or initial data.

1. **Creating a Seeder**:
   Generate a seeder file:
   ```bash
   php artisan make:seeder UsersTableSeeder
   ```

2. **Defining Data in the Seeder**:
   Edit the `run` method:
   ```php
   public function run()
   {
       User::create([
           'name' => 'Admin',
           'email' => 'admin@example.com',
           'password' => bcrypt('password'),
       ]);
   }
   ```

3. **Running Seeders**:
   Execute all seeders:
   ```bash
   php artisan db:seed
   ```

---

## Hands-On Task
1. Configure your `.env` file to connect to a MySQL database.
2. Create a migration for a `posts` table with the following columns:
    - `id`: Primary key
    - `title`: String
    - `content`: Text
    - `created_at` and `updated_at`: Timestamps
3. Run the migration and verify the table is created.
4. Create a seeder to populate the `posts` table with sample data.
5. Use Eloquent to retrieve, update, and delete records in the `posts` table.

---

## Summary
In this session, we learned how to configure Laravel's database, use migrations to manage tables, and seed data. We also explored Eloquent ORM for efficient database interaction. These tools make it easy to handle complex database operations with minimal effort.

---
