Untuk membuat akses remote ke server MariaDB yang telah diinstal dengan versi 10.4, Anda perlu mengikuti beberapa langkah berikut:

1. Buka Port MariaDB:
   Pastikan port default MariaDB (biasanya 3306) di server Anda sudah terbuka dan diizinkan melalui firewall. Anda perlu mengonfigurasi firewall Anda untuk mengizinkan koneksi ke port ini dari luar server.

2. Konfigurasi my.cnf:
   Anda perlu mengedit file konfigurasi MariaDB (`my.cnf`) di server Anda. Biasanya, file ini berada di `/etc/mysql/my.cnf` atau `/etc/my.cnf`. Buka file ini dengan teks editor, seperti `nano` atau `vim`, dan pastikan baris berikut ada dalam file tersebut:

   ```plaintext
   bind-address = 0.0.0.0
   ```

   Ini akan mengizinkan MariaDB untuk menerima koneksi dari semua alamat IP. Jika Anda ingin membatasi koneksi ke alamat IP tertentu, gantilah `0.0.0.0` dengan alamat IP yang sesuai.

3. Membuat Pengguna Remote:
   Anda perlu membuat pengguna yang dapat terhubung dari jarak jauh ke MariaDB. Anda bisa menggunakan perintah SQL berikut:

   ```sql
   CREATE USER 'nama_pengguna'@'alamat_IP' IDENTIFIED BY 'password';
   GRANT ALL PRIVILEGES ON *.* TO 'nama_pengguna'@'alamat_IP' WITH GRANT OPTION;
   ```

   Gantilah 'nama_pengguna' dengan nama pengguna yang Anda inginkan, 'alamat_IP' dengan alamat IP yang akan diizinkan terhubung, dan 'password' dengan kata sandi yang aman. Pastikan untuk memberikan izin yang sesuai kepada pengguna ini.

4. Terapkan Perubahan dan Restart MariaDB:
   Setelah mengedit file konfigurasi dan membuat pengguna, Anda perlu menerapkan perubahan dengan me-restart layanan MariaDB. Anda bisa melakukannya dengan perintah berikut:

   ```bash
   sudo systemctl restart mariadb
   ```

5. Konfigurasi Firewall:
   Pastikan firewall di server Anda mengizinkan koneksi ke port 3306 (atau port MariaDB yang Anda konfigurasikan) dari alamat IP yang diizinkan.

Sekarang, Anda seharusnya dapat terhubung ke MariaDB dari jarak jauh menggunakan alamat IP server MariaDB, nama pengguna, dan kata sandi yang Anda buat dalam langkah 3. Pastikan untuk menggunakan alamat IP yang diizinkan saat membuat koneksi dari aplikasi atau perangkat jarak jauh Anda ke server MariaDB.


### UNTUK MEMBUKA PORT

Konfigurasi firewall (langkah nomor 5) penting untuk memastikan bahwa lalu lintas ke port MariaDB (biasanya port 3306) diizinkan. Cara Anda mengkonfigurasi firewall akan bergantung pada sistem operasi yang Anda gunakan. Di bawah ini, saya akan memberikan panduan umum untuk Ubuntu/Debian dan CentOS/Fedora:

**Ubuntu/Debian:**

1. Buka terminal atau SSH ke server Anda.

2. Jika Anda menggunakan firewall UFW, Anda dapat memeriksa statusnya terlebih dahulu:

   ```bash
   sudo ufw status
   ```

   Pastikan bahwa port 3306 (atau port MariaDB yang Anda konfigurasikan) sudah diizinkan. Jika belum, Anda bisa mengizinkannya dengan perintah berikut:

   ```bash
   sudo ufw allow 3306/tcp
   ```

   Aktifkan UFW jika belum aktif:

   ```bash
   sudo ufw enable
   ```

3. Periksa status aturan firewall untuk memastikan bahwa perubahan telah diterapkan:

   ```bash
   sudo ufw status
   ```

**CentOS/Fedora:**

1. Buka terminal atau SSH ke server Anda.

2. Jika Anda menggunakan firewalld, Anda dapat memeriksa aturan yang ada terlebih dahulu:

   ```bash
   sudo firewall-cmd --list-all
   ```

   Pastikan bahwa port 3306 (atau port MariaDB yang Anda konfigurasikan) sudah diizinkan. Jika belum, Anda dapat menambahkan izin dengan perintah berikut:

   ```bash
   sudo firewall-cmd --zone=public --add-port=3306/tcp --permanent
   ```

   Kemudian, reload aturan firewall untuk menerapkan perubahan:

   ```bash
   sudo firewall-cmd --reload
   ```

3. Verifikasi bahwa aturan firewall telah diterapkan dengan menjalankan perintah:

   ```bash
   sudo firewall-cmd --list-all
   ```

Setelah mengkonfigurasi firewall, pastikan Anda memiliki izin yang benar dalam MariaDB dan Anda dapat mengaksesnya secara remote. Jika ada masalah, pastikan aturan firewall Anda sudah benar dan tidak menghalangi koneksi ke port MariaDB.