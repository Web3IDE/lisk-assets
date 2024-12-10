###### Kontrol akses

Ketika kita berbicara tentang kontrol akses, kita mengacu pada serangkaian kebijakan yang diberlakukan dalam kode kita yang membatasi akses ke fitur-fitur tertentu dalam smart control hanya untuk sekelompok entitas tertentu.

Dalam dunia pengembangan blockchain, kontrol akses merupakan konsep keamanan yang paling mendasar ketika mengembangkan smart contract.

Sifat kode on-chain yang tidak dapat diubah membuat bug sangat sulit untuk diperbaiki. Bahkan dalam kasus-kasus di mana [kontrak dapat ditingkatkan] (https://docs.openzeppelin.com/upgrades-plugins/1.x/writing-upgradeable), memperbaiki bug bukanlah tugas yang mudah.

Salah satu kelas kerentanan yang paling umum adalah, pada kenyataannya, kebijakan kontrol akses yang salah konfigurasi.

Tidak semua fungsi harus diekspos ke semua akun.

Sebagai contoh, mari kita lihat kontrak dasar berikut ini:

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
        // Abaikan jika seseorang mencoba menarik 0 atau jika mereka tidak memiliki Ether yang cukup untuk melakukan penarikan.
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

- `feeCollector`, yang dapat melakukan satu operasi istimewa
- `owner`, yang dapat melakukan semua operasi istimewa - termasuk mengelola identitas akun `feeCollector`.

Meskipun contoh ini sangat mendasar, contoh ini masih menyoroti perlunya peran dan tingkat izin yang berbeda dalam smart contract. Mempelajari bagaimana menyeimbangkan cakupan izin dan peran ini, pada kenyataannya, merupakan aspek penting lainnya dari kontrol akses berbasis peran.

Kontrol akses dapat bervariasi dari solusi dasar, di mana hanya ada satu entitas yang memiliki hak istimewa, hingga sistem yang lebih canggih dengan banyak peran dan tingkat izin.

Dalam pelajaran ini kita akan fokus pada skenario kontrol akses yang paling sederhana.

Lihatlah kontrak `AgorappNFT`. Apakah Anda melihat ada fungsionalitas yang harus dibatasi?

## Latihan

Dalam pelajaran terakhir, kita sudah mengimplementasikan fungsi mint. Namun berhati-hatilah! Saat ini, semua orang dapat memanggilnya - yang berarti siapa pun dapat membuat NFT Agorapp sebanyak yang mereka inginkan!

Untuk mengatasi masalah ini, kita perlu menambahkan batasan kontrol akses.

- Kontrak `AgorappNFT` harus menerima argumen bertipe `address` saat deployment.
- Pemanggilan `mintBadge` harus dibatasi.
- Pemanggilan yang tidak sah ke fungsi `mintBadge` harus dibatalkan dengan pesan error `UNAUTHORIZED_MINTER`
- Jangan menambahkan dependensi tambahan.
