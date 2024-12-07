Secara umum, dalam Solidity, fungsi digunakan untuk mendapatkan atau mengatur informasi sebagai respons terhadap panggilan fungsi.

Pengecualian utama dari pernyataan di atas adalah fungsi `pure`. Sebuah fungsi harus dideklarasikan sebagai `pure` ketika fungsi tersebut tidak membaca atau mengubah state.

```sol
function computeSum(uint256 _x, uint256 _y) pure returns(uint256) {
  return _x + _y;
}
```

Ketika sebuah fungsi melakukan perubahan pada penyimpanan kontrak, maka fungsi tersebut harus dideklarasikan tanpa kata kunci `view` atau `pure`.

```sol
uint256 private favoriteNumber
function setSecretNumber(uint256 _favoriteNumber) public returns(uint256) {
  favoriteNumber = _favoriteNumber;
}
```

Serupa dengan nilai yang dikembalikan, argumen dari sebuah fungsi juga harus dianotasi dengan tipe yang sesuai.

Terakhir, untuk beberapa tipe tertentu yang disebut [**reference types**](https://docs.soliditylang.org/en/v0.8.10/types.html#reference-types), **lokasi data harus selalu ditentukan**.

Lokasi data mengacu pada **tempat dimana nilai variabel disimpan**. Dalam Solidity, ada tiga lokasi data yang mungkin: `storage`, `memory`, dan `calldata`:

- **penyimpanan**: Variabel penyimpanan disimpan dalam blockchain dan nilai-nilai mereka tetap ada di seluruh transaksi. Mereka dialokasikan dalam slot penyimpanan di penyimpanan kontrak.
- **memori**: Ini adalah lokasi data sementara. Variabel `memory` dibuat dan digunakan dalam satu panggilan fungsi. Setelah panggilan fungsi selesai, variabel `memory` dihancurkan.
- **data panggilan**: Ini adalah lokasi data khusus yang hanya dapat digunakan untuk argumen fungsi ketika fungsi kontrak dipanggil dari luar kontrak. Oleh karena itu, ini hanya dapat diterapkan pada fungsi `public` dan `external`. `calldata` hanya dapat dibaca dan tidak bisa dimodifikasi oleh fungsi.

Lokasi data `calldata` dapat ditentukan seperti dalam contoh berikut:

```sol
function computeStringLength(string calldata _string_) public returns(uint256) {
  // Akses argumen input calldata (string)
  uint256 stringLength = bytes(_string_).length;
  return stringLength;
}
```

Perlu dicatat bahwa `calldata` hanya dapat digunakan untuk parameter fungsi dan **TIDAK untuk tipe nilai yang dikembalikan**. Itulah sebabnya pada pelajaran sebelumnya kami merekomendasikan untuk menggunakan lokasi data `memory` untuk mengembalikan nilai string dari sebuah fungsi.

## Latihan

- Deklarasikan fungsi publik bernama `setGreeting`.
- Fungsi `setGreeting` perlu menerima string sebagai argumen.
- Gunakan nilai string yang diteruskan sebagai argumen untuk `setGreeting` untuk memperbarui nilai dari variabel state `greeting`.
