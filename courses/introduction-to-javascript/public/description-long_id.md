# Pengenalan ke Blockchain

## Apa itu Blockchain?

![Gambar](/markdown/photo_01.jpg)

Secara inti, blockchain adalah buku besar terdistribusi—sejenis basis data yang berisi catatan transaksi, yang disimpan di banyak komputer di seluruh dunia. Berbeda dengan basis data tradisional, blockchain menyimpan data dalam blok yang terhubung (atau dirantai) satu sama lain. Setiap blok berisi daftar transaksi, dan begitu blok selesai, blok tersebut ditambahkan ke rantai dengan pengidentifikasi yang menghubungkannya ke blok sebelumnya.

(Gambar di sini)

Berikut adalah beberapa konsep kunci:

- **Desentralisasi:** Alih-alih dikelola oleh satu otoritas (seperti bank sentral), blockchain dipelihara oleh jaringan komputer, yang dikenal sebagai node, yang bekerja bersama untuk membuat, memvalidasi, dan menyimpan transaksi dalam blok.
- **Immutabilitas:** Begitu transaksi tercatat di blockchain, hampir tidak mungkin untuk mengubah atau menghapusnya.
- **Transparansi:** Setiap transaksi melibatkan pengirim dan penerima yang diidentifikasi oleh alamat publik. Meskipun identitas asli dari alamat ini mungkin tidak diketahui secara publik, siapa pun dapat memeriksa buku besar untuk melihat semua transaksi yang terkait dengan alamat manapun.

Ada beberapa blockchain yang berbeda yang ada. Beberapa nama yang paling dikenal termasuk Bitcoin, Ethereum, Solana, Polygon, dan XRP. Masing-masing memiliki tujuan unik, yang akan kita jelajahi lebih lanjut di pelajaran berikutnya.

## Kasus Penggunaan Blockchain

Mari kita mulai dengan kasus penggunaan yang paling jelas—cryptocurrency. Ide asli di balik Bitcoin, jaringan blockchain pertama, adalah untuk memungkinkan transfer nilai tanpa perlu otoritas pusat. Otoritas pusat—seperti bank, perusahaan kartu kredit, atau layanan pembayaran online—dapat campur tangan dalam transaksi, menundanya hingga kondisi tertentu terpenuhi, atau dalam kasus ekstrem, menyensor transaksi sepenuhnya. Blockchain, teknologi yang mendasari Bitcoin dan cryptocurrency lainnya, memungkinkan transaksi desentralisasi yang tidak memerlukan izin dan dapat dikirim dari mana saja di dunia ke mana saja dalam hitungan detik.

Kasus penggunaan besar lainnya adalah **smart contract**, sebuah konsep yang dipelopori oleh Ethereum, blockchain kedua yang paling dikenal. Ethereum dirancang untuk memungkinkan pengembang membuat aplikasi terdesentralisasi (dApps) yang berjalan di blockchain-nya. Aplikasi-aplikasi ini, yang dikenal sebagai smart contract, dapat berkisar dari daftar tugas sederhana hingga sistem keuangan kompleks (dikenal sebagai DeFi—Decentralized Finance), cryptocurrency kustom, token, permainan online, dan bahkan koleksi seni di blockchain.

Basis data blockchain juga semakin digunakan di berbagai industri, termasuk [asuransi](https://www.ingwb.com/en/insights/distributed-ledger-technology/blockchain-technology), [pemrosesan pembayaran](https://www.paypal.com/us/digital-wallet/manage-money/crypto/pyusd), dan manajemen rantai pasokan. Karena blockchain membuat hampir mustahil untuk mengubah catatan transaksi setelah ditambahkan ke rantai, banyak perusahaan menggunakannya untuk melacak pergerakan barang dari pabrik ke gudang, dan akhirnya ke toko-toko tempat pelanggan membelinya.

Namun, bagaimana kita bisa sampai ke tahap yang maju ini? Mari kita mundur sedikit dan jelajahi asal-usul blockchain.

## Bagaimana Semua Bermula

Konsep mata uang terdesentralisasi sudah ada sejak beberapa waktu lalu. Sejak tahun 1990-an, sekelompok penggemar kriptografi dan privasi, yang dikenal sebagai [cypherpunks](https://en.wikipedia.org/wiki/Cypherpunk), membagikan ide-ide mereka melalui mailing list, yang merupakan pendahulu forum diskusi online modern.

Pada tahun 2008, salah satu anggota komunitas ini, yang dikenal dengan nama samaran **Satoshi Nakamoto**, memposting makalah penelitian berjudul “Bitcoin: A Peer-to-Peer Electronic Cash System.” Makalah ini menguraikan jenis mata uang digital baru yang dapat dipindahkan langsung antar pengguna tanpa perlu otoritas pusat. Beberapa bulan kemudian, Satoshi mewujudkan teori ini dan meluncurkan Bitcoin, mata uang digital terdesentralisasi pertama.

Hingga saat ini, identitas asli Satoshi Nakamoto masih menjadi misteri. Apakah itu satu orang, atau sekelompok orang? Kami tidak tahu. Nama Satoshi Nakamoto umum di Jepang, mirip dengan "John Smith" di negara-negara berbahasa Inggris. Meskipun ada petunjuk yang menunjukkan bahwa orang ini memiliki pengetahuan tinggi tentang matematika terapan dan bahasa pemrograman C++, dan mungkin beroperasi di zona waktu Amerika, identitas definitif belum pernah ditetapkan. Pada tahun 2013, Satoshi membuat pos terakhirnya dan menghilang dari peredaran.

Selama bertahun-tahun, beberapa individu mengklaim diri mereka sebagai Satoshi, namun tidak ada yang memberikan bukti kriptografi yang meyakinkan komunitas—yaitu, menandatangani pesan dengan dompet asli Satoshi.

Meski Satoshi menghilang, jaringan Bitcoin terus berkembang sejak diluncurkan pada 2009. Sekarang didukung oleh puluhan ribu node, dan seluruh industri bernilai triliunan dolar telah dibangun di atas Bitcoin.

## Bitcoin: Blockchain Pertama

Konsep di balik penggunaan Bitcoin cukup sederhana. Anda menginstal perangkat lunak khusus yang membuat dompet untuk Anda dan menghubungkan ke jaringan. Tidak perlu mendaftar atau memberikan informasi pribadi—Anda dapat langsung mulai mengirim dan menerima pembayaran.

Di balik layar, dompet Anda terdiri dari **alamat publik** dan **kunci pribadi**. Untuk menerima pembayaran, Anda membagikan alamat publik Anda kepada pengirim. Untuk mengirim pembayaran, Anda menggunakan kunci pribadi Anda, yang berfungsi seperti kata sandi panjang dan aman. Kunci pribadi ini begitu kompleks sehingga hampir mustahil untuk ditebak orang lain dan biasanya disimpan dalam file yang aman.

Ketika Anda mengirim transaksi, transaksi tersebut disiarkan ke jaringan dan didistribusikan ke semua node sebagai transaksi **tertunda**. Transaksi-transaksi tertunda ini kemudian diambil oleh **penambang Bitcoin**, yang menggunakan komputer canggih untuk memecahkan persamaan matematika yang kompleks untuk membuat blok baru. Seperti yang disebutkan sebelumnya, setiap blok berisi daftar transaksi, yang mungkin termasuk transaksi Anda.

Penambang mendapatkan hadiah untuk pekerjaan mereka dengan dua cara:
1. Jaringan Bitcoin mengeluarkan BTC baru untuk setiap blok yang dihasilkan oleh penambang.
2. Mereka menerima biaya transaksi yang dibayar pengguna untuk mengirim transaksi mereka.

Saat ini, banyak **penyedia online** yang memungkinkan Anda untuk membuat dompet Bitcoin, mengelola kunci pribadi Anda, dan mengirim transaksi atas nama Anda, tanpa perlu menjalankan perangkat lunak khusus. Karena regulasi hukum, layanan ini mungkin memerlukan verifikasi ID, tetapi banyak dari mereka yang ramah pengguna, aman, dan terpercaya. Beberapa penyedia yang paling terkenal termasuk [Binance](https://www.binance.com/) dan [Coinbase](https://www.coinbase.com/). Pada tahun 2024, Bitcoin semakin mengukuhkan posisinya di dunia keuangan ketika perusahaan keuangan tradisional, seperti BlackRock, mulai menawarkan produk berbasis Bitcoin, seperti ETF Bitcoin.

## Ada Banyak Blockchain

Meskipun Bitcoin adalah blockchain pertama, itu jauh dari satu-satunya. Sejak peluncurannya, banyak jaringan blockchain telah dikembangkan, masing-masing dengan fitur dan kasus penggunaan unik.

- **Ethereum:** Ethereum memperkenalkan smart contract, yang memungkinkan pengembang membuat dApps yang berjalan di blockchain Ethereum. Inovasi ini membuka dunia kemungkinan, dari pengelolaan token hingga permainan online dan banyak lagi.

- **Solana:** Diluncurkan beberapa tahun setelah Ethereum, Solana mengatasi beberapa keterbatasan Ethereum. Sementara Ethereum membutuhkan lebih dari 10 detik untuk menghasilkan setiap blok (yang tidak ideal untuk transaksi cepat seperti membeli kopi), Solana telah mengurangi waktu produksi blok menjadi hanya 0,2 detik.

- **Lisk:** Sementara Solana sangat dioptimalkan, bisa menjadi tantangan bagi pengembang untuk membuat aplikasi di platformnya, yang membatasi potensi basis penggunanya. Lisk, di antara jaringan lainnya, membangun teknologi Ethereum tetapi memperkenalkan perubahan untuk membuat jaringannya lebih mudah diakses oleh pengembang dan pengguna. Jaringan seperti Lisk sering disebut sebagai “Jaringan Lapisan 2” (L2), dengan Ethereum berfungsi sebagai “Jaringan Lapisan 1.”

Apakah Anda ingin belajar lebih lanjut tentang jaringan blockchain ini? Anda beruntung karena bagian selanjutnya akan membahas Ethereum. Namun, ketika datang untuk mempelajari pemrograman dan memahami bahasa Solidity milik Ethereum, kita perlu mengetahui dasar-dasar Javascript.

Mari kita mulai dengan mempelajari dasar-dasar Javascript menggunakan lingkungan pengembangan interaktif.
