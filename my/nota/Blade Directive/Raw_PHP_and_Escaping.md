# **Laravel Blade Directives: Kod PHP & Keselamatan (Raw PHP & Escaping)**

Laravel Blade menyediakan cara untuk menulis kod PHP secara langsung dalam templat serta mekanisme untuk melindungi daripada suntikan skrip dengan `escaping` output.

---

## **1. Menulis Kod PHP dalam Blade dengan `@php`**

Direktif `@php ... @endphp` membolehkan anda menulis kod PHP dalam templat Blade dengan lebih bersih dan tersusun.

### **Contoh Penggunaan:**
```blade
@php
    $total = 100;
    $discount = 20;
    $finalPrice = $total - $discount;
@endphp

<p>Harga Akhir: RM{{ $finalPrice }}</p>
```
🔹 **Penjelasan:**
- Kod PHP di dalam `@php ... @endphp` akan dieksekusi seperti dalam fail PHP biasa.

---

## **2. Mencetak Data dengan `{{ }}` (Escaping Output)**

Secara lalai, Blade akan **melarikan (escape)** kandungan yang dipaparkan menggunakan `{{ }}` untuk melindungi daripada suntikan skrip.

### **Contoh Penggunaan:**
```blade
<p>{{ $nama }}</p>
```
🔹 **Penjelasan:**
- Jika `$nama = "<script>alert('Bahaya');</script>";`, maka Blade akan mencetak teks secara selamat sebagai `&lt;script&gt;alert('Bahaya');&lt;/script&gt;`, menghalang serangan XSS.

---

## **3. Mencetak Data Tanpa `Escaping` dengan `{!! !!}`**

Gunakan `{!! !!}` jika anda ingin memaparkan data secara langsung tanpa `escaping`. **Namun, gunakan dengan berhati-hati untuk mengelakkan suntikan skrip berbahaya.**

### **Contoh Penggunaan:**
```blade
<p>{!! $teksHTML !!}</p>
```
🔹 **Penjelasan:**
- Jika `$teksHTML = "<strong>Selamat Datang!</strong>";`, maka output akan dipaparkan dengan teks tebal.
- **Jangan gunakan jika data berasal dari input pengguna tanpa disaring.**

---

## **4. Menggunakan `@verbatim` untuk Mencegah Blade Parsing**

Kadangkala, anda mungkin ingin memaparkan kod yang mengandungi sintaks Blade tanpa ia dieksekusi oleh Laravel.

### **Contoh Penggunaan:**
```blade
@verbatim
    <p>{{ Ini bukan Blade, hanya teks biasa }}</p>
@endverbatim
```
🔹 **Penjelasan:**
- Kandungan dalam `@verbatim ... @endverbatim` tidak akan diproses oleh Blade.

---

## **Ringkasan**

| Direktif/Fungsi | Keterangan |
|----------------|------------|
| `@php ... @endphp` | Menjalankan kod PHP dalam templat Blade. |
| `{{ $variable }}` | Mencetak data dengan `escaping` untuk keselamatan. |
| `{!! $variable !!}` | Mencetak data tanpa `escaping` (berhati-hati dengan suntikan skrip). |
| `@verbatim ... @endverbatim` | Mencegah Blade daripada mengeksekusi kod dalam blok tersebut. |

---

Dengan menggunakan direktif ini, anda boleh menguruskan kod PHP dalam Blade dengan lebih fleksibel dan selamat. 🚀
