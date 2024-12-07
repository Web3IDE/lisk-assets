###### Saldo dan transfer

***Saldo dan Total Pasokan***

Saldo saat ini dari alamat mana pun dapat diambil menggunakan fungsi standar `balanceOf(address)`. Cara saldo tersebut disimpan tergantung pada pengembang token. Namun, dalam kebanyakan kasus, solusi optimal adalah dengan menyimpan saldo dalam `mapping` di mana setiap kunci mewakili pemilik token dan nilai yang sesuai mewakili saldo mereka saat ini. Semua nilai dalam mapping sudah 0 secara default, jadi Anda tidak perlu melakukan pengaturan awal untuk saldo.

Ini juga cara implementasi sumber terbuka menyimpan saldo token.

_OpenZeppelin `ERC20.sol`:_  

```
mapping(address account => uint256) private _balances;

function balanceOf(address account) public view virtual returns (uint256) {
	return _balances[account];
}
```

Namun, karena tidak ada cara mudah untuk mengambil semua nilai dalam `mapping` atau untuk menjumlahkannya, kita perlu menyimpan total pasokan secara terpisah. Total pasokan menunjukkan jumlah semua saldo yang digabungkan.

Standar mengharuskan kita juga mengembalikan nilai gabungan ini menggunakan fungsi `totalSupply()`.

_OpenZeppelin `ERC20.sol`:_  

```
uint256 private _totalSupply;

function totalSupply() public view virtual returns (uint256) {
	return _totalSupply;
}
```

***Transfer***

Kita dapat mentransfer token menggunakan fungsi `transfer(address,uint256)`. Argumen pertama adalah penerima token, dan argumen kedua adalah jumlah token yang ingin kita transfer.

Perhatikan bahwa kita tidak menentukan pengirim token. Itu karena token secara default dikirim dari alamat mana saja yang memanggil fungsi ini. Kita akan membahas pengiriman token atas nama orang lain di pelajaran berikutnya.

Jika transfer token berhasil, fungsi `transfer(address,uint256)` perlu mengembalikan `true` dan memancarkan acara `Transfer(address,address,uint256)`. Argumen acara tersebut menunjukkan pengirim token, penerima, dan jumlah. Memancarkan acara sering kali berguna untuk aplikasi offchain (pikirkan Etherscan dan pelacak token lainnya) karena mereka dapat membaca acara ini dan membangun database mereka sendiri mengenai transfer per alamat, riwayat transfer, dan jenis data terindeks dan dapat dicari lainnya yang akan lebih sulit untuk diambil hanya dari buku besar blockchain mentah.

Saat Anda memeriksa implementasi OpenZeppelin, Anda dapat melihat bahwa mereka juga memanggil `_beforeTokenTransfer(address,address,uint256)` dalam fungsi `transfer(address,uint256)` mereka. Ini memungkinkan Anda untuk menambahkan fitur kustom seperti memancarkan acara baru atau membatasi transfer oleh pengguna yang diblacklist.

_OpenZeppelin `ERC20.sol`:_  

```
function transfer(address to, uint256 amount) public virtual override returns (bool) {
	address owner = _msgSender();
	_transfer(owner, to, amount);
	return true;
}

function _transfer(
	address from,
	address to,
	uint256 amount
) internal virtual {
	require(from != address(0), "ERC20: transfer from the zero address");
	require(to != address(0), "ERC20: transfer to the zero address");

	_beforeTokenTransfer(from, to, amount);

	// ...
}
```

## Latihan

- Override fungsi OpenZeppelin `_beforeTokenTransfer(address,address,uint256)`. Buatlah untuk memancarkan acara baru `VitalikTransfer` - tetapi hanya jika ada transfer ke atau dari alamat Vitalik `0xd8dA6BF26964aF9D7eEd9e03E53415D37aA96045`.
