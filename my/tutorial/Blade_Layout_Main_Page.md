# **Tutorial: Menjadikan Template HTML sebagai Layout Laravel**

## **1. Pengenalan**
Dalam tutorial ini, kita akan menukar satu halaman HTML yang besar kepada **Laravel Blade Layout** yang modular menggunakan `@yield`, `@include`, `@extends`, `@push`, dan `@stack`. Ini akan membantu kita menguruskan template dengan lebih baik.

## **2. Struktur Fail dalam Laravel**
Selepas pemecahan layout, fail-fail berikut akan diwujudkan dalam **`resources/views/layouts/`**:

```
/resources/views/layouts/app.blade.php     →  Fail utama (layout keseluruhan)
/resources/views/layouts/header.blade.php  →  Header (Top Navigation)
/resources/views/layouts/sidebar.blade.php →  Sidebar (Menu kiri)
/resources/views/layouts/footer.blade.php  →  Footer (Bawah)
```

Setiap halaman baru akan **meletakkan kandungan dalam section `@section('content')`** dan menggunakan layout ini dengan `@extends('layouts.app')`.

---

## **3. Membina Layout Utama (`app.blade.php`)**
Fail **`resources/views/layouts/app.blade.php`** akan menjadi layout utama:

```blade
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
    <title>@yield('title', 'Dashboard')</title>
    <link href="{{ asset('css/styles.css') }}" rel="stylesheet">
    <link rel="icon" type="image/x-icon" href="{{ asset('assets/img/favicon.png') }}">
    @stack('styles')
</head>
<body class="nav-fixed">
    @include('layouts.header')
    <div id="layoutSidenav">
        @include('layouts.sidebar')
        <div id="layoutSidenav_content">
            <main>
                @yield('content')
            </main>
            @include('layouts.footer')
        </div>
    </div>
    <script src="{{ asset('js/scripts.js') }}"></script>
    @stack('scripts')
</body>
</html>
```

---

## **4. Membina Header (`header.blade.php`)**
Fail **`resources/views/layouts/header.blade.php`**:

```blade
<nav class="topnav navbar navbar-expand shadow navbar-light bg-white" id="sidenavAccordion">
    <a class="navbar-brand ps-3" href="#">SB Admin Pro</a>
    <button class="btn btn-icon btn-transparent-dark" id="sidebarToggle"><i data-feather="menu"></i></button>
</nav>
```

---

## **5. Membina Sidebar (`sidebar.blade.php`)**
Fail **`resources/views/layouts/sidebar.blade.php`**:

```blade
<div id="layoutSidenav_nav">
    <nav class="sidenav shadow-right sidenav-light">
        <div class="sidenav-menu">
            <div class="nav accordion" id="accordionSidenav">
                <div class="sidenav-menu-heading">Core</div>
                <a class="nav-link" href="#">
                    <div class="nav-link-icon"><i data-feather="home"></i></div>
                    Dashboard
                </a>
            </div>
        </div>
    </nav>
</div>
```

---

## **6. Membina Footer (`footer.blade.php`)**
Fail **`resources/views/layouts/footer.blade.php`**:

```blade
<footer class="footer-admin mt-auto footer-light">
    <div class="container-xl px-4">
        <div class="row">
            <div class="col-md-6 small">Copyright &copy; Your Website 2021</div>
            <div class="col-md-6 text-md-end small">
                <a href="#">Privacy Policy</a>
                &middot;
                <a href="#">Terms & Conditions</a>
            </div>
        </div>
    </div>
</footer>
```

---

## **7. Cara Menggunakan Layout dalam Halaman Lain**
Setiap halaman baru akan menggunakan layout utama dengan `@extends('layouts.app')`.
Sebagai contoh, untuk fail **`resources/views/dashboard.blade.php`**:

```blade
@extends('layouts.app')

@section('title', 'Dashboard')

@section('content')
<div class="container-fluid px-4">
    <h1 class="mt-4">Dashboard</h1>
    <p>Selamat datang ke dashboard.</p>
</div>
@endsection
```

---

## **8. Kesimpulan**
Kita telah berjaya menukar satu halaman HTML yang besar kepada **Laravel Blade Layout** yang modular dengan pemisahan **header, sidebar, footer, dan content**. Ini memudahkan penyelenggaraan dan meningkatkan kebersihan kod. 🚀

