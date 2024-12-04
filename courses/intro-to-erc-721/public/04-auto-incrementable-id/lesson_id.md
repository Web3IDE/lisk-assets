### Token ID yang Dapat Bertambah Otomatis

Sejauh ini, kita telah menetapkan `tokenId` untuk NFT kita secara manual. Namun, metode ini biasanya tidak ideal untuk mengasosiasikan ID unik dengan NFT karena rentan terhadap kesalahan.

[Desain EIP-721](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md) tidak mewajibkan pola tertentu untuk memperbarui `tokenId` NFT. Satu-satunya persyaratan ketat adalah bahwa setelah ID unik (`tokenId`) dihubungkan dengan NFT, nilainya harus tetap unik dan tidak dapat diubah selama masa kontrak.

Pola yang paling umum digunakan untuk memperbarui variabel state `tokenId` pada kontrak adalah dengan menetapkan nilai awalnya ke 0, kemudian meningkatkannya sebesar 1 untuk setiap NFT baru yang dicetak.

Pola ini menjadi sangat populer sehingga [OpenZeppelin menstandarisasinya dalam pustaka bernama `Counters`](https://github.com/agorapp-dao/openzeppelin-contracts/blob/6bd6b76d1156e20e45d1016f355d154141c7e5b9/contracts/utils/Counters.sol), yang sering digunakan bersama kontrak erc-721 OpenZeppelin untuk mengelola `tokenId`.

Namun, pustaka `Counters` cukup sederhana sehingga kita dapat membuat versi yang lebih kecil secara mandiri.

### Latihan

Sejauh ini, fungsi mint kita menetapkan ID token sebagai nilai yang diberikan oleh pemanggil fungsi melalui argumen `uint256`.

Namun, ini bukan praktik standar.

Biasanya, ID token adalah nilai yang awalnya ditetapkan ke 0 dan bertambah secara berurutan, naik satu setiap kali token berhasil dicetak.

- Hapus argumen `uint256` yang diteruskan ke fungsi `mintBadge`.
- ID token diharapkan menjadi nilai yang awalnya disetel ke 0 dan bertambah 1 setiap kali NFT baru diterbitkan.
- Definisikan fungsi getter bernama `getCurrentTokenId` yang mengembalikan nilai `uint256` `tokenId` saat ini.
- Jangan tambahkan dependensi tambahan.
