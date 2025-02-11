## Apa itu Laravel?

Laravel adalah alat yang membantu pembangun membina laman web dan aplikasi web dengan lebih mudah. Ia ditulis dalam PHP, iaitu bahasa pengaturcaraan yang digunakan untuk mencipta laman web dinamik. Laravel dicipta oleh Taylor Otwell pada tahun 2011 dan terkenal kerana kesederhanaan, kecekapan, serta kemampuannya yang hebat.

---

## Ciri Utama Laravel

Berikut adalah beberapa ciri utama yang menjadikan Laravel pilihan terbaik:

1. **Arkitektur MVC**: Laravel menyusun kod anda kepada Model, View, dan Controller untuk memastikan kod lebih tersusun dan mudah diurus.
2. **Eloquent ORM**: Laravel memudahkan interaksi dengan pangkalan data menggunakan kod yang lebih mudah difahami berbanding SQL biasa.
3. **Blade Templating Engine**: Membantu dalam membina reka bentuk laman web yang boleh digunakan semula dengan lebih mudah.
4. **Artisan CLI**: Alat baris perintah yang membantu dalam tugas seperti penciptaan fail dan migrasi pangkalan data.
5. **Sistem Pengesahan Terbina Dalam**: Laravel menyediakan sistem untuk menguruskan log masuk pengguna, pendaftaran, dan peranan dengan lebih mudah.
6. **Ekosistem yang Kaya**: Laravel menawarkan banyak alat tambahan seperti Laravel Nova (panel admin) dan Laravel Passport (keselamatan API).

---

## Alat Pembangunan

Untuk mula menggunakan Laravel, anda memerlukan alat berikut:

### 1. PHP

- Laravel memerlukan PHP versi 8.3 atau lebih tinggi.

### 2. Composer

- Composer adalah alat yang menguruskan pakej (perpustakaan) yang diperlukan oleh Laravel. Anda boleh memuat turunnya dari [https://getcomposer.org/](https://getcomposer.org/).

### 3. Pelayan Tempatan

- Laravel memerlukan pelayan untuk berjalan. Anda boleh menggunakan alat seperti:
    - **XAMPP** (Windows/Mac/Linux)
    - **Laragon** (Windows)
    - **MAMP** (Mac)

### 4. Penyunting Kod

- Penyunting kod digunakan untuk menulis kod Laravel. Beberapa pilihan yang popular termasuk:
    - **Visual Studio Code** (percuma)
    - **PHPStorm** (berbayar, sangat berguna untuk PHP)
    - **Sublime Text** (percuma/cubaan)

---
## Panduan Pemasangan

Berikut adalah panduan pemasangan untuk menyediakan alat yang diperlukan bagi pembangunan Laravel:

1. [Panduan Pemasangan XAMPP](../../notes/installation-guides/install-xampp-windows.md)
2. [Panduan Pemasangan Composer](../../notes/installation-guides/install-composer-windows.md)
3. [Panduan Pemasangan Visual Studio Code](../../notes/installation-guides/install-vscode-windows.md)
4. [Panduan Pemasangan Git Bash](../../notes/installation-guides/install-gitbash-windows.md)
5. [Panduan Pemasangan NPM](../../notes/installation-guides/install-npm-windows.md)

---

## Pemasangan Laravel

Ikuti langkah berikut untuk memasang Laravel dan memilih versi yang anda inginkan:

1. Pasang Laravel menggunakan Composer:
   ```bash
   composer create-project --prefer-dist laravel/laravel nama_projek "^10.0"
   ```
2. Jalankan pelayan Laravel:
    ```bash
    php artisan serve
    ```
3. Buka http://localhost:8000 dalam pelayar web anda untuk melihat projek Laravel anda.

