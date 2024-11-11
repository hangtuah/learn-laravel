
# Eloquent ORM and CRUD Operations

## Introduction
Eloquent ORM (Object-Relational Mapping) is Laravel’s default ORM, providing an elegant and simple way to interact with your database. Eloquent maps database tables to PHP models, enabling intuitive data handling.

---

## Setting Up Eloquent
1. **Model Creation**:
   Create a model using Artisan:
   ```bash
   php artisan make:model Post
   ```

2. **Model and Table Naming**:
   - By default, Eloquent maps the model name (`Post`) to a table named `posts` (plural form).
   - To customize the table name, define the `$table` property:
     ```php
     protected $table = 'custom_table_name';
     ```

3. **Database Connection**:
   Ensure your `.env` file is correctly configured for the database connection.

---

## Basic CRUD Operations with Eloquent

### 1. **Create**
Insert a new record into the database:
```php
$post = new Post();
$post->title = 'First Post';
$post->content = 'This is the content of the first post.';
$post->save();
```
Alternatively, use the `create` method (requires `$fillable` in the model):
```php
protected $fillable = ['title', 'content'];

Post::create([
    'title' => 'Second Post',
    'content' => 'Content of the second post.'
]);
```

### 2. **Read**
Retrieve records from the database:
- Retrieve all records:
  ```php
  $posts = Post::all();
  ```
- Retrieve a single record by ID:
  ```php
  $post = Post::find(1);
  ```
- Query with conditions:
  ```php
  $posts = Post::where('title', 'First Post')->get();
  ```
- Retrieve the first record matching a condition:
  ```php
  $post = Post::where('title', 'First Post')->first();
  ```

### 3. **Update**
Update an existing record:
```php
$post = Post::find(1);
$post->title = 'Updated Title';
$post->save();
```
Alternatively, use the `update` method:
```php
Post::where('id', 1)->update(['title' => 'Another Updated Title']);
```

### 4. **Delete**
Remove a record from the database:
```php
$post = Post::find(1);
$post->delete();
```
Alternatively, use the `destroy` method:
```php
Post::destroy(1); // Delete by ID
Post::destroy([1, 2, 3]); // Delete multiple records
```

---

## Relationships in Eloquent
Eloquent makes it easy to define and interact with database relationships.

### 1. **One-to-One**
Define the relationship in the models:
```php
// In User model
public function profile()
{
    return $this->hasOne(Profile::class);
}

// In Profile model
public function user()
{
    return $this->belongsTo(User::class);
}
```

### 2. **One-to-Many**
```php
// In Post model
public function comments()
{
    return $this->hasMany(Comment::class);
}

// In Comment model
public function post()
{
    return $this->belongsTo(Post::class);
}
```

### 3. **Many-to-Many**
```php
// In User model
public function roles()
{
    return $this->belongsToMany(Role::class);
}

// In Role model
public function users()
{
    return $this->belongsToMany(User::class);
}
```

---

## Hands-On Task
1. Create a `Post` model and migration with the following fields:
   - `id`: Primary key
   - `title`: String
   - `content`: Text
   - `created_at` and `updated_at`: Timestamps
2. Perform the following CRUD operations:
   - Add 3 sample posts to the database.
   - Retrieve all posts and filter by a specific condition.
   - Update the title of a post.
   - Delete a specific post.
3. Define a one-to-many relationship between `Post` and `Comment`.
4. Use Eloquent to retrieve comments for a specific post.

---

## Summary
In this session, we learned how to use Eloquent ORM to perform CRUD operations and manage relationships between tables. Eloquent’s simplicity and flexibility make it a powerful tool for interacting with databases in Laravel.

---
