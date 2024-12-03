###### Mencetak sebuah NFT

Salah satu elemen utama dari kontrak NFT adalah **fungsi mint**.

Mencetak NFT adalah proses di mana Anda menerbitkan item digital non-fungible ke dalam blockchain. ini memungkinkan Anda men-tokenisasi aset dengan merepresentasikannya dalam unit NFT, di mana kepemilikan dan keasliannya divalidasi oleh jaringan blockchain tempat NFT tersebut dideploy.

Ketika Anda mencetak NFT, biasanya ada dua parameter yang bervariasi:

- **penerima**, yaitu alamat akun yang akan menerima NFT yang baru dibuat.
- **NFT ID**, yaitu sebuah bilangan integer `uint256` yang secara unik diasosiasikan dengan setiap NFT baru yang dicetak.

Pasangan parameter ini membentuk suatu pemetaan (mapping) yang memungkinkan pelacakan kepemilikan NFT sejak pertama kali dicetak. Berikut adalah contohnya dalam [implementasi ERC721 dari OpenZeppelin](https://github.com/agorapp-dao/openzeppelin-contracts/blob/6bd6b76d1156e20e45d1016f355d154141c7e5b9/contracts/token/ERC721/ERC721.sol):

```sol
mapping(uint256 => address) private _owners;
```

Ketika sebuah kontrak ERC-721 mencetak NFT, kontrak tersebut memperbarui sebuah `(uint256 => address) mapping` dengan menetapkan NFT ID sebagai kunci `uint256` [yang terkait dengan alamat akun penerima](https://github.com/agorapp-dao/openzeppelin-contracts/blob/6bd6b76d1156e20e45d1016f355d154141c7e5b9/contracts/token/ERC721/ERC721.sol#L287).

Selanjutnya, setiap transfer akan memperbarui nilai dari `(uint256 => address)` yang sama, dengan menggunakan `uint256 tokenId` sebagai pengenal unik dan mengubah nilai `address` yang sesuai menjadi pemilik baru dari NFT.

Inilah kekuatan blockchain: secara otomatis, Anda diberikan riwayat publik yang dapat diaudit dari setiap transaksi item digital non-fungible.

## Latihan

Sekarang waktunya untuk mengimplementasikan fungsi `mint` dalam kontrak `AgorappNFT` kita.

- Definisikan fungsi `external` bernama `mintBadge`.
- `mintBadge` diharapkan untuk membuat `AGORA` NFT baru dengan token id yang ditentukan oleh pemanggil. Alamat tempat NFT dicetak juga ditentukan oleh pemanggil.
- Urutan yang diharapkan dari argumen untuk fungsi `mintBadge` adalah: `mintBadge(uint256, address)`.
- Jangan menambahkan dependensi tambahan.
