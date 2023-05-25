
8. Kesalahan dan Pengecualian : 
Sampai saat ini pesan kesalahan belum banyak disebutkan, tetapi jika Anda telah mencoba contoh-contohnya, Anda mungkin telah melihat beberapa. Ada (setidaknya) dua jenis kesalahan yang dapat dibedakan: kesalahan sintaks dan pengecualian .

8.1. Kesalahan Sintaks :
Kesalahan sintaksis, juga dikenal sebagai kesalahan parsing, mungkin merupakan jenis keluhan paling umum yang Anda dapatkan saat masih mempelajari Python:
Parser mengulangi baris yang menyinggung dan menampilkan 'panah' kecil yang menunjuk ke titik paling awal di baris tempat kesalahan terdeteksi. Kesalahan disebabkan oleh (atau setidaknya terdeteksi pada) token yang mendahului tanda panah: dalam contoh, kesalahan terdeteksi pada fungsi print(), karena titik dua ( ':') tidak ada sebelumnya. Nama file dan nomor baris dicetak sehingga Anda tahu ke mana harus mencari jika input berasal dari skrip.

8.2. Pengecualian : 
Bahkan jika sebuah pernyataan atau ekspresi benar secara sintaksis, itu dapat menyebabkan kesalahan ketika upaya dilakukan untuk mengeksekusinya. Kesalahan yang terdeteksi selama eksekusi disebut pengecualian dan tidak fatal tanpa syarat: Anda akan segera belajar cara menanganinya dalam program Python. Namun, sebagian besar pengecualian tidak ditangani oleh program, dan menghasilkan pesan kesalahan seperti yang ditampilkan di sini:
Baris terakhir dari pesan kesalahan menunjukkan apa yang terjadi. Pengecualian datang dalam berbagai jenis, dan jenisnya dicetak sebagai bagian dari pesan: jenis dalam contoh adalah ZeroDivisionError, NameErrordan TypeError. String yang dicetak sebagai tipe pengecualian adalah nama dari pengecualian bawaan yang terjadi. Ini berlaku untuk semua pengecualian bawaan, tetapi tidak harus benar untuk pengecualian yang ditentukan pengguna (walaupun ini adalah konvensi yang berguna). Nama pengecualian standar adalah pengidentifikasi bawaan (bukan kata kunci yang dicadangkan).
Baris selanjutnya memberikan detail berdasarkan jenis pengecualian dan apa yang menyebabkannya.
Bagian sebelumnya dari pesan kesalahan menunjukkan konteks di mana pengecualian terjadi, dalam bentuk stack traceback. Secara umum ini berisi baris sumber daftar traceback tumpukan; namun, ini tidak akan menampilkan baris yang dibaca dari input standar.

8.3. Menangani Pengecualian  :
Dimungkinkan untuk menulis program yang menangani pengecualian yang dipilih. Lihat contoh berikut, yang meminta input dari pengguna sampai bilangan bulat yang valid telah dimasukkan, tetapi memungkinkan pengguna untuk menginterupsi program (menggunakan atau apa pun yang didukung oleh sistem operasi); perhatikan bahwa interupsi yang dibuat pengguna ditandai dengan memunculkan pengecualian .Control-CKeyboardInterrupt

Pertama, klausa try (pernyataan antara trydan exceptkata kunci) dijalankan.
Jika tidak ada pengecualian yang terjadi, kecuali klausa dilewati dan eksekusi pernyataan tryselesai.
Jika pengecualian terjadi selama eksekusi klausa try, klausa lainnya akan dilewati. Kemudian, jika tipenya cocok dengan pengecualian yang dinamai menurut exceptkata kunci, klausa kecuali dieksekusi, dan kemudian eksekusi dilanjutkan setelah blok coba/kecuali.
Jika pengecualian terjadi yang tidak cocok dengan pengecualian yang disebutkan dalam klausa kecuali , itu diteruskan ke trypernyataan luar; jika tidak ada penangan yang ditemukan, itu adalah pengecualian yang tidak tertangani dan eksekusi berhenti dengan pesan seperti yang ditunjukkan di atas.

Perhatikan bahwa jika klausa pengecualian dibalik (dengan yang pertama), itu akan dicetak B, B, B — klausa pengecualian pertama yang cocok dipicu.except B

Ketika pengecualian terjadi, itu mungkin memiliki nilai terkait, juga dikenal sebagai argumen pengecualian . Kehadiran dan jenis argumen bergantung pada jenis pengecualian.
Klausa kecuali dapat menentukan variabel setelah nama pengecualian. Variabel terikat pada instance pengecualian yang biasanya memiliki args atribut yang menyimpan argumen. Untuk kenyamanan, tipe pengecualian bawaan menentukan __str__()untuk mencetak semua argumen tanpa mengakses secara eksplisit .args.

Penggunaan elseklausa lebih baik daripada menambahkan kode tambahan ke tryklausa karena menghindari menangkap pengecualian secara tidak sengaja yang tidak dimunculkan oleh kode yang dilindungi oleh try… exceptpernyataan.

8.4. Menaikkan Pengecualian  :
Satu-satunya argumen untuk raisemenunjukkan pengecualian yang akan diajukan. Ini harus berupa instance pengecualian atau kelas pengecualian (kelas yang berasal dari BaseException, seperti Exceptionatau salah satu subkelasnya). Jika sebuah kelas eksepsi dilewatkan, maka secara implisit akan dibuatkan instance-nya dengan memanggil konstruktornya tanpa argumen:

8.5. Rantai Pengecualian 
Jika pengecualian yang tidak tertangani terjadi di dalam suatu exceptbagian, pengecualian yang ditangani akan dilampirkan padanya dan disertakan dalam pesan kesalahan:

8.6. Pengecualian yang Ditentukan Pengguna 
Program dapat menamai pengecualiannya sendiri dengan membuat kelas pengecualian baru (lihat Kelas untuk informasi lebih lanjut tentang kelas Python). Pengecualian biasanya harus diturunkan dari Exceptionkelas, baik secara langsung maupun tidak langsung.

Kelas pengecualian dapat didefinisikan yang melakukan apa pun yang dapat dilakukan kelas lain, tetapi biasanya tetap sederhana, seringkali hanya menawarkan sejumlah atribut yang memungkinkan informasi tentang kesalahan diekstraksi oleh penangan untuk pengecualian.
Sebagian besar pengecualian ditentukan dengan nama yang diakhiri dengan "Kesalahan", mirip dengan penamaan pengecualian standar.
Banyak modul standar menentukan pengecualian mereka sendiri untuk melaporkan kesalahan yang mungkin terjadi pada fungsi yang mereka tentukan.

8.7. Mendefinisikan Tindakan Pembersihan 
Pernyataan tersebut trymemiliki klausa opsional lain yang dimaksudkan untuk menentukan tindakan

ika finallyada klausa, finally klausa tersebut akan dieksekusi sebagai tugas terakhir sebelum try pernyataan selesai. Klausa finallyberjalan apakah trypernyataan menghasilkan pengecualian atau tidak. Poin-poin berikut membahas kasus yang lebih kompleks ketika pengecualian terjadi:

Jika pengecualian terjadi selama eksekusi klausa try , pengecualian dapat ditangani oleh except klausa. Jika pengecualian tidak ditangani oleh except klausa, pengecualian akan dimunculkan kembali setelah finally klausa dieksekusi.

Pengecualian bisa terjadi selama eksekusi except atau elseklausa. Sekali lagi, pengecualian dimunculkan kembali setelah finallyklausa dieksekusi.

Jika finallyklausa mengeksekusi break, continueatau returnpernyataan, pengecualian tidak dimunculkan kembali.

Jika trypernyataan mencapai break, continueatau returnpernyataan, finallyklausa akan dieksekusi tepat sebelum break, continueatau return eksekusi pernyataan.

Jika finallyklausa menyertakan return pernyataan, nilai yang dikembalikan akan menjadi nilai dari pernyataan finallyklausa return, bukan nilai dari pernyataan tryklausa return .

Seperti yang Anda lihat, finallyklausa dijalankan dalam peristiwa apa pun. Dibesarkan TypeErrordengan membagi dua string tidak ditangani oleh exceptklausa dan oleh karena itu dimunculkan kembali setelah finally klausa dieksekusi.

Dalam aplikasi dunia nyata, finallyklausa ini berguna untuk melepaskan sumber daya eksternal (seperti file atau koneksi jaringan), terlepas dari keberhasilan penggunaan sumber daya tersebut.

8.8. Tindakan Pembersihan Standar 
Beberapa objek menentukan tindakan pembersihan standar yang harus dilakukan saat objek tidak lagi diperlukan, terlepas dari apakah operasi menggunakan objek berhasil atau gagal. Lihat contoh berikut, yang mencoba membuka file dan mencetak isinya ke layar.

8.9. Menaikkan dan Menangani Beberapa Pengecualian yang Tidak Terkait 
Ada situasi di mana perlu melaporkan beberapa pengecualian yang telah terjadi. Ini sering terjadi dalam kerangka kerja konkurensi, ketika beberapa tugas mungkin gagal secara paralel, tetapi ada juga kasus penggunaan lain yang diinginkan untuk melanjutkan eksekusi dan mengumpulkan banyak kesalahan daripada memunculkan pengecualian pertama.

Builtin ExceptionGroupmembungkus daftar instance pengecualian sehingga dapat dimunculkan bersama. Ini adalah pengecualian itu sendiri, sehingga dapat ditangkap seperti pengecualian lainnya.

Dengan menggunakan except*alih-alih except, kita hanya dapat menangani pengecualian dalam grup yang cocok dengan tipe tertentu secara selektif. Dalam contoh berikut, yang memperlihatkan grup pengecualian bersarang, setiap except*klausa mengekstrak dari pengecualian grup dari jenis tertentu sambil membiarkan semua pengecualian lainnya menyebar ke klausa lain dan akhirnya dinaikkan kembali.

8.10. Memperkaya Pengecualian dengan Catatan 
Saat pengecualian dibuat untuk dimunculkan, biasanya diinisialisasi dengan informasi yang menjelaskan kesalahan yang terjadi. Ada kasus di mana berguna untuk menambahkan informasi setelah pengecualian tertangkap. Untuk tujuan ini, pengecualian memiliki metode add_note(note)yang menerima string dan menambahkannya ke daftar catatan pengecualian. Render traceback standar menyertakan semua catatan, sesuai urutan penambahannya, setelah pengecualian.

Misalnya, saat mengumpulkan pengecualian ke dalam grup pengecualian, kami mungkin ingin menambahkan informasi konteks untuk setiap kesalahan. Berikut ini setiap pengecualian dalam grup memiliki catatan yang menunjukkan kapan kesalahan ini terjadi.



