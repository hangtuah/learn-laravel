
# Laravel, PHP, SQL, and Web Development Terms

This list explains common terms used in Laravel, PHP, SQL, and web development. Each term includes an explanation, and some have analogies or examples.

---

## Laravel Terms

### **1. Artisan**
**English**: Laravel’s command-line tool for performing tasks like starting a server or creating files.  
**Bahasa Malaysia**: Alat baris arahan Laravel untuk menjalankan tugas seperti memulakan pelayan atau mencipta fail.

**Example/Contoh**:  
Command to start a server:
```bash
php artisan serve
```  

---

### **2. Middleware**
**English**: Code that runs between a user’s request and the response. Often used for authentication.  
**Bahasa Malaysia**: Kod yang berjalan antara permintaan pengguna dan tindak balas. Biasanya digunakan untuk pengesahan.

**Analogy/Analogi**: Seperti pengawal keselamatan yang memeriksa kad pengenalan sebelum anda dibenarkan masuk ke dalam bangunan.

---

### **3. Blade**
**English**: Laravel’s templating engine for generating dynamic HTML pages.  
**Bahasa Malaysia**: Enjin templat Laravel untuk menghasilkan halaman HTML yang dinamik.

**Example/Contoh**:  
Fail Blade (`welcome.blade.php`):
```html
<h1>Selamat Datang, {{ $name }}</h1>
```

---

### **4. Eloquent**
**English**: Laravel’s ORM (Object-Relational Mapping) to interact with the database using models.  
**Bahasa Malaysia**: ORM Laravel untuk berinteraksi dengan pangkalan data menggunakan model.

**Analogy/Analogi**: Seperti pelayan restoran yang menterjemahkan pesanan pelanggan kepada dapur dan membawa makanan kembali kepada pelanggan.

---

### **5. Migration**
**English**: A file that defines changes to the database structure, like creating or updating tables.  
**Bahasa Malaysia**: Fail yang menentukan perubahan pada struktur pangkalan data, seperti mencipta atau mengemaskini jadual.

**Example/Contoh**:
```php
Schema::create('users', function (Blueprint $table) {
    $table->id();
    $table->string('name');
});
```

---

## PHP Terms

### **6. Variable**
**English**: A container for storing data, like numbers or text.  
**Bahasa Malaysia**: Bekas untuk menyimpan data seperti nombor atau teks.

**Example/Contoh**:
```php
$name = "Ali";
$age = 25;
```

---

### **7. Array**
**English**: A data structure that stores multiple values in one variable.  
**Bahasa Malaysia**: Struktur data yang menyimpan pelbagai nilai dalam satu pembolehubah.

**Example/Contoh**:
```php
$fruits = ["Epal", "Pisang", "Ceri"];
```

---

### **8. Class**
**English**: A blueprint for creating objects in object-oriented programming.  
**Bahasa Malaysia**: Rangka untuk mencipta objek dalam pengaturcaraan berorientasikan objek.

**Example/Contoh**:
```php
class Kereta {
    public $jenama;
    public function hidupkanEnjin() {
        return "Enjin dihidupkan";
    }
}
```

---

## SQL Terms

### **9. Query**
**English**: A request sent to the database to fetch or manipulate data.  
**Bahasa Malaysia**: Permintaan kepada pangkalan data untuk mendapatkan atau mengubah data.

**Example/Contoh**:
```sql
SELECT * FROM users;
```

---

### **10. Primary Key**
**English**: A unique identifier for each record in a table.  
**Bahasa Malaysia**: Pengecam unik untuk setiap rekod dalam jadual.

**Analogy/Analogi**: Seperti nombor kad pengenalan.

---

### **11. Foreign Key**
**English**: A column that links one table to another.  
**Bahasa Malaysia**: Lajur yang menghubungkan satu jadual dengan jadual lain.

**Analogy/Analogi**: Seperti pasport yang menghubungkan seseorang dengan negara asalnya.

---

## General Web Development Terms

### **12. HTTP**
**English**: The protocol for communication between a browser and a server.  
**Bahasa Malaysia**: Protokol untuk komunikasi antara pelayar dan pelayan.

**Example/Contoh**:  
Apabila anda melawat `www.example.com`, pelayar anda menghantar permintaan HTTP kepada pelayan.

---

### **13. JSON**
**English**: A lightweight data format often used in APIs to transfer data.  
**Bahasa Malaysia**: Format data ringan yang sering digunakan dalam API untuk memindahkan data.

**Example/Contoh**:
```json
{
    "nama": "Ali",
    "umur": 30
}
```

---

### **14. Authentication**
**English**: The process of verifying a user’s identity (e.g., logging in).  
**Bahasa Malaysia**: Proses mengesahkan identiti pengguna (contohnya, log masuk).

**Analogy/Analogi**: Seperti menggunakan kunci untuk membuka pintu rumah.

---

### **15. Cache**
**English**: Temporary storage to make data retrieval faster.  
**Bahasa Malaysia**: Storan sementara untuk mempercepatkan pengambilan data.

**Example/Contoh**:  
Laravel boleh menggunakan cache untuk menyimpan keputusan kueri yang kerap digunakan untuk meningkatkan prestasi.

---

## Summary
This list provides explanations in both **English** and **Bahasa Malaysia**, with examples or analogies to make the terms easier to understand. Knowing these terms will help you navigate Laravel and related technologies confidently. 🚀
