# **Pengurusan Versi dengan Git**

## **Pengenalan**
Git ialah sistem kawalan versi teragih yang membolehkan pembangun menjejaki perubahan dalam kod, bekerjasama dengan orang lain, dan mengekalkan sejarah projek mereka. Dalam sesi ini, kita akan meneroka asas Git, perintah biasa, dan cara menggunakan GitHub untuk projek Laravel.

---

## **Persediaan Git**
1. **Pasang Git**:
    - Muat turun dan pasang Git dari [https://git-scm.com/](https://git-scm.com/).
    - Sahkan pemasangan:
      ```bash
      git --version
      ```

2. **Konfigurasi Git**:
   Tetapkan nama pengguna dan e-mel untuk komit Git:
   ```bash
   git config --global user.name "Nama Anda"
   git config --global user.email "emelanda@example.com"
   ```

---

## **Aliran Kerja Asas Git**
1. **Inisialisasi Repositori Git**:
   Navigasi ke direktori projek Laravel anda dan inisialisasikan Git:
   ```bash
   git init
   ```

2. **Periksa Status Repositori**:
   Lihat perubahan dalam repositori anda:
   ```bash
   git status
   ```

3. **Tambah Fail ke Kawasan Staging**:
   Tambah fail tertentu atau semua fail ke kawasan staging:
   ```bash
   git add filename
   git add .
   ```

4. **Komit Perubahan**:
   Simpan perubahan ke repositori dengan mesej:
   ```bash
   git commit -m "Komit awal"
   ```

5. **Lihat Sejarah Komit**:
   Periksa log komit:
   ```bash
   git log
   ```

---

## **Bekerja dengan Cawangan (Branching)**
1. **Cipta Cawangan Baru**:
   ```bash
   git branch nama_cawangan
   ```

2. **Tukar ke Cawangan Lain**:
   ```bash
   git checkout nama_cawangan
   ```

3. **Gabung Cawangan**:
   Gabungkan satu cawangan ke dalam cawangan semasa:
   ```bash
   git merge nama_cawangan
   ```

4. **Padam Cawangan**:
   ```bash
   git branch -d nama_cawangan
   ```

---

## **Menggunakan GitHub**
1. **Cipta Repositori GitHub**:
    - Pergi ke [GitHub](https://github.com/) dan cipta repositori baharu.

2. **Sambungkan Repositori Tempatan ke GitHub**:
   Tambah URL repositori jauh:
   ```bash
   git remote add origin https://github.com/nama_pengguna/nama_repositori.git
   ```

3. **Tolak Perubahan ke GitHub**:
   Hantar komit tempatan anda ke GitHub:
   ```bash
   git push -u origin main
   ```

4. **Tarik Perubahan dari GitHub**:
   Kemas kini repositori tempatan anda dengan perubahan terkini:
   ```bash
   git pull origin main
   ```

---

## **Bekerjasama dengan Git**
1. **Klon Repositori**:
   Klon repositori sedia ada dari GitHub:
   ```bash
   git clone https://github.com/nama_pengguna/nama_repositori.git
   ```

2. **Cipta Pull Request**:
    - Buat perubahan dalam cawangan baharu.
    - Tolak cawangan tersebut ke GitHub.
    - Buka pull request di GitHub untuk semakan.

3. **Selesaikan Konflik Penggabungan**:
   Jika dua perubahan bercanggah, Git akan memaklumkan anda. Selesaikan konflik dalam fail dan kemudian:
   ```bash
   git add .
   git commit -m "Selesaikan konflik gabungan"
   git push
   ```

---

## **Tugasan Praktikal**
1. Inisialisasi repositori Git dalam projek Laravel anda.
2. Buat beberapa perubahan pada projek anda dan komitkan.
3. Tolak projek anda ke repositori GitHub baharu.
4. Cipta cawangan baharu untuk satu ciri (contoh: `feature/tambah-login`) dan buat perubahan.
5. Gabungkan cawangan ciri tersebut kembali ke cawangan `main`.
6. Klon repositori ke komputer atau direktori lain.

---

## **Kesimpulan**
Dalam sesi ini, kita telah belajar asas kawalan versi menggunakan Git dan cara bekerjasama menggunakan GitHub. Git membantu menjejaki perubahan, bekerjasama dengan pasukan, dan mengekalkan sejarah projek dengan bersih.

