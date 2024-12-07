###### Mint dan burn token

Standar ERC20 tidak menentukan apa pun tentang peningkatan atau pengurangan total pasokan. Namun, karena penulis token sering membutuhkan fitur ini, banyak kontrak pintar token yang menyertakan fungsi yang memungkinkan peningkatan dan penurunan total pasokan sebagai ekstensi opsional dari standar minimal.

Implementasi OpenZeppelin dari `ERC20.sol` mendefinisikan fungsi `_mint(address,uint256)`. Seperti yang dijelaskan dalam [halaman panduan](https://docs.openzeppelin.com/contracts/5.x/erc20-supply) mereka, argumen pertama berisi alamat penerima token yang baru dicetak, dan argumen kedua adalah jumlah token.

Jumlah token mencakup desimal. Jadi, sebagai contoh, jika token Anda menggunakan 2 desimal, dan Anda ingin mencetak 5 token, nilai argumen kedua menjadi 500.

Saat Anda memeriksa kode mereka, Anda dapat melihat bahwa fungsi `_mint()` dideklarasikan dengan modifier visibilitas `internal`. Ini berarti kontrak Anda dapat memanggilnya - dengan asumsi bahwa kontrak Anda diturunkan dari `ERC20.sol` mereka. Tetapi karena visibilitas `internal`, fungsi ini tidak tersedia untuk pemanggil eksternal (misalnya, pengguna) secara langsung. Jika fungsi ini dapat dipanggil oleh siapa saja, maka harus memiliki visibilitas `external` atau `public`.

_OpenZeppelin `ERC20.sol`_:

```
function _mint(address account, uint256 value) internal
```

## Latihan

- Gunakan fungsi `_mint(address,uint256)` dari OpenZeppelin. Cetak 100 token penuh (jangan lupa desimal) ke alamat peng-deploy (`msg.sender` di constructor).
