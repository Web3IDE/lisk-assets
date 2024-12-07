Pada pelajaran sebelumnya, kita belajar bagaimana mendefinisikan state variables pada kontrak. Pada pelajaran ini, kita akan membahas bagaimana dunia luar dapat mengakses variabel-variabel ini.

Setiap kali Anda mendeklarasikan state variable **public**, compiler secara otomatis membuat fungsi **getter** untuknya. Apa yang dilakukan oleh fungsi getter adalah memungkinkan [akun Ethereum](https://ethereum.org/en/developers/docs/accounts/) untuk mengambil nilai yang saat ini disimpan dalam state variable dengan memanggilnya seolah-olah itu adalah sebuah fungsi.

Bagaimana jika kita mendeklarasikan state variable **private**? Dalam hal ini, kita harus membuat fungsi getter sendiri!

```sol
uint256 private favoriteNumber;

function getFavoriteNumber() public view returns(uint256) {
  return favoriteNumber;
}
```

Seperti yang mungkin sudah Anda tebak, `getFavoriteNumber` mengembalikan nilai yang disimpan dalam variabel private `favoriteNumber`, yang nilainya seharusnya tidak dapat diakses di luar ruang lingkup kontraknya.

Mari kita uraikan sisa deklarasi fungsi kita.

Sama seperti state variables, **fungsi adalah publik** jika mereka dapat dipanggil baik dari dalam kontrak (atau kontrak turunan) maupun dari akun lain — apakah itu akun yang dimiliki secara eksternal (EOA) atau kontrak pintar lain.

Setelah **public**, kita memiliki kata kunci **view**: ini memastikan bahwa fungsi tersebut **hanya dapat dibaca** dan tidak ada state variable yang dapat dimodifikasi dalam tubuhnya.

Terakhir, karena [Solidity adalah bahasa yang statis-bertipu](https://docs.soliditylang.org/en/v0.8.10/types.html), Anda harus menentukan tipe nilai yang dikembalikan oleh sebuah fungsi.

Secara umum, dalam Solidity, fungsi digunakan untuk mengambil atau mengatur informasi sebagai respons terhadap panggilan fungsi.

Jika sebuah fungsi membaca data apapun dari penyimpanan kontrak, maka itu disebut fungsi **view**, dan harus diberi anotasi dengan kata kunci **view**.

## Latihan

- Ubah state variable `greeting` menjadi `private`.
- Deklarasikan fungsi `public` bernama `getGreeting`.
- Fungsi `getGreeting` harus menjadi fungsi `view` yang mengembalikan nilai dari variabel `greeting`.

Catatan: dalam kasus nilai yang dikembalikan bertipe `string`, lokasi data mereka harus ditentukan. Kami akan menjelajahi apa itu lokasi data sebuah variabel pada pelajaran berikutnya.

Untuk tujuan latihan saat ini, gunakan sintaks ini:

```sol
returns(string memory _replace_with_it)
```
