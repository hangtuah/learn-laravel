# **Laravel Blade Directives: Direktif Khusus (Custom Directives)**

Laravel membolehkan anda mencipta **direktif Blade khusus** untuk menjadikan kod templat lebih bersih, tersusun, dan boleh digunakan semula. Anda boleh menambahkan logik tersuai ke dalam Blade menggunakan fungsi `Blade::directive()`.

---

## **1. Mencipta Direktif Blade Tersuai**

Untuk mencipta direktif tersuai, anda boleh menambah kod berikut dalam `AppServiceProvider` atau mencipta penyedia perkhidmatan tersendiri.

### **Contoh: Direktif `@uppercase` untuk Menukar Teks ke Huruf Besar**
```php
use Illuminate\Support\Facades\Blade;

public function boot()
{
    Blade::directive('uppercase', function ($expression) {
        return "<?php echo strtoupper($expression); ?>";
    });
}
```

🔹 **Penjelasan:**
- Direktif `@uppercase('hello')` akan ditukar kepada `HELLO`.
- `strtoupper()` digunakan untuk menukar teks ke huruf besar.

### **Penggunaan dalam Fail Blade:**
```blade
<p>@uppercase('hello world')</p>
```
🔹 **Output:**
```html
<p>HELLO WORLD</p>
```

---

## **2. Direktif untuk Format Mata Wang**
Anda boleh mencipta direktif untuk memformatkan nombor sebagai mata wang.

### **Contoh: Direktif `@currency`**
```php
Blade::directive('currency', function ($expression) {
    return "<?php echo 'RM ' . number_format($expression, 2); ?>";
});
```

### **Penggunaan dalam Fail Blade:**
```blade
<p>Harga: @currency(1500)</p>
```
🔹 **Output:**
```html
<p>Harga: RM 1,500.00</p>
```

---

## **3. Direktif untuk Format Tarikh**
Anda juga boleh membuat direktif untuk memformatkan tarikh menggunakan `Carbon`.

### **Contoh: Direktif `@formatDate`**
```php
use Carbon\Carbon;

Blade::directive('formatDate', function ($expression) {
    return "<?php echo Carbon::parse($expression)->format('d M Y'); ?>";
});
```

### **Penggunaan dalam Fail Blade:**
```blade
<p>Tarikh: @formatDate('2025-01-01')</p>
```
🔹 **Output:**
```html
<p>Tarikh: 01 Jan 2025</p>
```

---

## **4. Menggunakan Direktif dengan Parameter Pelbagai**
Anda boleh menerima parameter berganda dalam direktif tersuai dengan fungsi `explode()`.

### **Contoh: Direktif `@greeting` dengan Nama Pengguna**
```php
Blade::directive('greeting', function ($expression) {
    return "<?php echo 'Selamat datang, ' . ucwords($expression) . '!'; ?>";
});
```

### **Penggunaan dalam Fail Blade:**
```blade
<p>@greeting('ali')</p>
```
🔹 **Output:**
```html
<p>Selamat datang, Ali!</p>
```

---

## **Ringkasan**

| Direktif Tersuai | Keterangan |
|----------------|------------|
| `@uppercase($text)` | Menukar teks ke huruf besar. |
| `@currency($amount)` | Memformatkan nombor sebagai mata wang. |
| `@formatDate($date)` | Memformatkan tarikh menggunakan `Carbon`. |
| `@greeting($name)` | Memaparkan ucapan selamat datang dengan nama pengguna. |

---

Dengan mencipta direktif Blade tersuai, anda boleh menjadikan kod lebih bersih, tersusun, dan mudah diselenggara. 🚀
