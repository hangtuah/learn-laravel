# **Laravel Blade Directives: Struktur Kawalan**

## **Pernyataan Bersyarat (Conditional Statements)**
Laravel Blade menyediakan pernyataan bersyarat yang memudahkan kawalan logik dalam templat tanpa perlu menulis kod PHP secara langsung.

## **1. `@if`, `@elseif`, `@else`, dan `@endif`**
Direktif `@if` digunakan untuk melaksanakan kod berdasarkan syarat tertentu.

### **Contoh:**
```blade
@if($status === 'draf')
    <p>Status: Draf</p>
@elseif($status === 'hantar')
    <p>Status: Telah dihantar</p>
@elseif($status === 'semak')
    <p>Status: Dalam semakan</p>
@elseif($status === 'lulus')
    <p>Status: Diluluskan</p>
@elseif($status === 'tolak')
    <p>Status: Ditolak</p>
@else
    <p>Status tidak diketahui</p>
@endif
```
🔹 **Penjelasan:**
- Jika status adalah `'draf'`, ia akan memaparkan "Status: Draf".
- Jika status adalah `'hantar'`, ia akan memaparkan "Status: Telah dihantar".
- Jika status adalah `'semak'`, ia akan memaparkan "Status: Dalam semakan".
- Jika status adalah `'lulus'`, ia akan memaparkan "Status: Diluluskan".
- Jika status adalah `'tolak'`, ia akan memaparkan "Status: Ditolak".
- Jika status tidak sepadan dengan mana-mana di atas, ia akan memaparkan "Status tidak diketahui".
---

## **2. `@isset` dan `@empty`**
Direktif ini digunakan untuk menyemak sama ada pembolehubah wujud (`@isset`) atau kosong (`@empty`).

### **Contoh `@isset`:**
```blade
@isset($user)
    <p>Pengguna telah ditetapkan: {{ $user->name }}</p>
@endisset
```
🔹 **Penjelasan:**
- Kod ini hanya akan dijalankan jika `$user` wujud.

### **Contoh `@empty`:**
```blade
@empty($cart)
    <p>Troli belian anda kosong.</p>
@endempty
```
🔹 **Penjelasan:**
- Jika `$cart` kosong, ia akan memaparkan mesej tersebut.

---

## **3. `@switch`, `@case`, dan `@default`**
Blade juga menyokong pernyataan `switch` menggunakan direktif `@switch`.

### **Contoh:**
```blade
@switch($user->role)
    @case('admin')
        <p>Akses Panel Admin</p>
        @break

    @case('editor')
        <p>Dashboard Editor</p>
        @break

    @default
        <p>Pengguna Biasa</p>
@endswitch
```
🔹 **Penjelasan:**
- Jika peranan pengguna adalah `'admin'`, ia memaparkan "Akses Panel Admin".
- Jika `'editor'`, ia memaparkan "Dashboard Editor".
- Jika bukan kedua-duanya, ia memaparkan "Pengguna Biasa".

---

## **Ringkasan**
| Direktif | Keterangan |
|-----------|------------|
| `@if(condition)` | Dilaksanakan jika syarat adalah `true`. |
| `@elseif(condition)` | Dilaksanakan jika `@if` sebelumnya `false` dan syarat ini `true`. |
| `@else` | Dilaksanakan jika tiada syarat di atas yang benar. |
| `@endif` | Menamatkan blok `@if`. |
| `@unless(condition)` | Dilaksanakan jika syarat adalah `false`. |
| `@isset($var)` | Menyemak jika pembolehubah wujud. |
| `@empty($var)` | Menyemak jika pembolehubah kosong. |
| `@switch($var)`, `@case(value)`, `@default` | Melaksanakan logik `switch-case`. |

---

# **Gelung (Loops)**

Laravel Blade menyediakan beberapa jenis gelung untuk mengulangi data dalam templat dengan lebih mudah dan kemas.

## **1. `@for`**
Direktif `@for` digunakan untuk mengulangi blok kod berdasarkan syarat tertentu.

### **Contoh:**
```blade
@for($i = 1; $i <= 5; $i++)
    <p>Item ke-{{ $i }}</p>
@endfor
```
🔹 **Penjelasan:**
- Kod ini akan mencetak "Item ke-1" hingga "Item ke-5".

---

## **2. `@foreach`**
Direktif `@foreach` digunakan untuk mengulangi setiap elemen dalam koleksi atau array.

### **Contoh:**
```blade
@foreach($users as $user)
    <p>Nama: {{ $user->name }}</p>
@endforeach
```
🔹 **Penjelasan:**
- Kod ini akan mengulangi setiap pengguna dalam `$users` dan mencetak nama mereka.

---

## **3. `@while`**
Direktif `@while` digunakan untuk mengulangi kod selagi syarat tertentu adalah benar.

### **Contoh:**
```blade
@php $count = 1; @endphp
@while($count <= 3)
    <p>Pengiraan: {{ $count }}</p>
    @php $count++; @endphp
@endwhile
```
🔹 **Penjelasan:**
- Kod ini akan mencetak "Pengiraan: 1" hingga "Pengiraan: 3".

---

## **Ringkasan**
| Direktif | Keterangan |
|-----------|------------|
| `@for` | Mengulangi blok kod berdasarkan syarat tertentu. |
| `@foreach` | Mengulangi setiap elemen dalam koleksi atau array. |
| `@forelse` | Sama seperti `@foreach` tetapi mempunyai keadaan `@empty` jika koleksi kosong. |
| `@while` | Mengulangi kod selagi syarat tertentu benar. |
| `@continue` | Melangkau iterasi semasa dalam gelung. |
| `@break` | Menghentikan gelung sepenuhnya. |

---