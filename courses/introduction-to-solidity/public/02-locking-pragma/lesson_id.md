Pada pelajaran sebelumnya, kita mengatur pragma kontrak kita ke sebuah nilai yang mendukung rentang versi compiler. Ini juga disebut **floating pragma**.

**Floating pragma** dianggap berbahaya.

Ketika pragma tidak diatur ke versi compiler yang spesifik, sebuah kontrak mungkin dikompilasi dengan versi compiler yang lebih lama atau lebih baru dari yang digunakan selama pengembangan dan pengujian lokal. Hal ini dapat menyebabkan inkonsistensi atau membuka kontrak terhadap **bug yang belum ditemukan** yang mungkin memengaruhi versi compiler yang lebih baru.

Sebagai akibatnya, mengunci pragma ke versi compiler yang spesifik [merupakan praktik keamanan yang disarankan](https://consensys.github.io/smart-contract-best-practices/development-recommendations/solidity-specific/locking-pragmas/).

## Latihan

- Kunci compiler Solidity ke versi `0.8.10`
