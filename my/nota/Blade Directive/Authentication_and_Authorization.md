# **Laravel Blade Directives: Authentication & Authorization**

Laravel menyediakan direktif Blade khas untuk menguruskan **Pengesahan (Authentication)** dan **Kebenaran (Authorization)** dalam templat. Ini membolehkan anda menampilkan atau menyembunyikan kandungan berdasarkan status log masuk pengguna atau keizinan yang diberikan.

---

## **1. Pengesahan (Authentication)**

Blade menyediakan beberapa cara untuk mengawal tampilan berdasarkan status log masuk pengguna.

### **1.1 Menggunakan `@auth` dan `@guest`**
- `@auth` digunakan untuk memaparkan kandungan jika pengguna sudah log masuk.
- `@guest` digunakan untuk memaparkan kandungan kepada pelawat yang belum log masuk.

#### **Contoh Penggunaan:**
```blade
@auth
    <p>Selamat datang, {{ auth()->user()->name }}!</p>
@endauth

@guest
    <p>Sila log masuk untuk mengakses kandungan ini.</p>
@endguest
```
🔹 **Penjelasan:**
- Jika pengguna log masuk, mesej selamat datang dipaparkan.
- Jika pengguna tidak log masuk, mesej meminta mereka untuk log masuk dipaparkan.

### **1.2 Menyemak Pengguna Log Masuk dengan `@if`**
Anda juga boleh menyemak status pengguna dengan `@if(auth()->check())`.

```blade
@if(auth()->check())
    <p>Anda sudah log masuk sebagai {{ auth()->user()->name }}.</p>
@endif
```

---

## **2. Kebenaran (Authorization)**

Laravel membolehkan anda mengawal akses kepada kandungan berdasarkan keizinan tertentu yang diberikan kepada pengguna.

### **2.1 Menggunakan `@can` dan `@cannot`**
- `@can` digunakan untuk memeriksa sama ada pengguna mempunyai keizinan tertentu.
- `@cannot` digunakan untuk menyemak jika pengguna **tidak** mempunyai keizinan tertentu.

#### **Contoh Penggunaan:**
```blade
@can('edit-articles')
    <button>Edit Artikel</button>
@endcan

@cannot('delete-articles')
    <p>Anda tidak mempunyai keizinan untuk memadam artikel.</p>
@endcannot
```
🔹 **Penjelasan:**
- Jika pengguna mempunyai keizinan `edit-articles`, butang "Edit Artikel" akan dipaparkan.
- Jika pengguna tidak mempunyai keizinan `delete-articles`, mesej larangan dipaparkan.

### **2.2 Menggunakan `@canany`**
`@canany` membenarkan semakan keizinan untuk lebih daripada satu keizinan.

```blade
@canany(['edit-articles', 'publish-articles'])
    <button>Urus Artikel</button>
@endcanany
```
🔹 **Penjelasan:**
- Jika pengguna mempunyai salah satu daripada keizinan `edit-articles` atau `publish-articles`, butang akan dipaparkan.

### **2.3 Menggunakan `@role` (Jika Menggunakan Spatie Laravel Permission)**
Jika anda menggunakan pakej **Spatie Laravel Permission**, anda boleh memeriksa peranan pengguna dengan `@role` dan `@endrole`.

```blade
@role('admin')
    <p>Anda adalah pentadbir.</p>
@endrole
```

---

## **Ringkasan**

| Direktif | Keterangan |
|-----------|------------|
| `@auth` | Memaparkan kandungan jika pengguna log masuk. |
| `@guest` | Memaparkan kandungan jika pengguna belum log masuk. |
| `@if(auth()->check())` | Menyemak status log masuk pengguna secara manual. |
| `@can('permission')` | Memaparkan kandungan jika pengguna mempunyai keizinan tertentu. |
| `@cannot('permission')` | Memaparkan kandungan jika pengguna tidak mempunyai keizinan tertentu. |
| `@canany(['perm1', 'perm2'])` | Memaparkan kandungan jika pengguna mempunyai mana-mana keizinan yang dinyatakan. |
| `@role('role')` | Memaparkan kandungan jika pengguna mempunyai peranan tertentu (bergantung kepada pakej Spatie Laravel Permission). |

---

Dengan menggunakan direktif ini, anda boleh mengawal tampilan kandungan berdasarkan status pengguna dan keizinan mereka dengan lebih mudah. 🚀
