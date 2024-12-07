Mari kita mulai dengan membahas dasar-dasar tata letak file Solidity.

Semua file Solidity memerlukan pernyataan `pragma` yang ditempatkan di bagian paling awal. Pernyataan pragma memastikan bahwa kode dalam file tersebut akan menggunakan versi compiler Solidity yang kompatibel.

Karena Solidity adalah bahasa yang terus berkembang, fitur baru sering kali ditambahkan atau dihapus dengan setiap rilis. Perubahan ini mengikuti aturan [versi semantik](https://semver.org/).

```sol
pragma solidity 0.8.0;
```

Pada pernyataan pragma di atas, kita menegaskan bahwa kode yang mengikuti hanya dapat dikompilasi oleh compiler versi 0.8.0. Mencoba untuk mengkompilasi file yang sama dengan versi compiler lainnya akan menghasilkan kesalahan.

Namun, pernyataan pragma juga dapat memungkinkan fleksibilitas.
Anda dapat menggunakan simbol caret (`^`) untuk menunjukkan bahwa kode dapat dikompilasi dengan versi compiler mana pun yang kompatibel dengan versi yang ditentukan:

```sol
pragma solidity ^0.8.2;
```

Pada cuplikan kode di atas, kita menegaskan bahwa versi compiler antara **0.8.2** dan perubahan besar berikutnya - dalam kasus ini, **0.9.0** - akan dapat mengkompilasi file kita.

Terakhir, setelah mendeklarasikan versi compiler, kita dapat mendeklarasikan kontrak kita. **Kontrak** mirip dengan kelas dalam pemrograman berorientasi objek. Sebagian besar logika dalam kode kita akan terkapsulasi dalam kontrak-kontrak.

Deklarasi kontrak adalah sebagai berikut:

```sol
contract FirstContract {}
```

## Latihan

Seperti halnya tradisi untuk memulai pembelajaran bahasa pemrograman baru dengan program "Hello World", dalam kursus ini kita akan membuat kontrak `Greeter`.

- Tentukan versi compiler Solidity yang kompatibel antara 0.8.0 dan perubahan besar berikutnya (0.9.0)
- Deklarasikan kontrak kosong dan beri nama `Greeter`
