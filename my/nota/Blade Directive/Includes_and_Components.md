# **Laravel Blade Directives: Includes & Components**
Blade menyediakan cara mudah untuk menyertakan fail lain dan menggunakan komponen yang boleh diguna semula. Ini membantu dalam mengekalkan kebersihan dan pengurusan kod dalam templat Laravel.

---

## **1. Menyertakan Paparan (Including Views)**

Laravel membolehkan anda memasukkan paparan lain ke dalam fail Blade menggunakan `@include`.

### **Contoh Penggunaan `@include`**
```blade
@include('header')
```

Anda juga boleh menghantar data ke paparan yang dimasukkan:
```blade
@include('header', ['title' => 'Laman Utama'])
```

Jika paparan yang disertakan tidak wujud, anda boleh menggunakan `@includeIf` untuk mengelakkan ralat:
```blade
@includeIf('sidebar')
```

---

## **2. Komponen (Components)**

Komponen Blade membolehkan anda mencipta elemen UI yang boleh diguna semula. Ini sangat berguna untuk bahagian laman seperti butang, kad, atau amaran.

### **Contoh Komponen Blade**
#### **1. Mencipta Fail Komponen**
Buat fail komponen di dalam direktori `resources/views/components/button.blade.php`:
```blade
<button class="btn btn-primary">
    {{ $slot }}
</button>
```

#### **2. Menggunakan Komponen dalam Blade**
```blade
<x-button>
    Klik Saya
</x-button>
```

#### **3. Komponen dengan Atribut**
```blade
<x-button type="submit" class="btn-success">
    Hantar
</x-button>
```

Untuk mengendalikan atribut dalam komponen:
```blade
<button {{ $attributes->merge(['class' => 'btn btn-primary']) }}>
    {{ $slot }}
</button>
```

---

## **3. Blade Layouts**

Blade menyediakan sistem layout yang memudahkan penggunaan templat utama dan menjadikan kod lebih tersusun.

### **3.1 Menggunakan `@extends` dan `@section`**
Dalam Laravel, anda boleh mewarisi susun atur utama menggunakan `@extends` dan menentukan bahagian tertentu dengan `@section`.

#### **Contoh Fail Susun Atur Utama (`layouts/master.blade.php`)**
```blade
<!DOCTYPE html>
<html>
<head>
    <title>@yield('title')</title>
</head>
<body>
    <header>
        @include('header')
    </header>
    <main>
        @yield('content')
    </main>
    <footer>
        @include('footer')
    </footer>
</body>
</html>
```

#### **Contoh Fail Paparan (`home.blade.php`)**
```blade
@extends('layouts.master')

@section('title', 'Halaman Utama')

@section('content')
    <h1>Selamat Datang ke Halaman Utama</h1>
@endsection
```

### **3.2 Menggunakan `@yield` untuk Kandungan Dinamik**
`@yield` membolehkan anda menentukan bahagian yang boleh diisi oleh fail Blade lain.

### **3.3 Menggunakan `@push` dan `@stack` untuk Skrip atau CSS Tambahan**
Kadangkala anda ingin menambah skrip atau gaya tersuai dalam halaman tertentu sahaja. Gunakan `@push` dan `@stack`:

#### **Dalam Fail Templat (`layouts/master.blade.php`)**
```blade
<head>
    @stack('styles')
</head>
<body>
    @stack('scripts')
</body>
```

#### **Dalam Fail Paparan (`home.blade.php`)**
```blade
@push('styles')
    <link rel="stylesheet" href="custom.css">
@endpush

@push('scripts')
    <script src="custom.js"></script>
@endpush
```

---

## **Ringkasan**
| Direktif | Keterangan |
|-----------|------------|
| `@include('view')` | Menyertakan fail Blade lain. |
| `@includeIf('view')` | Menyertakan fail Blade jika wujud. |
| `<x-component>` | Menggunakan komponen Blade tersuai. |
| `@extends('layout')` | Mewarisi susun atur utama. |
| `@section('name')` | Menentukan bahagian tertentu dalam layout. |
| `@yield('name')` | Tempat pemegang untuk kandungan dinamik. |
| `@push('stack')` | Menambah kandungan dalam tumpukan tertentu. |
| `@stack('stack')` | Memaparkan kandungan dalam tumpukan. |
