### Implementasi Open Source

Standar [ERC20](https://eips.ethereum.org/EIPS/eip-20) mendefinisikan beberapa fungsi - `name()`, `symbol()`, `decimals()`, `balanceOf(uint256)`, `totalSupply()`, `transfer(address,uint256)`, `approve(address,uint256)`, `allowance(address,address)`, dan `transferFrom(address,address,uint256)` - serta event `Transfer(address,address,uint256)` dan `Approval(address,address,uint256)`.

Semua ini sudah diimplementasikan dalam kontrak `ERC20.sol` dari OpenZeppelin yang diimpor dan dependensinya. Itulah mengapa Anda tidak melihatnya dalam kode ini.

***Decimals***

Node EVM berjalan di berbagai jenis komputer yang menggunakan tipe prosesor berbeda. Salah satu tantangan pada sistem multi-platform yang hingga kini belum terselesaikan adalah bekerja dengan angka desimal.

Pembagian matematika sederhana seperti 1/3 mungkin menghasilkan hasil dengan:

- presisi hingga 16 desimal yang dibulatkan ke bawah pada satu jenis prosesor
- tetapi juga - presisi hingga 17 desimal yang dibulatkan ke atas pada jenis prosesor lainnya

Untuk mengurangi kesalahan pembulatan, EVM dan Solidity tidak menggunakan tipe desimal sama sekali. Tidak ada tipe `float`, `double`, atau tipe desimal lainnya yang mungkin Anda ketahui dari bahasa pemrograman lain. Sebagai gantinya, angka desimal disimpan sebagai `integer` (dan sering kali sebagai `unsigned integer`) dengan jumlah desimal yang telah ditentukan sebelumnya.

_(Untuk pengembang tingkat lanjut: Ya, ada pengecualian dari aturan ini. Dalam beberapa kasus, Anda mungkin menemukan angka desimal di Solidity sebelum dikompilasi menjadi bytecode - tetapi semuanya diubah menjadi bilangan bulat selama kompilasi (misalnya, `0.5 * 2` diubah menjadi `1`). Jika transformasi ini gagal (misalnya pada kasus `0.4 * 2`), maka kompilasi akan gagal.)_

Misalnya, Anda mendefinisikan bahwa semua angka Anda akan menggunakan **2 desimal**.

Jika Anda ingin menyimpan angka "satu", Anda cukup menyimpannya sebagai `100`.

"Satu setengah" kemudian menjadi `150`.

Dengan **3 desimal** yang telah ditentukan, "satu" menjadi `1000`.

Dan dengan **18 desimal**, "satu" disimpan sebagai `1000000000000000000` (satu dan 18 nol). Yang membuat "setengah" disimpan sebagai `500000000000000000` (lima dan 17 nol).

Jumlah desimal yang telah ditentukan untuk token Anda dikembalikan dari fungsi `decimals()` dengan tipe `uint8`. `uint8` berarti "unsigned integer dengan panjang 8 bit", yang berarti nilai desimal maksimalnya adalah 255. Tetapi jumlah desimal yang biasa dan paling umum Anda temui adalah 18, kemungkinan karena token asli Ethereum, ETH, juga menggunakan 18 desimal.

## Latihan

- Override fungsi `decimals()` (dari `ERC20.sol`) di dalam kontrak Anda sendiri untuk mengubah jumlah desimal menjadi 6.
