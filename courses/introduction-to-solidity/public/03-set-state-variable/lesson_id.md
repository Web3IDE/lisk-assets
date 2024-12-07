Saat Anda ingin menyimpan data yang persisten pada kontrak Anda, Anda perlu menggunakan **state variables** - nilai yang disimpan secara permanen di blockchain Ethereum melalui kontrak Anda.

State variables bisa berupa berbagai tipe, seperti **uint, bytes, address, bool, string**. Untuk daftar lengkap [kunjungi tautan ini](https://docs.soliditylang.org/en/v0.8.10/types.html).

Berikut adalah contoh bagaimana mendefinisikan state variable pada kontrak:

```sol
contract Greeter {
  uint256 public myFavoriteNumber;
}
```

## Akun

Entitas yang dapat berinteraksi dengan kontrak pintar disebut **akun**. Di jaringan Ethereum, ada dua jenis:

- **Akun yang dimiliki secara eksternal (EOA)**: Umumnya dianggap sebagai akun pengguna, EOA dikendalikan oleh seseorang dengan dompet Ethereum.
- **Akun kontrak**: Ini adalah alamat tempat kontrak pintar berada.

Baik EOA maupun akun kontrak dapat berinteraksi dengan kontrak Anda. Namun, penting untuk dicatat bahwa transaksi hanya dapat dimulai oleh EOA.

## Visibilitas

Tidak semua orang dapat mengakses state variable. State variable dapat memiliki berbagai tingkat **visibilitas**, yang menentukan siapa yang dapat berinteraksi dengan mereka.

### Publik

State variable publik dapat diakses oleh siapa saja, baik dari dalam kontrak maupun dari luar kontrak:

```sol
uint256 public myFavoriteNumber;
```

### Pribadi

State variable pribadi hanya dapat diakses dari dalam kontrak tempat variabel itu didefinisikan:

```sol
uint256 private mySecretNumber;
```

### Internal

State variable internal tidak dapat diakses dari luar kontrak. Namun, ia dapat diakses dari **kontrak anak**.

Solidity adalah bahasa pemrograman berorientasi objek dan mendukung pewarisan. Kontrak anak adalah kontrak yang mewarisi kontrak lain:

```sol
contract ParentContract {
  uint256 internal myInternalNumber;
}

contract ChildContract is ParentContract {

  // ChildContract dapat mengakses myInternalNumber

}
```

## Latihan

- Deklarasikan sebuah state variable bernama `greeting` dengan tipe string.
- Pastikan bahwa akun mana pun dapat melakukan query terhadapnya!
