# **Laravel Blade Directives: Laluan & URL (Routing & URLs)**

Blade menyediakan beberapa direktif yang memudahkan pengurusan **Routing & URLs** dalam templat Laravel. Ini membolehkan anda menjana pautan secara dinamik tanpa perlu menulis URL secara manual.

---

## **1. Menjana URL dengan `@url`**

Direktif `@url` digunakan untuk menjana URL berdasarkan laluan tertentu.

### **Contoh Penggunaan:**
```blade
<a href="{{ url('/home') }}">Halaman Utama</a>
```
🔹 **Penjelasan:**
- Menghasilkan URL penuh berdasarkan laluan `/home`.
- Jika aplikasi Laravel berjalan di `https://example.com`, pautan akan menjadi `https://example.com/home`.

---

## **2. Menjana Laluan dengan `@route`**

Direktif `@route` digunakan untuk menjana URL berdasarkan nama laluan yang telah ditakrifkan dalam `routes/web.php`.

### **Contoh Penggunaan:**
```blade
<a href="{{ route('dashboard') }}">Pergi ke Dashboard</a>
```

🔹 **Penjelasan:**
- Jika anda mempunyai laluan berikut dalam `routes/web.php`:
```php
Route::get('/dashboard', [DashboardController::class, 'index'])->name('dashboard');
```
- Direktif `@route('dashboard')` akan menghasilkan URL yang betul secara automatik.

### **Menggunakan Parameter dalam Laluan**
Jika laluan anda mempunyai parameter, anda boleh menghantarnya sebagai argumen:
```blade
<a href="{{ route('profile', ['id' => 1]) }}">Profil Saya</a>
```
🔹 **Penjelasan:**
- Jika anda mempunyai laluan berikut dalam `routes/web.php`:
```php
Route::get('/profile/{id}', [UserController::class, 'show'])->name('profile');
```
- Maka, `@route('profile', ['id' => 1])` akan menghasilkan `/profile/1`.

---

## **3. Menjana URL berdasarkan Controller dengan `@action`**

Direktif `@action` digunakan untuk menjana URL berdasarkan kaedah dalam sesebuah pengawal (controller).

### **Contoh Penggunaan:**
```blade
<a href="{{ action([HomeController::class, 'index']) }}">Laman Utama</a>
```
🔹 **Penjelasan:**
- Jika anda mempunyai kaedah berikut dalam `HomeController`:
```php
public function index() {
    return view('home');
}
```
- Maka, `@action([HomeController::class, 'index'])` akan menjana URL yang betul secara automatik.

---

## **4. Menjana URL Aset dengan `asset()`**

Direktif ini digunakan untuk menjana URL kepada fail aset seperti gambar, CSS, atau JavaScript.

### **Contoh Penggunaan:**
```blade
<link rel="stylesheet" href="{{ asset('css/style.css') }}">
<img src="{{ asset('images/logo.png') }}" alt="Logo">
```
🔹 **Penjelasan:**
- `asset('css/style.css')` akan menghasilkan sesuatu seperti `https://example.com/css/style.css`.
- `asset('images/logo.png')` akan menghasilkan sesuatu seperti `https://example.com/images/logo.png`.

---

## **Ringkasan**

| Direktif | Keterangan |
|-----------|------------|
| `@url('/path')` | Menjana URL berdasarkan laluan relatif. |
| `@route('route.name')` | Menjana URL berdasarkan nama laluan dalam Laravel. |
| `@route('route.name', ['param' => value])` | Menjana URL dengan parameter laluan. |
| `@action([Controller::class, 'method'])` | Menjana URL berdasarkan pengawal dan kaedahnya. |
| `asset('path')` | Menjana URL untuk aset statik dalam folder `public/`. |

---

Dengan menggunakan direktif ini, anda boleh mengurus pautan dan URL dalam Blade dengan lebih fleksibel dan mudah! 🚀
