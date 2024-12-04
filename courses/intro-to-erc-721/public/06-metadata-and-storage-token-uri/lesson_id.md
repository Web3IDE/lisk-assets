###### Metadata dan tokenURI yang Disimpan

Dalam implementasinya terhadap standar ERC-721, OpenZeppelin mengikuti desain modular di mana kontrak dasar `ERC721` yang telah kita gunakan sejauh ini dapat dengan mudah diperluas.

Ekstensi yang akan kita tambahkan pada pelajaran terakhir ini adalah kontrak `ERC721URIStorage`.

Melihat kontrak `ERC721` [di sini](https://github.com/agorapp-dao/openzeppelin-contracts/blob/6bd6b76d1156e20e45d1016f355d154141c7e5b9/contracts/token/ERC721/ERC721.sol), kita dapat mengamati bahwa tokenUri tidak disimpan dalam penyimpanan kontrak, tetapi [dihitung setiap kali secara dinamis](https://github.com/agorapp-dao/openzeppelin-contracts/blob/6bd6b76d1156e20e45d1016f355d154141c7e5b9/contracts/token/ERC721/ERC721.sol#L93-L98). Karena string di Solidity cukup mahal, pendekatan ini memiliki keuntungan menghemat biaya gas.

Ekstensi `ERC721URIStorage` mengikuti pendekatan yang berbeda. Fungsi `_setTokenURI` menyimpan `_tokenURI` dalam penyimpanan kontrak.

```sol
function _setTokenURI(uint256 tokenId, string memory _tokenURI) internal virtual {
    require(_exists(tokenId), "ERC721URIStorage: URI set of nonexistent token");
    _tokenURIs[tokenId] = _tokenURI;
}
```

Mirip dengan [pemetaan `_owners`](https://github.com/agorapp-dao/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol#L29-L30) dalam kontrak `ERC721`, fungsi `_setTokenURI` dari `ERC721URIStorage` menggunakan pengidentifikasi unik `uint256 tokenId` untuk melacak nilai token uri dari sebuah NFT.

```sol
mapping(uint256 => string) private _tokenURIs;
```

## Latihan

- Kami telah mengimpor kontrak `ERC721URIStorage` dari OpenZeppelin untuk Anda. Sekarang saatnya Anda menggunakannya untuk memperluas `AgorappNFT` dan menggantikan kontrak `ERC721`.
- Setiap token baru yang diterbitkan harus dikaitkan dengan `tokenURI`.
- Token URI harus diatur saat memanggil fungsi `mintBadge`.
- Perluas event `CreatedNFT` yang sebelumnya dibuat dengan menambahkan parameter ketiga bertipe `string`. Saat memicu event, parameter string harus berupa `tokenURI`.
- Jangan tambahkan dependensi tambahan.
