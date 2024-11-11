
# SQL Table Creation Tutorial for Laravel Simulation

This tutorial demonstrates how to create tables using SQL commands to simulate single and join table operations with Laravel. We will create three tables: **users**, **posts**, and **comments**.

---

## Table Structure and Commands

### Step 1: Create the `users` Table

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);
```

**Explanation**:
- `id`: Primary key, auto-increments for each user.
- `name`: User's name.
- `email`: Unique email for each user.
- `created_at` and `updated_at`: Timestamps to track record creation and updates.

---

### Step 2: Create the `posts` Table

```sql
CREATE TABLE posts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    title VARCHAR(255) NOT NULL,
    content TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
```

**Explanation**:
- `id`: Primary key for each post.
- `user_id`: Foreign key referencing the `id` column in the `users` table.
- `title`: Title of the post.
- `content`: Content of the post.
- `created_at` and `updated_at`: Timestamps for record tracking.
- `FOREIGN KEY`: Ensures posts are linked to valid users. `ON DELETE CASCADE` deletes posts if the associated user is deleted.

---

### Step 3: Create the `comments` Table

```sql
CREATE TABLE comments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    post_id INT NOT NULL,
    user_id INT NOT NULL,
    comment TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    FOREIGN KEY (post_id) REFERENCES posts(id) ON DELETE CASCADE,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
```

**Explanation**:
- `id`: Primary key for each comment.
- `post_id`: Foreign key referencing the `id` column in the `posts` table.
- `user_id`: Foreign key referencing the `id` column in the `users` table.
- `comment`: Content of the comment.
- `created_at` and `updated_at`: Timestamps for record tracking.
- `FOREIGN KEY`: Ensures comments are linked to valid posts and users.

---

## Sample Data Insertion

**Insert sample data into `users`:**
```sql
INSERT INTO users (name, email) VALUES
('John Doe', 'john@example.com'),
('Jane Smith', 'jane@example.com');
```

**Insert sample data into `posts`:**
```sql
INSERT INTO posts (user_id, title, content) VALUES
(1, 'First Post', 'This is the content of the first post.'),
(2, 'Second Post', 'This is the content of the second post.');
```

**Insert sample data into `comments`:**
```sql
INSERT INTO comments (post_id, user_id, comment) VALUES
(1, 2, 'Great post!'),
(2, 1, 'Thanks for sharing.');
```

---

## Query Examples

### 1. Single Table Query
Retrieve all posts by a specific user:
```sql
SELECT * FROM posts WHERE user_id = 1;
```

### 2. Join Tables Query
Get all comments with the post title and user name:
```sql
SELECT 
    comments.comment, 
    posts.title AS post_title, 
    users.name AS user_name
FROM 
    comments
JOIN 
    posts ON comments.post_id = posts.id
JOIN 
    users ON comments.user_id = users.id;
```

---

## Summary

With these tables, you can simulate:
1. Single-table queries using the `users`, `posts`, or `comments` table.
2. Join-table queries using relationships between the tables.

Use this setup to practice working with both raw SQL queries and Eloquent ORM in Laravel.
