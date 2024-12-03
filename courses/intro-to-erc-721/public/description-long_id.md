# Pengantar Non-Fungible Tokens (NFTs)

## Cara Kerja Non-Fungible Tokens (NFTs)

Non-fungible tokens, atau NFT, adalah jenis aset digital yang mewakili kepemilikan suatu **item unik** atau konten di blockchain. Berbeda dengan token fungible (seperti token ERC-20), yang dapat saling dipertukarkan dan memiliki nilai yang sama, sebagian besar NFT bersifat unik dan biasanya tidak dapat dipertukarkan satu lawan satu.

Terdapat beberapa standar untuk NFT, tetapi yang pertama dan paling sering digunakan adalah **ERC-721**. Oleh karena itu, istilah **token ERC-721** sering digunakan sebagai sinonim untuk NFT.

NFT biasanya dirilis dalam kelompok yang memiliki makna serupa — kelompok ini disebut **koleksi**. Misalnya, Anda dapat memiliki NFT yang merepresentasikan gambar kucing oleh satu penulis dalam satu koleksi, dan NFT yang merepresentasikan gambar anjing oleh penulis lain dalam koleksi yang berbeda. Salah satu koleksi yang terkenal adalah **Bored Ape Yacht Club**, yang merupakan kumpulan gambar digital animasi kera dengan berbagai kostum dan properti.

Setiap NFT adalah representasi on-chain dari kombinasi berikut:

- **ID Token Numerik**: Sebuah angka unik untuk setiap token dalam sebuah koleksi.
- **Alamat Kontrak Koleksi**: Seperti alamat dompet Anda, setiap kontrak pintar koleksi dapat diidentifikasi dengan alamat uniknya di jaringan.
- **Jaringan**: Jaringan blockchain tempat koleksi tersebut berada, seperti Ethereum atau Lisk.

![Gambar](/markdown/photo_02.jpg)

Sebagai contoh: Sebuah NFT dengan ID 6477 yang berada dalam koleksi di alamat `0xbc4ca0eda7647a8ab7c2061c2e118a18a936f13d` di jaringan Ethereum berisi tautan ke gambar di atas.

Mungkin ada NFT lain yang menautkan ke gambar yang sama. Namun, yang membuat NFT benar-benar unik adalah kombinasi dari tiga parameter ini — ID token, alamat koleksi, dan jaringan.

Namun, NFT tidak hanya tentang gambar, karena sering kali juga merepresentasikan jenis konten dan aset lainnya...

## NFT Bukan Hanya Gambar - Kasus Penggunaan

Seperti disebutkan dalam bagian sebelumnya, NFT adalah jenis token unik yang dapat berisi tautan ke beberapa konten lainnya.

Jenis seni digital lain yang sering dihubungkan oleh NFT mencakup video dan **musik**. Misalnya, ada pasar NFT untuk pembuat musik di mana mereka dapat memperdagangkan token yang merepresentasikan trek—bagian-bagian dari sebuah lagu. Karena struktur NFT, pencipta trek dapat secara otomatis memperoleh royalti dari setiap penjualan atau pemutaran lagu tersebut.

Contoh hebat lainnya adalah industri **game**. NFT dapat merepresentasikan item dalam game (misalnya, pedang, karakter yang dapat dimainkan, peti loot, atau bahkan tanah dalam game) dan skin-nya. Beberapa game online, seperti Decentraland, dibangun sedemikian rupa sehingga setiap item yang dapat dimainkan adalah NFT yang juga dapat digunakan di game lain atau diperdagangkan di pasar terdesentralisasi.

Tetap dalam dunia digital, beberapa NFT dapat merepresentasikan **nama domain** untuk situs web. Setelah Anda mendaftarkan nama domain dengan salah satu penyedia yang mendukung NFT, Anda juga menerima hak untuk menggunakan nama domain ini, mengarahkannya ke situs web mana pun, atau memperdagangkannya di pasar tanpa memerlukan pendaftar terpusat.

Ingat Uniswap, bursa terdesentralisasi dari pelajaran kita tentang token fungible? Penyedia likuiditas juga menerima NFT sebagai representasi standar dari bagian likuiditas keseluruhan mereka. Jadi, jika Anda menyediakan, misalnya, ETH dan USDT, Anda menerima NFT yang menyatakan, "pemilik NFT ini berhak menarik sejumlah ETH dan USDT ini dari kumpulan likuiditas." Anda dapat menyimpan NFT ini di dompet Anda, memberikan, atau menjualnya kepada orang lain. Namun ingat—siapa pun yang memegang NFT ini, mereka berhak menarik jumlah likuiditas yang direpresentasikannya. Dan setelah Anda menarik bagian likuiditas Anda dari kumpulan, NFT ini dihancurkan.

## Mengakses NFT dari Dompet Anda

Bagaimana Anda dapat melihat NFT yang dimiliki oleh alamat Anda? Sama seperti token native dan fungible, berinteraksi dengan NFT memerlukan dompet digital. Anda dapat memilih dari berbagai jenis dompet.

- **Ekstensi Browser**: Banyak dompet berbasis browser, seperti MetaMask, dapat melihat NFT Anda, mentransfernya ke akun lain, dan melakukan operasi lainnya.
- **Dompet Seluler**: Salah satu kasus penggunaan yang hebat dari NFT adalah bahwa NFT dapat merepresentasikan, misalnya, tiket acara yang mudah dilacak dan diperdagangkan di bursa terdesentralisasi. Setelah Anda memasuki tempat acara, cukup buka dompet seluler Anda, dan penyelenggara dapat memindai kode QR yang ditautkan oleh tiket NFT.
- **Dompet Perangkat Keras**: Anda juga dapat menyimpan NFT Anda di dompet perangkat keras seperti Ledger atau Trezor. Ini dianggap sebagai opsi paling aman untuk token bernilai tinggi, karena penyimpanan dingin sering dilindungi oleh langkah-langkah keamanan tambahan seperti kode PIN dan kata sandi khusus.


## Transfer dan Persetujuan

Transfer token adalah salah satu fitur dasar dari dompet apa pun yang mendukung NFT. Anda cukup memilih token tertentu yang ingin ditransfer, memasukkan alamat penerima, dan menekan tombol kirim. Namun, Anda juga perlu memastikan memiliki sejumlah kecil **token asli** (misalnya, ETH) pada jaringan tempat Anda mengirim NFT untuk menutupi **biaya transaksi**, seperti yang telah disebutkan dalam pelajaran sebelumnya.

Anda mungkin juga ingin memberikan persetujuan kepada orang lain untuk mengoperasikan NFT Anda. Tapi mengapa memberikan persetujuan daripada langsung mengirimkan token tersebut? Persetujuan biasanya diberikan bukan kepada pengguna akhir tetapi kepada kontrak pintar, misalnya, kepada pasar NFT yang akan dibahas lebih mendalam di bagian berikutnya.

Jika Anda memutuskan untuk menjual NFT Anda untuk ditukar dengan token fungible di sebuah pasar, transaksi tersebut melibatkan beberapa langkah yang harus terjadi secara bersamaan. Memberikan persetujuan kepada pasar memungkinkan mereka menarik NFT dari dompet Anda selama perdagangan berlangsung, sambil secara bersamaan mengirimkan token fungible yang Anda terima dalam pertukaran tersebut.

Ada dua jenis persetujuan terkait NFT:

1. Anda dapat menyetujui seseorang untuk mengoperasikan **satu token tertentu** dari koleksi tertentu. Persetujuan jenis ini dapat diulang sebanyak yang Anda inginkan, dengan token berbeda dalam koleksi yang sama atau di koleksi yang berbeda.
2. Anda juga dapat memberikan persetujuan kepada mereka untuk mengoperasikan **semua token** yang Anda miliki dalam koleksi tertentu. Dengan cara ini, Anda tidak perlu terus-menerus memberikan persetujuan satu per satu jika ingin mereka mengoperasikan beberapa token sekaligus.

Penting untuk dipahami bahwa operator yang disetujui (orang atau protokol yang Anda beri persetujuan) dapat mentransfer NFT tersebut keluar dari dompet Anda. Oleh karena itu, tetaplah berhati-hati dan hanya memberikan persetujuan kepada pihak yang Anda percayai.

## Contoh Dunia Nyata

Kami telah menyebutkan beberapa contoh di bagian Kasus Penggunaan. Sekarang, mari kita lihat lebih dekat NFT Uniswap yang mewakili likuiditas.

Dalam versi 3 mereka, protokol Uniswap memperkenalkan likuiditas terkonsentrasi, yang berarti Anda dapat menyediakan likuiditas bukan hanya untuk keseluruhan pool tetapi juga untuk rentang harga tertentu. Semakin kecil rentang harga tempat Anda menyediakan likuiditas, semakin besar bagian biaya perdagangan yang bisa Anda peroleh.

Begitu Anda menyediakan likuiditas dalam rentang tertentu, Uniswap mencetak NFT untuk Anda yang mewakili bagian likuiditas tersebut. NFT ini mencakup informasi penting seperti:

- Pool tertentu tempat Anda menyediakan likuiditas
- Token fungible yang Anda setorkan (misalnya, ETH dan USDC)
- Rentang harga posisi likuiditas (misalnya, antara 2.000 hingga 3.000 USDC untuk 1 ETH)

Karena NFT sering kali **terkait** dengan gambar, mereka juga menciptakan gambar yang ditautkan oleh NFT tersebut, menampilkan grafik posisi likuiditas dan informasi bermanfaat lainnya.

Sebagai contoh, [di sini](https://opensea.io/assets/ethereum/0xc36442b4a4522e871399cd717abdd847ab11fe88/1) Anda dapat melihat NFT posisi likuiditas pertama, yang dicetak oleh pendiri Uniswap, Hayden Adams. Nilai "Tick" negatif menunjukkan rentang harga—dalam hal ini, tick bawah -50580 mewakili sekitar 0,00636 WETH per 1 UNI, dan tick atas -36720 mewakili sekitar 0,02543 WETH per 1 UNI. Setiap kali token UNI diperdagangkan dalam rentang harga ini, pemilik NFT menerima bagian dari biaya perdagangan.

Tautan tersebut mengarah ke OpenSea, salah satu **pasar** NFT terbesar dan tertua. OpenSea menampilkan semua koleksi NFT di berbagai jaringan, termasuk semua token dalam koleksi tersebut. Ketika pemilik NFT memutuskan untuk menjual NFT mereka, mereka dapat melakukannya di OpenSea atau pasar lainnya.

## Pasar NFT

Pasar NFT adalah platform tempat Anda dapat **memperdagangkan** NFT. Platform ini mirip dengan situs e-commerce dan rumah lelang daring, tetapi beroperasi menggunakan teknologi blockchain, yang memberikan transparansi, keamanan, dan desentralisasi lebih baik dibandingkan sistem tradisional.

Beberapa pasar terkenal meliputi [OpenSea](https://opensea.io/), [Rarible](https://rarible.com/), dan [SuperRare](https://superrare.com/). Umumnya, situs pasar memindai semua koleksi NFT baru dan yang sudah ada di beberapa jaringan untuk mencari token yang baru dibuat. Begitu mereka menemukan token baru, mereka dapat menampilkan detailnya, seperti alamat pembuat dan gambar yang ditautkan oleh NFT tersebut, di situs pasar.

Siapa pun dapat menggunakan pasar untuk mendaftarkan NFT yang mereka miliki untuk dijual atau membeli NFT. Saat menggunakan pasar ini, Anda dapat menelusuri NFT yang tersedia, dan setelah **menghubungkan dompet Anda**, Anda dapat menawar atau membeli secara langsung.

Karena daftar NFT biasanya **terikat pada pasar tertentu**, beberapa pembuat mungkin memilih untuk hanya mendaftarkan NFT mereka di satu atau dua situs terbesar, sementara yang lain mungkin ingin mendaftarkannya di sebanyak mungkin platform.

Ingin mencoba membangun koleksi Anda sendiri? Jika ya, lanjutkan ke kursus IDE berikutnya untuk belajar membuat kontrak pintar sederhana untuk koleksi NFT Anda sendiri.

