# lab2web
Hardi Wirkan 312210492 

## Belajar PHP Dasar
![Screenshot (292)](https://github.com/Hardi219/Lab2_Web/assets/129932048/9ae86864-e568-4b3c-b524-4b2ef377d426)

Hasil:

![Screenshot (290)](https://github.com/Hardi219/Lab2_Web/assets/129932048/0ea12d5c-a7f7-44c7-8818-d0456ca4e22e)


## Menggunakan Variable
![Capture](https://github.com/Hardi219/Lab2_Web/assets/129932048/7664eb74-0cd9-4b80-ab03-6ab7757ac01f)

Hasil:

![Screenshot (294)](https://github.com/Hardi219/Lab2_Web/assets/129932048/9c700b08-8746-4e17-858e-4d60f59c6c69)


## Form Input
![Code_8pCIUg5wi3](https://github.com/steprtm/lab2web/assets/129705802/a06d70eb-ac57-499b-aa90-8adaeca21364)

Hasil:

![Screenshot (296)](https://github.com/Hardi219/Lab2_Web/assets/129932048/51b13854-6142-4742-aba6-c142cf303837)


## Tugas
![Screenshot (298)](https://github.com/Hardi219/Lab2_Web/assets/129932048/945e1743-25b1-48c8-8241-772986745072)

Hasil:

![Screenshot (297)](https://github.com/Hardi219/Lab2_Web/assets/129932048/692910ca-b685-4109-8717-f1d21970e0af)


## Penjelasan
1. Struktur HTML
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>PHP Dasar</title>
</head>
<body>
    <h2>Form Input</h2>
    <form method="post">
        <label>Nama: </label>
        <input type="text" name="nama">
        <label>Tanggal Lahir: </label>
        <input type="date" name="tanggal_lahir">
        <label>Pekerjaan: </label>
        <select name="pekerjaan">
            <option value="Operator">Operator</option>
            <option value="Developer">Developer</option>
            <option value="Manager">Manager</option>
        </select>
        <input type="submit" value="Kirim">
    </form>
```
**Input Nama:** Pengguna memasukkan nama mereka.

**Input Tanggal Lahir:** Pengguna memilih tanggal lahir menggunakan kontrol input tanggal.

**Pilihan Pekerjaan:** Pengguna memilih pekerjaan dari dropdown, yang akan mempengaruhi perhitungan gaji.

2. Logika PHP, Proses Formulir
```
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST" && isset($_POST['nama']) && isset($_POST['tanggal_lahir']) && isset($_POST['pekerjaan'])) {
    $nama = htmlspecialchars($_POST['nama']);
    $tanggal_lahir = $_POST['tanggal_lahir'];
    $pekerjaan = $_POST['pekerjaan'];
```
**Pengecekan Metode dan Data:** Memeriksa apakah formulir telah dikirim menggunakan metode POST dan semua data yang diperlukan ada.

**Sanitisasi Input:** Fungsi htmlspecialchars digunakan untuk menghindari serangan XSS (Cross-Site Scripting) dengan membersihkan input nama dari tag HTML atau karakter khusus.

3. Kalkulasi Umur
```
    $birthdate = new DateTime($tanggal_lahir);
    $today = new DateTime('today');
    $age = $birthdate->diff($today)->y;
```
**Objek DateTime:** Digunakan untuk memanipulasi tanggal dengan mudah.

**Perhitungan Selisih Tahun:** Menghitung selisih tahun antara tanggal lahir dan hari ini untuk mendapatkan umur.

4. Perhitungan Gaji dan Pajak
```
    $salaries = [
        "Operator" => 1000000,
        "Developer" => 3000000,
        "Manager" => 5000000
    ];
    $taxRates = [
        "Operator" => 0.1,
        "Developer" => 0.15,
        "Manager" => 0.2
    ];
    $gaji = isset($salaries[$pekerjaan]) ? $salaries[$pekerjaan] : 0;
    $pajak = isset($taxRates[$pekerjaan]) ? $taxRates[$pekerjaan] : 0;
    $thp = $gaji - ($gaji * $pajak);
```

**Array:** Menyimpan nilai gaji dan pajak berdasarkan jenis pekerjaan.

**Kalkulasi Gaji Bersih:** Menghitung gaji bersih dengan mengurangkan pajak dari gaji kotor.

5. Menampilkan Hasil
```
    echo "Selamat Datang $nama<br>";
    echo "Usia Anda: $age tahun<br>";
    echo "Pekerjaan: $pekerjaan<br>";
    echo "Gaji sebelum pajak = Rp. " . number_format($gaji, 0, ',', '.') . "<br>";
    echo "Gaji yang dibawa pulang = Rp. " . number_format($thp, 0, ',', '.');
}
?>
</body>
</html>
```
**Output:** Menggunakan echo untuk menampilkan teks dan data yang diproses ke pengguna.




