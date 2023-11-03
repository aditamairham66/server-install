Untuk menginstall ulang Apache HTTP Server (httpd) yang sudah ada di CentOS 7, Anda dapat mengikuti langkah-langkah berikut:

1. Buka terminal atau SSH ke server CentOS 7 Anda.

2. Pastikan Anda memiliki akses root atau memiliki izin sudo. Jika tidak, Anda perlu masuk sebagai pengguna root atau menggunakan sudo untuk menjalankan perintah-perintah berikut.

3. Hentikan layanan httpd yang sedang berjalan (jika sedang berjalan) dengan perintah:

   ```
   systemctl stop httpd
   ```

4. Untuk menghapus paket httpd yang sudah ada, Anda bisa menggunakan perintah `yum remove`:

   ```
   yum remove httpd
   ```

   Perintah ini akan menghapus Apache HTTP Server beserta konfigurasi dan file-file yang terkait.

5. Setelah menghapus Apache HTTP Server, Anda dapat menginstalnya kembali dengan perintah `yum install`:

   ```
   yum install httpd
   ```

6. Setelah instalasi selesai, Anda dapat memulai ulang layanan httpd dengan perintah:

   ```
   systemctl start httpd
   ```

7. Anda juga dapat mengaktifkan layanan httpd agar otomatis berjalan setiap kali sistem boot dengan perintah:

   ```
   systemctl enable httpd
   ```

8. Periksa apakah Apache HTTP Server telah berjalan dengan benar dengan membuka browser web Anda dan mengunjungi alamat IP server CentOS atau nama domain jika ada. Misalnya, `http://alamat-ip-server` atau `http://nama-domain`.

Sekarang Anda telah berhasil menginstal ulang Apache HTTP Server di CentOS 7. Pastikan untuk memeriksa konfigurasi dan file-file situs web Anda yang mungkin telah terpengaruh oleh proses reinstallasi ini.