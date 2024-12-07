## JavaScript Asinkron

Karena JS mampu berinteraksi dengan situs web lain, file lokal, dan berbagai sumber daya eksternal, terkadang Anda perlu menunggu sebelum sumber daya tersebut diproses.

Misalnya, saat Anda ingin membaca teks dari situs web eksternal. Meskipun biasanya hanya memakan waktu kurang dari satu detik, waktu ini digunakan untuk membangun koneksi dengan situs web dan mengunduh teks agar aplikasi Anda dapat membacanya. Kita bisa membuat aplikasi kita **menunggu** agar teks tersebut tersedia, sehingga kita bisa memprosesnya nanti.

Dalam kode contoh berikut, Anda dapat melihat kata kunci `await`. Ini menandakan bahwa kita sedang menunggu agar file sepenuhnya dibaca dan isinya dikembalikan ke aplikasi kita. Kami telah menyertakan modul JS bawaan `fs` (filesystem) yang berisi fungsi `readFileSync()`. Fungsi ini membaca file lokal dari sistem yang sama tempat aplikasi dijalankan, dan kemudian mengembalikan isinya. Tetapi karena operasi ini tidak instan, kita perlu menunggu agar selesai.

Tidak mungkin menggunakan kata kunci `await` di sembarang tempat. Kita perlu menggunakannya dalam fungsi `async` - kata kunci ini menandakan **asinkron**. Fungsi `async` memberi tahu mesin JS bahwa kita mengharapkan untuk menunggu sumber daya eksternal diproses.

Lalu, bagaimana cara Anda membedakan kapan kita perlu menunggu agar suatu operasi selesai (dengan kata lain, kapan menggunakan kata kunci `await`) dan kapan tidak? Aturan praktisnya adalah bahwa setiap kali Anda berinteraksi dengan sumber daya yang tidak ada dalam kode JS Anda, Anda perlu menunggu agar itu diproses. Baik itu file lokal seperti dalam contoh ini atau situs web di internet.

## Latihan

- Bacalah isi file lokal `./greeting.text` dengan memberikan jalur file ke fungsi `readFileSync()`. Halaman [dokumentasi](https://nodejs.org/api/fs.html#fsreadfilesyncpath-options) juga mungkin berguna.
