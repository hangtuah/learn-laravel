
# Prerequisite Skills for Learning Laravel

Before learning Laravel, it’s important to know some basic skills. These skills will help you understand how Laravel works and make learning easier.

---

## 1. Basic PHP Knowledge
Laravel is built with PHP, so you should know how to:
- Create variables and use functions.
- Write simple programs with **if/else** conditions and loops.
- Understand object-oriented programming (OOP):
  - Learn about **classes**, **objects**, and **methods**.

For example:
```php
class Animal {
    public $name;

    public function makeSound() {
        return "Roar";
    }
}

$lion = new Animal();
$lion->name = "Lion";
echo $lion->makeSound();
```

---

## 2. HTML, CSS, and JavaScript
These are the building blocks of web development:
- **HTML**: Creates the structure of a webpage (like headings, paragraphs, and forms).
- **CSS**: Adds style (like colors, fonts, and layouts).
- **JavaScript**: Adds interactivity (like animations or clicking buttons).

For example:
```html
<!DOCTYPE html>
<html>
<head>
    <style>
        h1 { color: blue; }
    </style>
</head>
<body>
    <h1>Welcome to My Website</h1>
    <button onclick="alert('Hello!')">Click Me</button>
</body>
</html>
```

---

## 3. Database Basics
Laravel works with databases to store data. You should know how to:
- Create tables and store data in them.
- Write simple SQL commands like:
  ```sql
  SELECT * FROM users;
  INSERT INTO users (name, email) VALUES ('John', 'john@example.com');
  ```
- Understand relationships between tables (e.g., one user can have many posts).

---

## 4. Command Line Basics
Learn how to use the terminal (Command Prompt or Git Bash) to:
- Navigate folders.
- Run commands like:
  ```bash
  php artisan serve
  ```

---

## 5. What is MVC?
MVC stands for **Model-View-Controller**. It’s a way to organize your code:
1. **Model**: Deals with data (e.g., a list of users).
2. **View**: Displays the data (e.g., a webpage).
3. **Controller**: Handles the logic (e.g., when a user logs in).

Example:
- You visit a webpage (Controller).
- The Controller gets data from the database (Model).
- The webpage shows the data (View).

---

## 6. Git Basics (Optional)
Git is used to save and track your code changes. Learn simple commands like:
```bash
git init
git add .
git commit -m "My first commit"
git push
```

---

## 7. HTTP Basics
Understand how a browser sends requests to a server:
- **GET**: To fetch data (e.g., loading a webpage).
- **POST**: To send data (e.g., submitting a form).

For example, when you visit `www.example.com`, your browser sends a **GET request** to get the webpage.

---

## 8. Composer
Composer is a tool that Laravel uses to manage packages (extra features). Learn how to:
- Install Composer.
- Run commands like:
  ```bash
  composer install
  composer require laravel/ui
  ```

---

## Summary
To learn Laravel, you need basic knowledge of:
1. **PHP** (the language Laravel uses).
2. **HTML, CSS, and JavaScript** (for building webpages).
3. **Databases** (to store data).
4. **Command Line** (to run Laravel commands).
5. **MVC** (to organize your project).

If you know these basics, you’re ready to start building amazing web applications with Laravel! 🚀
