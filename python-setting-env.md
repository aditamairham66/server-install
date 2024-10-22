Untuk memeriksa apakah Python sudah aktif di dalam virtual environment (venv), kamu bisa mengikuti langkah-langkah berikut:

1. **Aktifkan Virtual Environment**:
   - Di Windows:
     ```bash
     .\venv\Scripts\activate
     ```
   - Di macOS/Linux:
     ```bash
     source venv/bin/activate
     ```

2. **Periksa Versi Python**:
   Setelah virtual environment diaktifkan, jalankan perintah berikut untuk memastikan Python yang sedang digunakan berasal dari virtual environment:
   ```bash
   python --version
   ```

   Output-nya akan menampilkan versi Python yang aktif. Jika virtual environment telah diaktifkan dengan benar, kamu akan menggunakan Python dari direktori `venv`.

3. **Periksa Lokasi Python**:
   Kamu juga bisa memeriksa lokasi Python yang sedang digunakan dengan perintah:
   ```bash
   which python
   ```
   atau di Windows:
   ```bash
   where python
   ```

   Jika virtual environment aktif, output-nya akan menunjukkan path yang berada di dalam folder `venv`.

### Untuk memastikan:
- Jika perintah di atas merujuk ke path di dalam folder `venv`, maka Python di virtual environment sudah aktif.
