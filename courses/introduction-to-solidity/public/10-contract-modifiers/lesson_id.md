Apa yang terjadi jika kita memiliki banyak fungsi yang hanya boleh dipanggil oleh pemilik kontrak?

Kita tentu bisa mengulang apa yang kita lakukan pada pelajaran sebelumnya dan menyalin ekspresi "require" ke mana pun diperlukan. Namun, pendekatan ini tidak akan sangat [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself). Kita berusaha untuk menjadi programmer yang baik, dan salah satu prinsip dasar adalah menghindari duplikasi kode kapan pun memungkinkan.

Masukkan **modifier**!

**Modifier digunakan untuk memodifikasi perilaku fungsi**.

Kita dapat menggunakannya untuk mengenkapsulasi logika ekspresi `require` yang berulang di dalamnya.

```sol
modifier greaterThanTwo(uint256 _number) {
  require(_number > 2, "number too small");
  _;
}
```

Pada contoh di atas, modifier `greaterThanTwo` akan selalu memastikan bahwa argumen `uint256` dari fungsi yang diterapkan padanya lebih besar dari 2.

Perhatikan `_` di akhir! Itu disebut **wildcard penggabungan**, dan ini memungkinkan kita untuk kembali ke alur normal fungsi setelah pemeriksaan dalam modifier berhasil dilakukan.

Modifier `greaterThanTwo` dapat diterapkan ke fungsi dengan cara berikut:

```sol
pragma solidity 0.8.10;

contract FavoriteNumber {
  uint256 public myFavoriteNumber;

  modifier greaterThanTwo(uint256 _number) {
      require(_number > 2, "number too small");
      _;
  }

  function setFavoriteNumber(uint256 _myFavoriteNumber) public greaterThanTwo(_myFavoriteNumber) {
      myFavoriteNumber = _myFavoriteNumber;
  }
}
```

Pada kontrak di atas, fungsi `setFavoriteNumber` akan melemparkan pengecualian jika `_myFavoriteNumber` kurang dari 3 dan akan berjalan seperti yang diharapkan jika sebaliknya.

Perhatikan bahwa modifier tidak harus menerima argumen.

## Latihan

- Hapus pernyataan `require` yang dibuat pada pelajaran sebelumnya.
- Deklarasikan modifier bernama `isOwner`.
- Di dalam tubuh modifier, deklarasikan pernyataan `require` yang memastikan bahwa pemanggil fungsi harus pemilik kontrak.
- Terapkan modifier ke fungsi `setGreeting`.
