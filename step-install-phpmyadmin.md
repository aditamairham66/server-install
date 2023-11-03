Untuk menginstal MySQL Server dan phpMyAdmin di CentOS 7, Anda dapat mengikuti langkah-langkah berikut:

### Instal MySQL Server:

1. Buka terminal di CentOS 7.

2. Jalankan perintah berikut untuk menginstal MySQL Server:

   ```
   sudo yum install mysql-server
   ```

3. Setelah instalasi selesai, jalankan perintah berikut untuk memulai layanan MySQL dan mengaktifkannya agar dijalankan secara otomatis setiap kali sistem dinyalakan:

   ```
   sudo systemctl start mysqld
   sudo systemctl enable mysqld
   ```

4. Setelah MySQL Server dijalankan, Anda dapat menjalankan perintah berikut untuk mengamankan instalasi MySQL dan mengikuti instruksi yang ada:

   ```
   sudo mysql_secure_installation
   ```

### Instal phpMyAdmin:

1. Buka terminal di CentOS 7.

2. Jalankan perintah berikut untuk menginstal phpMyAdmin:

   ```
   sudo yum install epel-release
   sudo yum install phpmyadmin
   ```

3. Selama instalasi, Anda akan diminta untuk mengonfigurasi phpMyAdmin. Anda perlu memilih server web yang akan digunakan oleh phpMyAdmin. Pilih server web yang sesuai dengan kebutuhan Anda, misalnya Apache.

4. Setelah instalasi selesai, Anda perlu mengedit berkas konfigurasi Apache untuk mengizinkan akses ke phpMyAdmin. Edit berkas `/etc/httpd/conf.d/phpMyAdmin.conf`:

   ```
   sudo nano /etc/httpd/conf.d/phpMyAdmin.conf
   ```

   Kemudian, temukan baris berikut:

   ```
   Require ip 127.0.0.1
   ```

   Gantilah dengan:

   ```
   Require all granted
   ```

5. Setelah mengedit konfigurasi, jalankan perintah berikut untuk memulai Apache dan mengaktifkannya agar dijalankan secara otomatis setiap kali sistem dinyalakan:

   ```
   sudo systemctl start httpd
   sudo systemctl enable httpd
   ```

6. Terakhir, buka browser Anda dan akses phpMyAdmin melalui alamat `http://localhost/phpmyadmin` atau alamat yang sesuai dengan konfigurasi server web Anda.

Sekarang, Anda sudah berhasil menginstal MySQL Server dan phpMyAdmin di CentOS 7 dan dapat menggunakannya untuk mengelola basis data MySQL Anda. Pastikan untuk mengamankan instalasi MySQL dan phpMyAdmin dengan baik dan mengikuti praktik keamanan yang sesuai.