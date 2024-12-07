Fungsi konstruktor adalah jenis fungsi khusus yang **hanya dijalankan sekali saat kontraknya diterapkan**.

Jika Anda memiliki pengalaman dengan bahasa pemrograman berorientasi objek, Anda mungkin sudah familiar dengan konsep ini.

Kita dapat menggunakan fungsi konstruktor untuk mengatur nilai awal dari variabel status kontrak pada saat penerapan.

```sol
contract MyFavoriteNumber {
  uint256 public myFavoriteNumber;

  constructor(uint256 _myFavoriteNumber) {
    myFavoriteNumber = _myFavoriteNumber;
  }
}
```

Pada contoh di atas, konstruktor mengatur variabel `myFavoriteNumber` agar nilainya sama dengan argumen `_myFavoriteNumber`-nya. Oleh karena itu, jika kontrak `myFavoriteNumber` diterapkan dengan nilai 4, maka nilai awal dari variabel status `myFavoriteNumber` akan menjadi 4.

Demikian juga, jika kontrak `MyFavoriteNumber` diterapkan dengan nilai 13, maka nilai awal dari variabel status `myFavoriteNumber` akan menjadi 13.

## Latihan

- Tambahkan konstruktor ke kontrak `Greeter` kami.
- Konstruktor tersebut harus menerima satu argumen bertipe string.
- Di dalam tubuh konstruktor, atur nilai variabel status publik `greeting` dengan nilai dari argumen string konstruktor.
