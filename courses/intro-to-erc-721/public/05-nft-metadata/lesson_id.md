###### Metadata dan tokenURI di dalam penyimpanan

Metadata NFT adalah kumpulan anotasi kaya yang mendeskripsikan sebuah NFT.

Biasanya, skema metadata mencakup URI yang menunjuk ke sebuah gambar. Karena sebagian besar NFT saat ini merepresentasikan karya seni digital, URI gambar dalam metadata mengarahkan ke aset yang ditokenisasi oleh NFT tersebut.

Untuk meningkatkan interoperabilitas antara komponen NFT yang ada di rantai (on-chain) dan komponen di luar rantai (off-chain) — seperti marketplace — skema metadata akhirnya berkembang menjadi standar yang terpadu: `ERC721 Metadata JSON Schema`.

```javascript
{
    "title": "Asset Metadata",
    "type": "object",
    "properties": {
        "name": {
            "type": "string",
            "description": "Identifies the asset to which this NFT represents"
        },
        "description": {
            "type": "string",
            "description": "Describes the asset to which this NFT represents"
        },
        "image": {
            "type": "string",
            "description": "A URI pointing to a resource with mime type image/* representing the asset to which this NFT represents. Consider making any images at a width between 320 and 1080 pixels and aspect ratio between 1.91:1 and 4:5 inclusive."
        }
    }
}
```

Standar `ERC721 Metadata JSON Schema` juga dijelaskan. [eip-721 resmi](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-721.md).

Contoh dari `ERC721 Metadata JSON Schema` adalah metadata berikut:

```javascript
{
  "name": "Agorapp Badge",
  "description": "Enrich your on-chain resume by collecting skill badges which document your accomplishments!",
  "image": "https://agorapp.dev/favicon.io",
}
```

Anda mungkin memperhatikan bahwa metadata NFT adalah entitas yang cukup besar jika dibandingkan dengan variabel yang biasanya kita kelola dalam konteks on-chain.

Penyimpanan adalah komoditas yang mahal di jaringan Ethereum, itulah sebabnya sebagian besar NFT menyimpan metadata mereka di luar rantai (off-chain).

Untuk menghindari penggunaan layanan penyimpanan off-chain terpusat seperti *s3 buckets*, industri sebagian besar telah mengadopsi platform peer-to-peer untuk kebutuhan penyimpanannya.

Beberapa solusi penyimpanan terdesentralisasi yang paling menonjol adalah:  
- Ethereum Swarm  
- IPFS dan Filecoin  
- Arweave

Dengan pengecualian IPFS - yang merupakan jaringan peer-to-peer -, platform lainnya adalah blockchain sepenuhnya yang dioptimalkan untuk penyimpanan sebagai kasus penggunaan utama. Mereka menawarkan ketahanan terhadap sensor yang kuat, sifat tidak dapat diubah, dan jaminan desentralisasi.

Standar `ERC721 Metadata JSON Schema` didukung secara luas oleh industri, termasuk oleh OpenSea - marketplace NFT terbesar. Spesifikasi lain yang diharapkan oleh OpenSea, seperti halnya sebagian besar DApps dan API lainnya, adalah metode **`tokenURI`.

Metode `tokenURI` adalah penunjuk ke lokasi metadata NFT di luar rantai. Marketplace seperti OpenSea menggunakannya untuk mengambil data yang terkait dengan NFT dan menampilkannya.

Dalam kontrak `ERC721` OpenZeppelin, [fungsi `tokenURI`](https://github.com/agorapp-dao/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol#L90-L98) membangun penunjuk URI secara dinamis dengan menggabungkan [`_baseURI()`](https://github.com/agorapp-dao/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol#L100-L107) dan `tokenId`.

```solidity
/**
 * @dev See {IERC721Metadata-tokenURI}.
 */
function tokenURI(uint256 tokenId) public view virtual override returns (string memory) {
    _requireMinted(tokenId);
    string memory baseURI = _baseURI();
    return bytes(baseURI).length > 0 ? string(abi.encodePacked(baseURI, tokenId.toString())) : "";
}
/**
 * @dev Base URI for computing {tokenURI}. If set, the resulting URI for each
 * token will be the concatenation of the `baseURI` and the `tokenId`. Empty
 * by default, can be overridden in child contracts.
 */
function _baseURI() internal view virtual returns (string memory) {
    return "";
}
```

Output dari `_baseURI()` adalah string yang seharusnya menjadi awalan umum untuk semua URI, sementara `tokenId` memberikan pengidentifikasi unik untuk membedakan URI yang dihasilkan.

## Latihan

- Buat `_baseURI()` untuk mengembalikan "https://alice_in_wonderland/".
- Deklarasikan sebuah event yang disebut `CreatedNFT` yang mengambil dua argumen `indexed`: `address` dan `tokenId`.
- Nyatakan event `CreatedNFT` di akhir fungsi minting. Parameter yang perlu dicatat adalah penerima NFT yang dicetak dan ID token dari NFT yang dicetak.
- Jangan tambahkan dependensi tambahan.
