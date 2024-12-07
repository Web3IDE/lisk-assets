###### Transfer dari alamat lain dan persetujuan

Pada pelajaran sebelumnya, kita menjelaskan bagaimana transfer token dilakukan jika pemegang token memanggil fungsi `transfer()`. Namun, bagaimana jika Anda ingin kontrak Anda dapat mentransfer token milik orang lain selain milik Anda?

Contoh yang bagus dari mekanisme ini adalah bursa terdesentralisasi. Saat melakukan pertukaran (misalnya membeli WETH dengan USDC), bursa melakukan dua jenis transfer:

1. Menarik token USDC dari dompet pengguna
2. Dan mengirimkan WETH yang telah dipertukarkan kepada mereka

Kita sudah tahu bagaimana langkah kedua bekerja. Bursa hanya memanggil `weth.transfer(userAddress, exchangedAmount)` - dan karena pemanggil fungsi `transfer()` adalah bursa, token dikirim dari saldo mereka.

Tapi bagaimana mereka dapat mentransfer token dari dompet pengguna?

***Transfer Dari***.

Ada fungsi lain yang mirip dengan transfer biasa yang sudah dijelaskan. Dan fungsi ini disebut **Transfer Dari**.

Fungsi ini menerima 3 argumen alih-alih 2 argumen yang sebelumnya. Argumen baru di posisi pertama adalah alamat pengirim.

`transferFrom(address sender, address recipient, uint256 value)`

Saat Anda memanggil fungsi ini, Anda dapat mentransfer token dari dompet orang lain (`sender`) ke alamat siapa pun (`recipient`) - bahkan ke alamat Anda sendiri.

Menggunakan contoh bursa terdesentralisasi, kontrak bursa juga melakukan panggilan ini:

```
// transfer usdc dari pengguna ke alamat kami sendiri
usdc.transferFrom(userAddress, address(this), amountToBeExchanged);
```

Tapi... Ini hanya mungkin jika pengirim telah memberikan Anda (pemanggil fungsi) persetujuan sebelumnya untuk mengoperasikan token mereka.

***Persetujuan dan Alokasi***.

Persetujuan untuk "transfer dari" di masa depan hanya dapat diberikan oleh pemegang token dengan memanggil fungsi `approve(address,uint256)` pada kontrak token. Argumen pertama adalah alamat pengeluaran yang Anda izinkan untuk mengoperasikan token Anda (misalnya bursa). Dan argumen kedua adalah batas pengeluaran. Anda tidak perlu memberi mereka kontrol penuh atas semua token Anda, tetapi Anda dapat membatasi seberapa banyak yang mereka izinkan untuk dibelanjakan.

Fungsi `approve(address,uint256)` memancarkan acara `Approval(address,address,uint256)`. Argumen pertama adalah pemilik token yang memberikan persetujuan, argumen kedua adalah pengelola yang disetujui, dan argumen ketiga adalah batas berapa banyak yang mereka izinkan untuk dibelanjakan. Sama seperti pada pelajaran sebelumnya, acara ini berguna untuk aplikasi offchain yang dapat melacak persetujuan dan menampilkannya dengan cara yang ramah pengguna.

Ada juga fungsi getter standar untuk mengambil jumlah yang disetujui saat ini. `allowance(address owner, address spender) returns (uint256)` menerima dua argumen - pemilik token dan pengelola token. Dengan cara ini, Anda juga dapat memvalidasi apakah Anda telah memberi persetujuan kepada Uniswap atau bursa terdesentralisasi lainnya, dan seberapa banyak dari jumlah yang disetujui yang masih tersisa untuk dibelanjakan.

## Latihan

- Override fungsi OpenZeppelin `_approve(address,address,uint256,bool)` . Buatlah untuk memancarkan acara baru `VitalikApproval` - tetapi hanya jika ada persetujuan ke atau dari alamat Vitalik `0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045`.
