Anda dapat menginstal Node Version Manager (NVM) di CentOS 7 dengan langkah-langkah berikut:

1. **Persiapkan Dependensi**:

   Pastikan Anda telah menginstal beberapa dependensi yang diperlukan sebelum menginstal NVM. Anda memerlukan `curl` dan `git`. Jika belum terpasang, Anda dapat menginstalnya dengan perintah berikut:

   ```bash
   sudo yum install curl git
   ```

2. **Unduh Script Instalasi NVM**:

   Anda dapat mengunduh script instalasi NVM menggunakan `curl`. Pastikan Anda masuk sebagai pengguna yang akan menggunakan NVM (jangan gunakan root).

   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
   ```

   Pastikan untuk memeriksa situs web [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm) untuk versi terbaru dan gantilah URL di atas sesuai versi terbaru.

3. **Aktifkan NVM**:

   Setelah script diunduh dan dijalankan, Anda perlu mengeksekusi perintah berikut di terminal Anda atau masukkan ke dalam file konfigurasi shell (seperti `.bashrc`, `.zshrc`, atau `.profile`):

   ```bash
   source ~/.nvm/nvm.sh
   ```

   Atau Anda dapat menggunakan perintah ini jika Anda menggunakan Bash:

   ```bash
   echo "source ~/.nvm/nvm.sh" >> ~/.bashrc
   source ~/.bashrc
   ```

   Jika Anda menggunakan Zsh, gantilah `.bashrc` dengan `.zshrc`.

4. **Periksa Instalasi NVM**:

   Untuk memeriksa bahwa NVM berhasil diinstal, jalankan perintah berikut:

   ```bash
   nvm --version
   ```

   Ini akan menampilkan versi NVM yang telah diinstal.

5. **Instal Node.js Menggunakan NVM**:

   Setelah menginstal NVM, Anda dapat menginstal Node.js dengan perintah seperti berikut:

   ```bash
   nvm install 16.19.0
   ```

   Perintah di atas akan menginstal versi Node.js terbaru. Anda juga dapat menginstal versi Node.js lainnya dengan menggantikan `node` dengan versi yang diinginkan, misalnya:

   ```bash
   nvm use 16.19.0
   ```

   Anda dapat memeriksa versi Node.js yang diinstal dengan `node -v`.

Sekarang Anda telah berhasil menginstal NVM dan Node.js di CentOS 7 dan dapat mengelola versi Node.js dengan mudah menggunakan NVM.