###### Apa itu standar ERC-20

ERC-20 adalah salah satu standar Ethereum yang paling awal (secara harfiah yang ke-20). Ini memungkinkan kita untuk membangun token kustom di jaringan EVM - bukan hanya Ethereum, tetapi juga Polygon, Binance Smart Chain, Arbitrum, dan lainnya.

Dalam kursus ini, kita akan melihat sisi teknis bagaimana token ERC20 bekerja. Kita akan mengeksplorasi beberapa implementasi yang ada - dan sebagai validasi dari apa yang telah kita pelajari, kita akan membangun token ERC20 kita sendiri di pelajaran terakhir.

***Nama dan simbol***

Sebagai pembuat token, Anda mungkin ingin memilih nama dan simbol token. Sebagai contoh, salah satu token stablecoin yang terkenal menggunakan nama "Tether USD" dan simbol "USDT".

Banyak aplikasi offchain (seperti Etherscan dan semua jenis pelacak token) menampilkan nama dan simbol token Anda sebagai cara yang lebih ramah pengguna untuk mengidentifikasi token yang berbeda dibandingkan hanya menampilkan alamat mereka.

***Implementasi Sumber Terbuka***

Karena token ERC-20 distandarisasi, ada banyak implementasi sumber terbuka dari standar ini yang dapat Anda manfaatkan saat membangun token Anda. Anda dapat dengan mudah memperluas kode mereka dan membangun di atas apa yang telah mereka buat, sehingga Anda tidak perlu menulis fitur dasar seperti transfer dan kueri saldo berulang-ulang.

Dalam pelajaran berikut, kita akan menggunakan implementasi sumber terbuka ERC20 yang dibuat oleh OpenZeppelin. Mari kita mulai dengan mengenal dasar-dasar kode mereka.

Konstruktor mereka menerima dua argumen - nama token dan simbol. Mari kita coba.

## Latihan

- Ubah nama token dari `Some Token` menjadi `Agorapp Token`
- Ubah simbol token dari `SoT` menjadi `AGORA`
