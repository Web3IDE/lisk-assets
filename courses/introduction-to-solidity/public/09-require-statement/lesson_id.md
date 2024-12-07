Salah satu cara **msg.sender** dapat sangat penting adalah dalam menerapkan logika **kontrol akses** pada kontrak.

Saat ini, siapa saja dapat memanggil fungsi `setGreeting` dan mengubah nilai variabel status `greeting` ke argumen string yang mereka pilih. Bagaimana kita bisa memastikan bahwa hanya kita - pihak yang menerapkan kontrak - yang diizinkan untuk mengubah variabel `greeting`?

Pada pelajaran sebelumnya, kita mendefinisikan variabel `owner`, yang akan selalu setara dengan kita - pihak yang menerapkan kontrak. Ini berarti yang perlu kita lakukan adalah memeriksa apakah `msg.sender` yang memanggil fungsi `setGreeting` sama dengan alamat `owner`. Jika iya, maka semuanya akan berjalan seperti biasa. Jika tidak, maka kita harus melemparkan pengecualian, yang akan mencegah logika `setGreeting` lainnya dijalankan.

Kita bisa menggunakan fungsi **membutuhkan** untuk mencapai hal ini:

```sol
function myFunction() public {
  require(firstValue == secondValue, "condition not satisfied");
}
```

Pada contoh di atas, kita bisa melihat bahwa `require` **menerima kondisi dan pesan kesalahan sebagai argumen**. Jika kondisi tersebut tidak terpenuhi, maka pengecualian akan dilemparkan, dan tidak ada perubahan yang akan disimpan di kontrak.

## Latihan

- Tambahkan pernyataan `require` pada baris pertama tubuh fungsi `setGreeting`.
- Pernyataan `require` perlu memastikan bahwa fungsi `setGreeting` hanya bisa dipanggil oleh pemilik kontrak.
- Pernyataan `require` perlu melemparkan string `caller is not the owner` jika kondisi yang diassert tidak terpenuhi.
