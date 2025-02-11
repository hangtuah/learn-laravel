# Routes, Controller, dan View

## Routes dalam Laravel
Routes ditakrifkan dalam fail `routes/web.php`. Ia menentukan Controller atau tindak balas yang akan mengendalikan permintaan URL tertentu.

### Konsep Utama:
1. **Routes Asas**:
   Routes ringkas yang mengembalikan teks:
   ```php
   Route::get('/hello', function () {
       return 'Hello, Dunia!';
   });
   ```

2. **Parameter Routes**:
   Menangkap nilai dinamik daripada URL:
   ```php
   Route::get('/pengguna/{id}', function ($id) {
       return "ID Pengguna: $id";
   });
   ```

3. **Routes Bernama**:
   Menamakan Routes untuk rujukan mudah:
   ```php
   Route::get('/profil', function () {
       return 'Profil Pengguna';
   })->name('profil');
   ```

4. **Kumpulan Routes**:
   Mengelompokkan Routes dengan atribut yang dikongsi seperti middleware:
   ```php
   Route::middleware(['auth'])->group(function () {
       Route::get('/dashboard', function () {
           return 'Dashboard';
       });
   });
   ```

5. **Routes ke Controller dengan Nama**:
   Memetakan Routes ke kaedah Controller tertentu dan memberinya nama:
   ```php
   Route::get('/laporan/senarai', [App\Http\Controllers\ReportController::class, 'index'])->name('laporan.index');
   ```

---

## Controller dalam Laravel
Controller mengendalikan logik aplikasi anda. Ia memproses permintaan dan mengembalikan tindak balas.

### Konsep Utama:
1. **Mewujudkan Controller**:
   Gunakan Artisan untuk menjana Controller:
   ```bash
   php artisan make:controller MenuController
   ```

2. **Menentukan Kaedah Controller**:
   Tambah kaedah untuk mengendalikan logik tertentu:
   ```php
   namespace App\Http\Controllers;

   use Illuminate\Http\Request;

   class MenuController extends Controller
   {
       public function show()
       {
           $hidangan = ['Pasta', 'Burger', 'Pizza'];
           return view('menu', ['hidangan' => $hidangan]);
       }
   }
   ```

3. **Menghubungkan Routes ke Controller**:
   Memetakan Routes ke kaedah Controller:
   ```php
   Route::get('/menu', [MenuController::class, 'show']);
   ```

---

## View dalam Laravel
View menjana HTML untuk aplikasi anda dan disimpan dalam direktori `resources/views`.

### Konsep Utama:
1. **Mewujudkan View**:
   Buat fail templat Blade (contoh: `menu.blade.php`):
   ```html
   <!-- resources/views/menu.blade.php -->
   <h1>Menu Kami</h1>
   <ul>
       @foreach ($hidangan as $hidang)
           <li>{{ $hidang }}</li>
       @endforeach
   </ul>
   ```

2. **Mengembalikan View**:
   Mengembalikan View daripada Controller atau Routes:
   ```php
   return view('menu');
   ```

3. **Menghantar Data ke View**:
   Menghantar pembolehubah daripada Controller ke View:
   ```php
   return view('menu', ['hidangan' => $hidangan]);
   ```

---

## Tugasan Praktikal
1. Tetapkan Routes dalam `web.php` yang memaparkan mesej "Selamat datang ke Laravel!".
2. Buat `MenuController` dengan kaedah yang mengambil senarai hidangan.
3. Buat View Blade untuk memaparkan senarai hidangan.
4. Sambungkan Routes ke `MenuController` dan uji dalam pelayar web anda.

---

## Ringkasan
**Routes, Controller, dan View dalam Laravel** bekerjasama untuk mengendalikan permintaan pengguna dan memaparkan tindak balas:
- **Routes**: Pelayan – Mengarahkan permintaan ke tempat yang betul.
- **Controller**: Tukang masak – Memproses permintaan dan menyediakan data.
- **View**: Hidangan di pinggan – Memformat dan memaparkan tindak balas.

Pendekatan ini menjadikan aplikasi Laravel lebih bersih, tersusun, dan mudah diurus.

