# **Pengesahan dan Kebenaran (RBAC) dalam Laravel**

## **Pengenalan**
Pengesahan (Authentication) adalah ciri penting dalam aplikasi web yang membolehkan pengguna log masuk, mendaftar, dan mengakses kandungan yang dilindungi. Laravel menyediakan kaedah mudah untuk mengimplementasikan pengesahan melalui `auth` scaffolding.

Dalam bahagian ini, kita akan menyediakan pengesahan dengan `auth` Bootstrap scaffolding dan menangani isu keserasian dengan Vite.js dalam Laravel 9+.

---

## **Menyediakan Pengesahan dengan Auth Scaffolding (Bootstrap)**

### **Langkah 1: Pasang Laravel UI**
1. Pasang pakej Laravel UI menggunakan Composer:
   ```bash
   composer require laravel/ui
   ```

2. Jana scaffolding pengesahan dengan Bootstrap:
   ```bash
   php artisan ui bootstrap --auth
   ```

3. Pasang kebergantungan dan kompilasi aset:
   ```bash
   npm install
   npm run dev
   ```

---

### **Langkah 2: Jalankan Migrasi**
Jalankan migrasi pangkalan data untuk mencipta jadual yang diperlukan bagi pengesahan:
```bash
php artisan migrate
```

Ini akan mencipta jadual seperti `users` dalam pangkalan data anda.

---

### **Langkah 3: Menyelesaikan Isu Keserasian Vite.js dalam Laravel 9+**
Jika anda menggunakan Laravel 9 atau versi lebih baru, anda mungkin menghadapi isu keserasian dengan Vite.js dalam Laravel UI. Ikuti langkah-langkah ini untuk menyelesaikan isu tersebut:

#### **1. Pasang Laravel Mix**
Gantikan Vite dengan Webpack Mix:
```bash
npm install laravel-mix --save-dev
npm install sass sass-loader --save-dev
```

Cipta fail `webpack.mix.js` dalam direktori root:
```javascript
const mix = require('laravel-mix');

mix.js('resources/js/app.js', 'public/js')
   .sass('resources/sass/app.scss', 'public/css');
```

#### **2. Buang Konfigurasi Vite**
1. Padam fail `vite.config.js`.
2. Kemaskini bahagian skrip dalam `package.json`:
   ```json
   "scripts": {
       "dev": "npm run development",
       "build": "npm run production",
       "development": "mix",
       "production": "mix --production"
   }
   ```
3. Buang kebergantungan Vite:
   ```bash
   npm uninstall vite laravel-vite-plugin
   ```

#### **3. Kompilasi Aset**
Kompilasi aset menggunakan Laravel Mix:
```bash
npm run dev
```

---

### **Langkah 4: Uji Pengesahan**
1. Jalankan pelayan pembangunan Laravel:
   ```bash
   php artisan serve
   ```
2. Layari URL berikut dalam pelayar:
    - **Daftar**: `/register`
    - **Log Masuk**: `/login`
    - **Log Keluar**: `/logout`

Kini sistem pengesahan anda sudah berfungsi sepenuhnya dengan Bootstrap.

---

## **Kebenaran dengan RBAC (Role-Based Access Control)**
Kawalan Akses Berasaskan Peranan (RBAC) membolehkan kita mengehadkan akses berdasarkan peranan pengguna.

### **1. Tambah Medan `role` dalam Jadual Pengguna**
Edit fail migrasi pengguna dan tambahkan medang `role`:
```php
Schema::table('users', function (Blueprint $table) {
    $table->string('role')->default('user');
});
```
Jalankan migrasi:
```bash
php artisan migrate
```

### **2. Tentukan Middleware untuk Peranan**
Cipta middleware untuk mengesahkan peranan:
```bash
php artisan make:middleware RoleMiddleware
```
Edit fail `app/Http/Middleware/RoleMiddleware.php`:
```php
public function handle($request, Closure $next, $role)
{
    if (auth()->check() && auth()->user()->role !== $role) {
        return redirect('/');
    }
    return $next($request);
}
```

### **3. Daftarkan Middleware**
Daftarkan middleware dalam `app/Http/Kernel.php`:
```php
protected $routeMiddleware = [
    'role' => \App\Http\Middleware\RoleMiddleware::class,
];
```

### **4. Gunakan Middleware dalam Laluan**
Gunakan middleware dalam laluan untuk mengehadkan akses:
```php
Route::get('/admin', [AdminController::class, 'index'])->middleware('role:admin');
```

---

## **Tugasan Praktikal**
1. Sediakan pengesahan menggunakan `auth` scaffolding dengan Bootstrap.
2. Gunakan middleware `auth` untuk melindungi laluan `/dashboard`.
3. Cipta middleware `RoleMiddleware` untuk mengehadkan akses kepada pentadbir sahaja.
4. Tambah peranan `admin` dan `user` dalam jadual `users` dan uji kawalan akses.

---

## **Kesimpulan**
Dalam sesi ini, kita telah belajar bagaimana untuk:
1. Menyediakan sistem pengesahan menggunakan Laravel UI dengan Bootstrap.
2. Menyelesaikan isu keserasian dengan Vite.js.
3. Menggunakan RBAC untuk mengehadkan akses berdasarkan peranan pengguna.
4. Menggunakan middleware untuk mengawal akses laluan.

Dengan pelaksanaan ini, aplikasi Laravel anda akan lebih selamat dan teratur dalam mengawal akses pengguna.

