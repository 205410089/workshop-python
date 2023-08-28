PEP-249, dokumentasi psycopg, PyMongo, SQLAlchemy. Kerjakan dan jelaskan akses ke basis dataCockroachDB
menggunakan psycopg2 dan menggunakan SQLAlchemy
Bangun Aplikasi Python dengan CockroachDB dan psycopg2Langkah 1.
Mulai CockroachDB
Pilih metode instalasi Anda
Anda dapat membuat klaster Tanpa Server CockroachDB menggunakan CockroachDB Cloud Console,alat antarmuka
pengguna grafis (GUI) berbasis web, atau ccloud, alat antarmuka baris perintah (CLI).
Langkah 2. Dapatkan kode contoh
git clone https://github.com/cockroachlabs/hello-world-python-psycopg2Kode sampel dalam
example.pymelakukan hal berikut:
Membuat accountstabel dan menyisipkan beberapa barisTransfer
dana antara dua akun di dalam transaksi
Menghapus akun dari tabel sebelum keluar sehingga Anda dapat menjalankan kembali kode contoh
Untuk menangani kesalahan percobaan ulang transaksi , kode menggunakan loop percobaan ulangtingkat aplikasi 
yang, jika terjadi kesalahan, akan tidur sebelum mencoba transfer dana lagi. Jika menemukan kesalahan coba lagi, ia 
tidur untuk interval yang lebih lama, menerapkan backoff eksponensial .
Untuk menginstal psycopg2-binary, jalankan perintah berikut:pip install
psycopg2-binary
Langkah 4. Jalankan kode
=> Setel DATABASE_URLvariabel lingkungan ke string koneksi ke klaster Anda:export
DATABASE_URL="{connection-string}"
Di mana {connection-string}string koneksi yang Anda salin sebelumnya.
Aplikasi menggunakan string koneksi yang disimpan ke DATABASE_URLvariabel lingkungan untukterhubung ke
klaster Anda dan menjalankan kode
