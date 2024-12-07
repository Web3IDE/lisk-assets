Menyimpan data di blockchain Ethereum itu mahal.

Pada saat yang sama, kontrak pintar, seperti perangkat lunak lainnya, mendapatkan manfaat dari log yang dirancang dengan baik yang memungkinkan aplikasi pihak ketiga untuk mendengarkan dan merespons peristiwa di blockchain.

Setara dengan log di blockchain Ethereum sebenarnya disebut `event`, dan penggunaannya jauh lebih murah dibandingkan dengan data `storage`. Namun, mereka memiliki tujuan yang berbeda.

Beberapa kasus penggunaan yang mungkin termasuk memungkinkan antarmuka aplikasi untuk menampilkan pemberitahuan kepada pengguna saat terjadi perubahan status di blockchain atau memantau kontrak pintar untuk tujuan keamanan.

Event kontrak didefinisikan menggunakan kata kunci `event` dan, seperti halnya fungsi, dapat memiliki satu atau lebih parameter. Namun, berbeda dengan fungsi, event tidak perlu menentukan lokasi data saat menggunakan variabel tipe kompleks sebagai parameter. Ini karena event tidak disimpan di `memory` atau `storage`, karena mereka dimaksudkan untuk konsumsi di luar rantai.

Anda dapat memicu sebuah `event` menggunakan kata kunci `emit`, seperti pada contoh berikut:

```sol
event Transfer(address from, address to, uint256 value);

function transfer(address to, uint256 value) public returns (bool) {
  // Transfer nilai yang ditentukan kepada penerima
  // ...
  emit Transfer(msg.sender, to, value);
  return true;
}
```

Kata kunci `indexed` dapat diterapkan pada hingga tiga parameter `event`. Parameter `indexed` dapat lebih mudah difilter dan dicari oleh aplikasi yang mendengarkan.

```sol
event Transfer(address indexed from, address indexed to, uint256 value);

function transfer(address to, uint256 value) public returns (bool) {
  // Transfer nilai yang ditentukan kepada penerima
  // ...
  emit Transfer(msg.sender, to, value);
  return true;
}
```

## Latihan

- Deklarasikan sebuah `event` bernama `LogGreeting` yang mengambil argumen berupa `string`.
- Jangan menjadikannya indexable.
- Picu event `LogGreeting` ketika sebuah akun mengubah nilai variabel `greeting`.
- Event `LogGreeting` harus mencatat nilai baru dari variabel `greeting` dalam bidang bernama `updatedGreeting`.
