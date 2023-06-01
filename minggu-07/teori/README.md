9. Kelas 
Kelas menyediakan sarana bundling data dan fungsionalitas bersama. Membuat kelas baru akan membuat tipe objek baru, yang memungkinkan instance baru dari tipe tersebut dibuat. Setiap instance kelas dapat memiliki atribut yang melekat padanya untuk mempertahankan statusnya. Instance kelas juga dapat memiliki metode (ditentukan oleh kelasnya) untuk memodifikasi statusnya.
Dibandingkan dengan bahasa pemrograman lain, mekanisme kelas Python menambahkan kelas dengan sintaks dan semantik baru yang minimal. Ini adalah campuran dari mekanisme kelas yang ditemukan di C++ dan Modula-3. Kelas Python menyediakan semua fitur standar Pemrograman Berorientasi Objek: mekanisme pewarisan kelas memungkinkan banyak kelas dasar, kelas turunan dapat mengganti metode apa pun dari kelas atau kelas dasarnya, dan metode dapat memanggil metode kelas dasar dengan nama yang sama . Objek dapat berisi jumlah dan jenis data yang sewenang-wenang. Seperti halnya modul, kelas mengambil bagian dari sifat dinamis Python: mereka dibuat saat runtime, dan dapat dimodifikasi lebih lanjut setelah dibuat.
Dalam terminologi C++, biasanya anggota kelas (termasuk anggota data) bersifat publik (kecuali lihat di bawah Private Variables ), dan semua fungsi anggota bersifat virtual . Seperti di Modula-3, tidak ada singkatan untuk mereferensikan anggota objek dari metodenya: fungsi metode dideklarasikan dengan argumen pertama yang eksplisit yang mewakili objek, yang disediakan secara implisit oleh panggilan. Seperti di Smalltalk, kelas itu sendiri adalah objek. Ini menyediakan semantik untuk mengimpor dan mengganti nama. Tidak seperti C++ dan Modula-3, tipe bawaan dapat digunakan sebagai kelas dasar untuk ekstensi oleh pengguna. Juga, seperti di C++, sebagian besar operator bawaan dengan sintaks khusus (operator aritmatika, subskrip, dll.) dapat didefinisikan ulang untuk instance kelas.
(Kurangnya terminologi yang diterima secara universal untuk berbicara tentang kelas, saya akan sesekali menggunakan istilah Smalltalk dan C++. Saya akan menggunakan istilah Modula-3, karena semantik berorientasi objeknya lebih dekat dengan Python daripada C++, tetapi saya berharap bahwa beberapa pembaca

Tentu saja, __init__()metode tersebut mungkin memiliki argumen untuk fleksibilitas yang lebih besar. Dalam hal ini, argumen yang diberikan kepada operator instansiasi kelas diteruskan ke __init__(). Misalnya,

9.3.5. Variabel Kelas dan Instance 
Secara umum, variabel instan untuk data unik untuk setiap instans dan variabel kelas untuk atribut dan metode yang digunakan bersama oleh semua instans kelas:

Seperti yang dibahas dalam A Word About Names and Objects , data yang dibagikan mungkin memiliki efek mengejutkan dengan melibatkan objek yang dapat berubah seperti daftar dan kamus. Misalnya, daftar trik dalam kode berikut tidak boleh digunakan sebagai variabel kelas karena hanya satu daftar yang akan digunakan bersama oleh semua instance Anjing :

Desain kelas yang benar harus menggunakan variabel instan sebagai gantinya:
9.4. Keterangan Acak ¶
Jika nama atribut yang sama muncul di kedua instance dan di kelas, maka pencarian atribut akan memprioritaskan instance tersebut

Gaya akses ini jelas, ringkas, dan nyaman. Penggunaan iterator meliputi dan menyatukan Python. Di belakang layar, forpernyataan itu memanggil iter()objek kontainer. Fungsi mengembalikan objek iterator yang mendefinisikan metode __next__()yang mengakses elemen dalam wadah satu per satu. Ketika tidak ada lagi elemen, __next__()munculkan StopIterationpengecualian yang memberi tahu forloop untuk diakhiri. Anda dapat memanggil __next__()metode menggunakan next()fungsi bawaan; contoh ini menunjukkan cara kerjanya:

9.10. Ekspresi Generator 
Beberapa generator sederhana dapat dikodekan secara ringkas sebagai ekspresi menggunakan sintaks yang mirip dengan pemahaman daftar tetapi dengan tanda kurung, bukan tanda kurung siku. Ekspresi ini dirancang untuk situasi di mana generator langsung digunakan oleh fungsi penutup. Ekspresi generator lebih kompak tetapi kurang fleksibel daripada definisi generator lengkap dan cenderung lebih ramah memori daripada pemahaman daftar yang setara.
