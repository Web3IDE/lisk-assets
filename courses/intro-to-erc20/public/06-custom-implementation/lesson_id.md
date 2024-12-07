###### Implementasi ERC20 Kustom

Terkadang, open source mungkin tidak cukup untuk kasus penggunaan Anda dan Anda mungkin perlu membuat implementasi kustom dari awal.

Berikut adalah implementasi minimalis dari standar ERC20 yang melakukan semua yang seharusnya dilakukan. Implementasi ini dapat menanyakan saldo dari alamat manapun, menampilkan total suplai, memungkinkan pengguna untuk memberikan persetujuan kepada orang lain, ... Tapi tunggu - fungsi `transfer(address,uint256)` belum diimplementasikan.

Berikut adalah apa yang dikatakan [standar ERC20](https://eips.ethereum.org/EIPS/eip-20) tentang transfer token:

> Mentransfer jumlah token `_value` ke alamat `_to`, dan HARUS memicu peristiwa `Transfer`. Fungsi ini SEHARUSNYA `throw` jika saldo akun pemanggil pesan tidak cukup untuk dibelanjakan.
> 
> _Catatan_ Transfer dengan nilai 0 HARUS diperlakukan sebagai transfer normal dan memicu peristiwa `Transfer`.

Luangkan waktu sejenak untuk membaca kode yang ada. Fungsi `transferFrom(address,address,uint256)` mungkin sangat berguna untuk inspirasi.

## Latihan

- Implementasikan fungsi `transfer(address,uint256)` kustom agar sesuai dengan standar ERC20:
- Kurangi saldo pengirim. Solidity v0.8 secara otomatis `throws` revert jika Anda mencoba mengurangi angka yang lebih besar dari yang lebih kecil.
- Tambahkan saldo penerima
- Emit peristiwa `Transfer`
- Kembalikan `true`
