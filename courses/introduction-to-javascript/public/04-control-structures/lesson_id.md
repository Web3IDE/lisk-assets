## Struktur Kontrol

Bagian penting dalam membangun aplikasi sering kali adalah mengkondisikan perilaku aplikasi. Dengan kata lain, menampilkan output yang berbeda - atau melakukan tugas yang berbeda - berdasarkan nilai dari input.

Misalnya, Anda memiliki seorang pengguna dengan hak istimewa admin, dan Anda ingin memungkinkan mereka untuk melakukan tugas tertentu, misalnya menulis artikel blog baru. Tapi Anda tidak ingin sembarang orang yang bisa memposting artikel baru - hanya admin yang bisa melakukannya.

Kita bisa memvalidasi sebuah kondisi menggunakan pernyataan `if`. Jika pengguna memiliki hak istimewa admin, biarkan mereka memposting artikel. Jika tidak - tampilkan pesan kesalahan.

Dan jika kita ingin menggabungkan beberapa validasi, kita bisa menggabungkan kondisi dengan pernyataan `else if`.

Dalam contoh ini, kita memvalidasi apakah sebuah angka lebih kecil atau lebih besar dari 5. Bagian pertama dari kondisi `if (number < 5)` akan mengeksekusi blok yang dibungkus dalam kurung kurawal (`{` dan `}`) hanya jika kondisi ini terpenuhi (nilai `number` lebih kecil dari `5`).

Jika kondisi tersebut tidak terpenuhi (`number` **bukan** lebih kecil dari `5`), kode akan melanjutkan untuk memvalidasi kondisi kedua, dalam hal ini `else if (number > 5)`. Sekali lagi, jika kondisi ini terpenuhi (`number` lebih besar dari `5`), kita mengeksekusi blok berikutnya yang dibungkus dalam kurung kurawal (`{` dan `}`).

Tugas Anda adalah untuk memperluas set kondisi ini dan menambahkan kondisi ketiga yang memvalidasi apakah `number` **sama dengan** `5`.

## Latihan

- Selesaikan fungsi `buildMessage()`. Jika `number` sama dengan lima, kembalikan pesan `Number equals 5`.
