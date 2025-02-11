# **Model, Eloquent ORM dan Operasi CRUD**

## **Pengenalan**
Eloquent ORM (Object-Relational Mapping) ialah ORM umum Laravel yang menyediakan cara mudah dan elegan untuk berinteraksi dengan pangkalan data. Eloquent memetakan jadual pangkalan data kepada model PHP, membolehkan pengendalian data secara intuitif.

---

## **Persediaan Eloquent**
1. **Membuat Model**:
   Cipta model menggunakan Artisan:
   ```bash
   php artisan make:model Student
   ```

2. **Penamaan Model dan Jadual**:
    - Secara umum, Eloquent memetakan nama model (`Student`) kepada jadual `students` (bentuk jamak).
    - Untuk menyesuaikan nama jadual, tetapkan sifat `$table`:
      ```php
      protected $table = 'custom_table_name';
      ```

3. **Sambungan ke Pangkalan Data**:
   Pastikan fail `.env` dikonfigurasi dengan betul untuk sambungan pangkalan data.

---

## **Operasi CRUD Asas dengan Eloquent**

### **1. Cipta (Create)**
Menambah rekod baharu ke dalam pangkalan data:
```php
$student = new Student();
$student->name = 'Ali';
$student->age = 20;
$student->save();
```
Atau menggunakan kaedah `create` (memerlukan `$fillable` dalam model):
```php
protected $fillable = ['name', 'age'];

Student::create([
    'name' => 'Siti',
    'age' => 22
]);
```

### **2. Baca (Read)**
Mendapatkan rekod daripada pangkalan data:
- Semua rekod:
  ```php
  $students = Student::all();
  ```
- Rekod berdasarkan ID:
  ```php
  $student = Student::find(1);
  ```
- Carian dengan syarat:
  ```php
  $students = Student::where('age', '>=', 20)->get();
  ```
- Dapatkan rekod pertama yang sepadan:
  ```php
  $student = Student::where('name', 'Ali')->first();
  ```

### **3. Kemaskini (Update)**
Mengemas kini rekod sedia ada:
```php
$student = Student::find(1);
$student->age = 25;
$student->save();
```
Atau menggunakan kaedah `update`:
```php
Student::where('id', 1)->update(['age' => 26]);
```

### **4. Padam (Delete)**
Menghapuskan rekod daripada pangkalan data:
```php
$student = Student::find(1);
$student->delete();
```
Atau menggunakan kaedah `destroy`:
```php
Student::destroy(1); // Padam berdasarkan ID
Student::destroy([1, 2, 3]); // Padam banyak rekod
```

---

## **Hubungan dalam Eloquent**
Eloquent memudahkan penentuan dan interaksi antara hubungan dalam pangkalan data.

### **1. Hubungan One-to-One**
```php
// Dalam model Student
public function profile()
{
    return $this->hasOne(Profile::class);
}

// Dalam model Profile
public function student()
{
    return $this->belongsTo(Student::class);
}
```

### **2. Hubungan One-to-Many**
```php
// Dalam model Student
public function courses()
{
    return $this->hasMany(Course::class);
}

// Dalam model Course
public function student()
{
    return $this->belongsTo(Student::class);
}
```

### **3. Hubungan Many-to-Many**
```php
// Dalam model Student
public function clubs()
{
    return $this->belongsToMany(Club::class);
}

// Dalam model Club
public function students()
{
    return $this->belongsToMany(Student::class);
}
```

---

## **Tugasan Praktikal**
1. Cipta model `Student` dan migrasi dengan medan berikut:
    - `id`: Primary key
    - `name`: String
    - `age`: Integer
    - `created_at` dan `updated_at`: Timestamps
2. Laksanakan operasi CRUD berikut:
    - Tambah 3 pelajar contoh ke dalam pangkalan data.
    - Dapatkan semua pelajar dan tapis berdasarkan umur tertentu.
    - Kemaskini umur seorang pelajar.
    - Padamkan seorang pelajar tertentu.
3. Tentukan hubungan one-to-many antara `Student` dan `Course`.
4. Gunakan Eloquent untuk mendapatkan senarai kursus bagi pelajar tertentu.

---

## **Kesimpulan**
Dalam sesi ini, kita telah belajar bagaimana menggunakan **Eloquent ORM** untuk melakukan operasi **CRUD** serta menguruskan **hubungan antara jadual** dalam pangkalan data. Kesederhanaan dan fleksibiliti Eloquent menjadikannya alat yang sangat berguna dalam Laravel.

