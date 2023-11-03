Tentu, berikut adalah tahap-tahapnya:

1. **Pastikan Anda Memiliki Izin Administratif:**
   Pastikan Anda menjalankan semua perintah instalasi dengan izin administratif. Anda dapat menggunakan `sudo` untuk mendapatkan izin administratif pada CentOS. Misalnya:
   ```
   sudo yum update
   ```

2. **Perbarui Sistem Anda:**
   Pertama-tama, pastikan sistem Anda diperbarui dengan versi paket terbaru. Ini akan memastikan Anda memiliki versi perangkat lunak dan paket yang paling baru. Jalankan perintah berikut:
   ```
   sudo yum update
   ```

3. **Tambahkan Repositori yang Tepat:**
   Pastikan Anda telah menambahkan repositori yang sesuai untuk menginstal ekstensi SQLSRV PHP. Anda dapat mengunduh dan menambahkan repositori Microsoft dengan perintah `curl` seperti ini:
   ```
   sudo curl -o /etc/yum.repos.d/mssql-release.repo https://packages.microsoft.com/config/rhel/8/prod.repo
   ```

4. **Periksa Dependensi:**
   Pastikan Anda telah menginstal semua dependensi yang diperlukan. Untuk ekstensi SQLSRV, Anda akan memerlukan paket seperti `unixODBC` dan `unixODBC-devel`. Anda dapat menginstalnya dengan perintah berikut:
   ```
   sudo yum install unixODBC unixODBC-devel
   ```

5. **Periksa Pesan Kesalahan:**
   Jika Anda mendapatkan pesan kesalahan saat mencoba menginstal ekstensi SQLSRV, pastikan untuk membacanya dengan cermat. Pesan kesalahan akan memberikan petunjuk tentang masalah yang mungkin ada. Jika ada pesan kesalahan tertentu yang ingin Anda tanyakan, berikan pesan kesalahan tersebut sehingga saya dapat memberikan bantuan lebih lanjut.

Setelah mengikuti langkah-langkah di atas, Anda harus dapat menginstal ekstensi SQLSRV PHP pada CentOS 7 tanpa konflik dengan Maria


### Detail Step No 5

Tentu, langkah nomor 5 adalah tentang mengatasi masalah yang mungkin muncul saat Anda mencoba menginstal ekstensi SQLSRV PHP atau paket-paket terkait. Masalah ini dapat muncul dalam bentuk pesan kesalahan yang memberi tahu Anda mengapa instalasi gagal. Di bawah ini adalah beberapa masalah umum yang mungkin Anda temui dan cara mengatasi mereka:

1. **Tidak Dapat Menemukan Paket atau Repository:**
   - Pastikan Anda sudah menambahkan repositori yang sesuai, seperti yang dijelaskan pada langkah 3.
   - Periksa koneksi internet Anda. Pastikan Anda dapat mengakses repository Microsoft tanpa masalah.
   - Pastikan Anda menggunakan repositori yang sesuai dengan versi CentOS Anda (misalnya, CentOS 7 atau CentOS 8).

2. **Konflik Dependensi:**
   - Jika Anda melihat pesan kesalahan yang mengindikasikan adanya konflik dependensi, Anda mungkin perlu menghapus paket-paket yang menyebabkan konflik tersebut.
   - Periksa apakah paket-paket yang sama dari repositori lain atau pihak ketiga yang terinstal di sistem Anda. Hapus paket-paket konflik tersebut atau coba ganti dengan versi yang sesuai.

3. **Paket Tidak Ditemukan atau Tidak Tersedia:**
   - Pesan kesalahan mungkin menyebutkan bahwa paket yang dicari tidak tersedia. Pastikan Anda telah menambahkan repositori dengan benar.
   - Anda juga dapat mencoba menjalankan `yum clean all` untuk membersihkan cache repository dan kemudian mencoba lagi.

4. **Ketergantungan yang Hilang:**
   - Jika Anda mendapatkan pesan kesalahan yang mencantumkan ketergantungan yang hilang, Anda harus memastikan semua ketergantungan terpenuhi. Ini termasuk paket seperti `unixODBC` dan `unixODBC-devel`. Instal ketergantungan yang hilang sebelum mencoba menginstal ekstensi SQLSRV.

5. **Versi PHP yang Tidak Cocok:**
   - Pastikan bahwa versi PHP yang terinstal cocok dengan versi ekstensi SQLSRV yang Anda coba instal. Versi PHP Anda harus sesuai dengan versi yang didukung oleh ekstensi tersebut.

6. **Firewall atau Izin Jaringan:**
   - Pastikan firewall Anda tidak memblokir koneksi ke repositori atau server yang Anda butuhkan untuk mengunduh paket-paket tersebut.

7. **Lainnya:**
   - Ada banyak masalah yang mungkin muncul selama instalasi. Baca pesan kesalahan dengan cermat dan, jika perlu, cari di internet untuk menemukan solusi yang sesuai dengan masalah Anda.

Setiap pesan kesalahan yang muncul selama proses instalasi akan memberikan petunjuk yang berguna untuk memecahkan masalah. Jika Anda menghadapi masalah tertentu atau pesan kesalahan tertentu, berikan informasi lebih lanjut, dan saya akan mencoba memberikan panduan lebih rinci untuk mengatasinya.

Di CentOS 7, Anda dapat menginstal ekstensi SQLSRV untuk PHP dengan beberapa langkah tambahan. Berikut adalah langkah-langkahnya:

1. Pastikan Anda telah mengaktifkan repositori Microsoft dan menginstal ODBC Driver, seperti yang telah dijelaskan sebelumnya.

2. Buka terminal atau SSH ke server Anda.

3. Instal ekstensi SQLSRV menggunakan `pecl`. Jalankan perintah berikut:

   ```bash
   sudo pecl install sqlsrv
   ```

   Jika Anda belum menginstal `pecl`, Anda dapat menginstalnya terlebih dahulu dengan perintah:

   ```bash
   sudo yum install php-pear
   ```

4. Setelah instalasi selesai, Anda perlu mengaktifkan ekstensi SQLSRV dalam konfigurasi PHP. Buat file konfigurasi untuk ekstensi SQLSRV dengan perintah berikut:

   ```bash
   echo "extension=sqlsrv.so" | sudo tee /etc/php.d/sqlsrv.ini
   ```

   Pastikan Anda mengganti `sqlsrv.ini` sesuai dengan versi PHP yang Anda gunakan. Anda dapat memeriksa versi PHP dengan perintah `php -v`.

5. Selanjutnya, Anda perlu memuat ekstensi SQLSRV. Jalankan perintah berikut:

   ```bash
   sudo phpenmod sqlsrv
   ```

6. Untuk menerapkan perubahan tersebut, Anda perlu me-restart PHP-FPM. Jalankan perintah ini:

   ```bash
   sudo systemctl restart php-fpm
   ```

7. Terakhir, pastikan Anda memeriksa apakah ekstensi SQLSRV telah diaktifkan dengan menjalankan perintah:

   ```bash
   php -m | grep sqlsrv
   ```

   Jika Anda melihat `sqlsrv` dalam daftar ekstensi yang diaktifkan, maka ekstensi ini telah berhasil diinstal pada PHP di CentOS 7.

Pastikan Anda memiliki izin sudo untuk menjalankan perintah ini, dan pastikan juga Anda telah memasang ODBC Driver seperti yang disebutkan dalam langkah-langkah sebelumnya.


### NOTE: Jika ada masalah dengan libtool
#### INSTALL LIBTOOL
Pesan kesalahan yang Anda sebutkan menunjukkan bahwa kompilasi ekstensi `sqlsrv` gagal karena tidak dapat menemukan pustaka `-lltdl`. Masalah ini berkaitan dengan pustaka yang dibutuhkan oleh `libtool` selama proses kompilasi.

Untuk mengatasi masalah ini, Anda perlu menginstal pustaka yang diperlukan. Pustaka `-lltdl` adalah bagian dari pustaka GNU Libtool. Berikut adalah langkah-langkah yang dapat Anda ikuti untuk mengatasi masalah ini:

1. Instal pustaka GNU Libtool:

   ```bash
   sudo yum install libtool
   ```

2. Setelah Anda menginstal pustaka GNU Libtool, coba kembali proses instalasi ekstensi `sqlsrv` dengan `pecl`:

   ```bash
   sudo pecl install sqlsrv
   ```

Pastikan untuk menjalankan perintah instalasi `pecl` sebagai superuser (sudo).

Setelah Anda menginstal `libtool`, Anda seharusnya tidak lagi melihat kesalahan yang berkaitan dengan `-lltdl`. Ini akan memungkinkan kompilasi ekstensi `sqlsrv` berhasil. Jika Anda masih mengalami masalah, pastikan juga Anda telah menginstal semua ketergantungan yang dibutuhkan seperti yang disebutkan sebelumnya.

#### INSTALL LIBTOOL-DEVEL
Masalah ekstraksi dengan `libtool` mungkin disebabkan oleh beberapa faktor. Saya akan memberikan beberapa langkah yang dapat Anda coba untuk mengatasi masalah ini:

1. Pastikan bahwa Anda memiliki semua dependensi yang diperlukan terinstal dengan benar, seperti yang disebutkan dalam langkah-langkah sebelumnya.

2. Cobalah menjalankan perintah berikut sebelum mencoba menginstal SQL Server PHP extensions:

   ```
   sudo dnf install libtool-ltdl-devel
   ```

   Ini akan menginstal paket pengembangan libtool yang mungkin dibutuhkan oleh proses kompilasi.

3. Setelah itu, Anda dapat mencoba lagi untuk menginstal `sqlsrv` extension:

   ```
   sudo pecl install -f sqlsrv
   ```

4. Jika masalah masih terjadi, Anda mungkin ingin mencoba menggunakan perintah `pecl` sebagai pengguna root atau menggunakan `sudo` untuk menjalankannya. Terkadang, masalah ekstraksi dan kompilasi perangkat lunak tertentu dapat terkait dengan hak akses atau lingkungan pengguna.

Jika setelah langkah-langkah ini Anda masih mengalami masalah, harap berikan informasi lebih lanjut tentang pesan kesalahan yang Anda terima sehingga saya dapat memberikan bantuan yang lebih tepat.