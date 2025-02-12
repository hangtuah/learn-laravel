# **Laravel Blade Directives: CSRF & Borang (CSRF & Forms)**

Laravel menyediakan mekanisme perlindungan terhadap **Cross-Site Request Forgery (CSRF)** dan memudahkan pengurusan borang dalam Blade. Dengan penggunaan direktif khusus, anda boleh memastikan borang selamat daripada serangan CSRF dan mengawal jenis permintaan HTTP dengan lebih mudah.

---

## **1. Perlindungan CSRF dengan `@csrf`**

Laravel menggunakan **token CSRF** untuk memastikan bahawa permintaan yang dibuat melalui borang datang daripada sumber yang sah.

### **Contoh Penggunaan:**
```blade
<form action="{{ route('submitForm') }}" method="POST">
    @csrf
    <input type="text" name="name" placeholder="Nama">
    <button type="submit">Hantar</button>
</form>
```

🔹 **Penjelasan:**
- `@csrf` akan menambah token CSRF tersembunyi dalam borang.
- Laravel secara automatik akan menyemak token ini apabila borang dihantar untuk menghalang serangan CSRF.

Jika token CSRF tidak disertakan dalam borang, Laravel akan menolak permintaan tersebut.

---

## **2. Menentukan Jenis Permintaan HTTP dengan `@method`**

Kadangkala, anda perlu menggunakan kaedah HTTP seperti `PUT`, `PATCH`, atau `DELETE` dalam borang. Laravel tidak menyokong kaedah ini secara langsung dalam elemen `<form>`, tetapi anda boleh menggunakan `@method` untuk menyatakan kaedah yang ingin digunakan.

### **Contoh Penggunaan `@method` dalam Borang:**
```blade
<form action="{{ route('updateProfile') }}" method="POST">
    @csrf
    @method('PUT')
    <input type="text" name="name" value="{{ $user->name }}">
    <button type="submit">Kemas Kini</button>
</form>
```

🔹 **Penjelasan:**
- `@method('PUT')` menambah input tersembunyi dengan nilai `PUT`, membolehkan Laravel mengesan permintaan sebagai `PUT`.
- Ini penting apabila mengemas kini data dalam Laravel menggunakan RESTful routes.

---

## **3. Menggunakan `route()` dalam Borang**

Anda boleh menjana URL secara dinamik dalam atribut `action` menggunakan `route()`.

### **Contoh Penggunaan:**
```blade
<form action="{{ route('deleteUser', ['id' => $user->id]) }}" method="POST">
    @csrf
    @method('DELETE')
    <button type="submit" onclick="return confirm('Anda pasti ingin memadam?')">Padam</button>
</form>
```

🔹 **Penjelasan:**
- `route('deleteUser', ['id' => $user->id])` akan menjana URL berdasarkan laluan dinamakan dalam `routes/web.php`.
- `@csrf` melindungi borang daripada serangan CSRF.
- `@method('DELETE')` memastikan Laravel mengenali permintaan sebagai permintaan `DELETE`.
- `onclick="return confirm('Anda pasti ingin memadam?')"` menambah pengesahan sebelum menghantar borang.

---

## **Ringkasan**

| Direktif | Keterangan |
|-----------|------------|
| `@csrf` | Menambah token CSRF ke dalam borang untuk perlindungan terhadap serangan CSRF. |
| `@method('PUT')` | Menentukan kaedah HTTP seperti `PUT`, `PATCH`, atau `DELETE` dalam borang. |
| `route('route.name')` | Menjana URL berdasarkan nama laluan dalam Laravel. |

---

Dengan menggunakan direktif ini, anda boleh memastikan borang dalam Laravel lebih selamat dan mematuhi prinsip RESTful dengan mudah. 🚀
