kamu bisa menjalankan migrasi yang hanya ada di folder `field_scanning` dengan beberapa pendekatan, tergantung bagaimana struktur proyek Laravel kamu diatur. Berikut adalah beberapa cara yang bisa kamu gunakan:

### 1. **Menjalankan Migrasi dengan Kelas Secara Spesifik:**

Jika kamu tahu nama kelas migrasi yang ada di folder `field_scanning`, kamu bisa menjalankan migrasi tersebut secara spesifik menggunakan perintah `migrate` dengan `--path` atau dengan menentukan nama kelas secara langsung:

```bash
php artisan migrate --path=database/migrations/field_scanning/2024_08_14_000000_create_field_scanning_table.php
```

Jika ada lebih dari satu file migrasi di dalam folder `field_scanning`, kamu bisa menjalankan perintah di atas untuk setiap file migrasi.

### 2. **Menjalankan Semua Migrasi dalam Folder Tertentu:**

Jika semua file migrasi berada dalam satu folder `field_scanning`, kamu bisa menjalankan semua migrasi di dalam folder tersebut dengan perintah berikut:

```bash
php artisan migrate --path=/database/migrations/field_scanning
```

### 3. **Membuat dan Menjalankan `Migration Batch`:**

Jika kamu memiliki banyak file migrasi dalam folder `field_scanning`, dan ingin menjalankan mereka dalam satu batch, kamu bisa mempertimbangkan untuk membuat migrasi baru yang menggabungkan semua perubahan di dalam folder `field_scanning` dan kemudian menjalankan migrasi tersebut.

### 4. **Menjalankan Migrasi Secara Manual dalam Kode:**

Jika kamu ingin lebih banyak kontrol, kamu bisa membuat command khusus atau script untuk menjalankan migrasi dari folder `field_scanning` saja. Misalnya, dengan menggunakan `DB::unprepared()` dalam command khusus.

### 5. **Penggunaan Perintah Khusus:**

Jika kamu sering melakukan hal ini, kamu juga bisa membuat Artisan command khusus yang secara otomatis hanya menjalankan migrasi dari folder tertentu.

### Contoh Artisan Command:

```php
namespace App\Console\Commands;

use Illuminate\Console\Command;
use Illuminate\Support\Facades\Artisan;

class MigrateFieldScanning extends Command
{
    protected $signature = 'migrate:field-scanning';
    protected $description = 'Run migrations from the field_scanning folder';

    public function handle()
    {
        $this->info('Running migrations from the field_scanning folder...');
        Artisan::call('migrate', ['--path' => 'database/migrations/field_scanning']);
        $this->info('Migrations completed.');
    }
}
```

Setelah menambahkan command di atas, kamu bisa menjalankannya dengan perintah berikut:

```bash
php artisan migrate:field-scanning
```

Dengan menggunakan salah satu dari pendekatan di atas, kamu bisa fokus menjalankan migrasi yang hanya ada di folder `field_scanning`.

## CREATE MIGRATION

Ya, Anda bisa membuat file migrasi di folder tertentu menggunakan perintah:

```bash
php artisan make:migration create_table_field_scanning_problematic_vehicles --create=field_scanning_problematic_vehicles --path=/database/migrations/field_scanning
```

Perintah ini akan membuat file migrasi di folder `database/migrations/field_scanning`.

Pastikan direktori `field_scanning` sudah ada di dalam jalur `database/migrations/`; jika tidak, Laravel akan menampilkan error. Jika direktori tersebut belum ada, Anda bisa membuatnya sebelum menjalankan perintah:

```bash
mkdir -p database/migrations/field_scanning
```

## ROLLBACK MIGRATION

Untuk melakukan rollback pada migrasi yang ada di folder tertentu, seperti `field_scanning`, Anda bisa menggunakan perintah berikut:

```bash
php artisan migrate:rollback --path=/database/migrations/field_scanning
```

Perintah ini akan mengembalikan (rollback) hanya migrasi yang berada di folder `field_scanning`, tanpa mempengaruhi migrasi lain di folder default `database/migrations`.

Jadi, jika Anda hanya ingin mengembalikan migrasi yang ada di folder tersebut, pastikan untuk menyertakan opsi `--path` seperti di atas.
