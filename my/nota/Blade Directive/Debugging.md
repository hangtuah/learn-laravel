# **Laravel Blade Directives: Nyahpepijat (Debugging)**

Laravel menyediakan beberapa alat untuk membantu dalam proses **nyahpepijat (debugging)** dalam templat Blade. Dengan direktif khusus, anda boleh mencetak data dan mengenal pasti isu dalam aplikasi dengan lebih mudah.

---

## **1. Menggunakan `@dump()` untuk Mencetak Data**

Direktif `@dump()` membolehkan anda mencetak maklumat mengenai satu atau lebih pembolehubah secara terus dalam templat Blade.

### **Contoh Penggunaan:**
```blade
@dump($user)
```

🔹 **Penjelasan:**
- Ini akan mencetak nilai `$user` dalam format yang mudah dibaca oleh manusia, termasuk struktur array atau objek.

Jika anda ingin mencetak lebih daripada satu pembolehubah:
```blade
@dump($user, $orders)
```

---

## **2. Menggunakan `@dd()` untuk Berhenti & Cetak Data**

Direktif `@dd()` (die and dump) berfungsi sama seperti `@dump()`, tetapi ia akan menghentikan eksekusi selepas mencetak data.

### **Contoh Penggunaan:**
```blade
@dd($user)
```

🔹 **Penjelasan:**
- Ini akan mencetak kandungan `$user` dalam format yang terperinci dan menghentikan skrip daripada terus berjalan.
- Sangat berguna apabila anda ingin melihat nilai sesuatu pembolehubah tanpa menjalankan kod yang lain.

---

## **3. Menggunakan `{{ var_dump() }}` dalam Blade**

Walaupun tidak disyorkan dalam kebanyakan kes kerana keluaran yang tidak kemas, anda masih boleh menggunakan `var_dump()` dalam Blade dengan mencetaknya dalam kurungan `{{ }}`.

### **Contoh Penggunaan:**
```blade
{{ var_dump($user) }}
```

🔹 **Penjelasan:**
- Ini akan mencetak struktur `$user`, tetapi tanpa pemformatan yang baik seperti `@dump()` atau `@dd()`.

---

## **4. Menggunakan `{{ print_r() }}` dalam Blade**

`print_r()` juga boleh digunakan untuk mencetak data dalam format yang lebih ringkas berbanding `var_dump()`.

### **Contoh Penggunaan:**
```blade
{{ print_r($user, true) }}
```

🔹 **Penjelasan:**
- Mencetak nilai `$user` dengan format yang lebih ringkas tetapi kurang terperinci.

---

## **5. Debugbar untuk Debugging Lanjutan**

Laravel menyokong pakej **Laravel Debugbar** yang menyediakan antara muka visual untuk debugging yang lebih terperinci.

### **Cara Pasang Laravel Debugbar:**
```sh
composer require barryvdh/laravel-debugbar --dev
```

Tambahkan servis penyediaan dalam `config/app.php` jika perlu:
```php
Barryvdh\Debugbar\ServiceProvider::class,
```

Debugbar akan secara automatik menunjukkan maklumat permintaan, pangkalan data, dan prestasi aplikasi anda dalam penyemak imbas.

---

## **Ringkasan**

| Direktif/Fungsi | Keterangan |
|----------------|------------|
| `@dump($var)` | Mencetak data dengan format yang mudah dibaca. |
| `@dd($var)` | Mencetak data dan menghentikan skrip. |
| `{{ var_dump($var) }}` | Mencetak data secara mentah, tetapi tidak disyorkan. |
| `{{ print_r($var, true) }}` | Mencetak data dalam format yang lebih ringkas. |
| **Laravel Debugbar** | Pakej untuk debugging yang lebih terperinci dalam penyemak imbas. |

---

Dengan menggunakan teknik nyahpepijat ini, anda boleh mengenal pasti masalah dalam aplikasi Laravel dengan lebih mudah dan cepat! 🚀
