###### Kontrol akses

Ketika kita berbicara tentang kontrol akses, kita merujuk pada serangkaian kebijakan yang diterapkan dalam kode kita untuk membatasi akses ke fitur tertentu dalam smart contract hanya untuk kelompok entitas tertentu.

Dalam pengembangan blockchain, kontrol akses adalah konsep keamanan paling dasar saat mengembangkan smart contract.

Sifat kode on-chain yang tidak dapat diubah membuat bug menjadi sangat sulit untuk diperbaiki. Bahkan dalam kasus-kasus di mana [kontrak dapat diupgrade] (https://docs.openzeppelin.com/upgrades-plugins/1.x/writing-upgradeable), memperbaiki bug bukanlah tugas yang mudah.

Salah satu jenis kerentanan yang paling umum adalah kesalahan konfigurasi kebijakan kontrol akses.

Tidak setiap fungsi harus dapat diakses oleh semua akun.

Sebagai contoh, mari kita lihat kontrak dasar berikut:

```sol
pragma solidity 0.8.10;

contract Bank {
    address public owner;
    address public feeCollector;
    uint256 public bankFee;
    uint256 public collectedFees;
    mapping (address => uint) public balances;

    constructor(address _feeCollector, uint256 _bankFee) {
        owner = msg.sender;
        feeCollector = _feeCollector;
        bankFee = _bankFee;
    }

    function deposit() external payable {
        require(msg.value > bankFee, "Deposit must be greater than bank fee");
        collectedFees += bankFee;
        balances[msg.sender] += msg.value - bankFee;
    }

    function withdraw(uint256 amount) external {
        // Lewati jika seseorang mencoba menarik 0 atau jika mereka tidak memiliki cukup Ether untuk melakukan penarikan.
        require(balances[msg.sender] >= amount);
        balances[msg.sender] -= amount;
        payable(msg.sender).transfer(amount);
    }

    function collectFees() external {
        require(msg.sender == feeCollector || msg.sender == owner, "account not authorized to collect fees");
        payable(msg.sender).transfer(collectedFees);
        collectedFees = 0;
    }

    function setFeeCollector(address _newFeeCollector) external {
        require(msg.sender == owner, "account not authorized to set fee collector");
        feeCollector = _newFeeCollector;
    }
}
```

Ada dua peran istimewa:

- `feeCollector`, yang memiliki wewenang untuk melakukan satu operasi istimewa.
- `owner`, yang memiliki wewenang penuh untuk melakukan semua operasi istimewa, termasuk mengelola identitas `feeCollector`.

Meskipun contoh ini sederhana, ini menunjukkan perlunya memiliki peran dan tingkat izin yang berbeda dalam smart contract. Mempelajari cara menyeimbangkan cakupan izin dan peran adalah aspek penting dalam kontrol akses berbasis peran.

Kontrol akses dapat berkisar dari solusi sederhana, di mana hanya ada satu entitas istimewa, hingga sistem yang lebih kompleks dengan banyak peran dan tingkat izin.

Dalam pelajaran ini, kita akan fokus pada skenario kontrol akses yang paling sederhana.

Perhatikan kontrak `AgorappNFT`. Apakah Anda melihat ada fungsi yang perlu dibatasi?

---

## **Latihan**

Pada pelajaran terakhir, kita mengimplementasikan fungsi mint. Namun, perhatikan bahwa saat ini **semua orang** dapat memanggil fungsi tersebut—yang berarti siapa saja dapat mencetak sebanyak mungkin Agorapp NFT yang mereka inginkan!

Untuk mengatasi masalah ini, kita perlu menambahkan batasan kontrol akses.

1. Kontrak `AgorappNFT` harus menerima argumen bertipe `address` saat deployment.
2. Pemanggilan `mintBadge` harus dibatasi.
3. Pemanggilan yang tidak sah ke fungsi `mintBadge` harus dibatalkan dengan pesan error `UNAUTHORIZED_MINTER`.
4. Jangan menambahkan dependensi tambahan.
