Untuk meng-upgrade MariaDB pada server CentOS 7 dari versi yang lebih lama (misalnya 5.5) ke versi yang lebih baru, Anda dapat mengikuti langkah-langkah berikut:

1. **Buat Cadangan Data**:

   Sebelum Anda mulai melakukan upgrade, sangat penting untuk mencadangkan semua data dan konfigurasi yang ada. Pastikan Anda telah mencadangkan semua basis data dan file konfigurasi yang diperlukan. Anda dapat menggunakan perintah `mysqldump` untuk mencadangkan basis data Anda.

2. **Hapus Versi Lama**:

   Hentikan layanan MariaDB terlebih dahulu:

   ```bash
   sudo systemctl stop mariadb
   ```

   Kemudian hapus paket-paket MariaDB versi lama:

   ```bash
   sudo yum remove mariadb-server mariadb-client
   ```

3. **Tambahkan Repositori MariaDB Baru**:

   Untuk menginstal versi MariaDB yang lebih baru, Anda perlu menambahkan repositori MariaDB yang sesuai dengan versi CentOS Anda. Misalnya, untuk CentOS 7, Anda dapat menggunakan repositori MariaDB 10.4. Gantilah `<version>` dengan versi yang sesuai:

   ```bash
   sudo vi /etc/yum.repos.d/MariaDB.repo
   ```

   Kemudian tambahkan berikut ini ke berkas tersebut:

   ```ini
   [mariadb]
   name = MariaDB
   baseurl = http://yum.mariadb.org/<version>/centos7-amd64
   gpgkey = https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
   gpgcheck = 1
   ```

   Simpan dan keluar dari editor.

4. **Instal MariaDB Baru**:

   Sekarang, Anda dapat menginstal MariaDB versi yang lebih baru dari repositori yang baru ditambahkan:

   ```bash
   sudo yum install MariaDB-server MariaDB-client
   ```

5. **Mulai dan Aktifkan Layanan MariaDB**:

   Setelah instalasi selesai, mulai layanan MariaDB dan aktifkan otomatis pada boot:

   ```bash
   sudo systemctl start mariadb
   sudo systemctl enable mariadb
   ```

6. **Upgrade Basis Data (jika diperlukan)**:

   Jika Anda memiliki basis data yang dibuat dengan versi lama MariaDB, Anda mungkin perlu menjalankan skrip upgrade basis data. Perintah berikut akan membantu Anda mengeksekusi upgrade basis data jika diperlukan:

   ```bash
   mysql_upgrade -u root -p
   ```

   Anda akan diminta memasukkan kata sandi akun root MariaDB.

7. **Periksa Versi MariaDB Baru**:

   Periksa versi MariaDB yang baru terinstal dengan perintah `mysql --version` atau masuk ke MariaDB dan jalankan `SELECT VERSION();`.

Dengan ini, Anda seharusnya telah berhasil meng-upgrade MariaDB ke versi yang lebih baru di server CentOS 7 Anda. Pastikan untuk memeriksa dokumentasi MariaDB atau situs web MariaDB untuk informasi lebih lanjut tentang versi tertentu yang Anda ingin instal.