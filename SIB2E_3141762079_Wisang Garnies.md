Nama  : Wisang Garnies Rineksa Panggalih

Kelas : SIB2E

Absen : 23

NIM   : 2141762079


# MEMBUAT RESUME TENTANG QUERY, UPDATE DATA, DELETE DATA, SERTA SORTNG DATA.
```
**QUERY** 

Query adalah syntax atau perintah yang di gunakan untuk mengakses dan mennampilkan data pada sistem database. Query memiliki kemampuan untuk mengatur data mana yang perlu di tampilkan sesuai yang kita anda inginkan. Selain itu, query dapat dipakai untuk membuat data dapat saling berinteraksi.
Ada tiga jenis query database pada SQL, yaitu :
•	DDL (Data Definiton Language)
•	DML (Data Manipulation Language)
•	DCL (Data Control Language)
Ketiga query tersebut berfungsi untuk membuat atau mendefinisikan objek-objek pada database seperti membuat tabel, memanipulasi database, mengontrol database.

```
```
**UPDATE**

Statement update berfungsi untuk memperbaruhi data dalam tabel. Hal ini memungkinkan anda untuk mengubah nilai dalam satu atau lebih kolom dari satu baris atau beberapa baris.
Cara menggunakan sintaks dasar dari Update yaitu sebagai berikut :
-	Pertama, tentukan nama tabel yang ingin anda perbaruhi datanya dengan menggunakan kata kuci update
-	Kedua, tentukan kolom mana yang ingin anda perbaruhi dan nilai baru dalam dalam klausa SET.
-	Ketiga, tentukan baris nama yang akan di perbaruhi menggunakan klausa WHERE. Klausa WHERE bersifat optional. Jika Anda mmenghilangkannya, Pernyataan Update tersebut akan mengubah semua baris dalam tabel.

```
```
**DELETE DATA**

Perintah DELETE di gunakan untuk menghapus baris data pada suatu tabel dalam database. Perintah DELETE dapat menghapus satu baris data dan dapat juga menghapus beberapa baris data sekaligus. Perintah DELETE biasanya dikombinasikan dengan suatu kondisi dimana baris data yang di hapus hanya sesuai dengan kondisi tersebut.
Dibawah ini adalah format perintah DELETE :
DELETE FROM table_name WHERE condition;

```
```
**SORTING DATA DALAM MONGODB**

MongoDB menyediakan daftar lengkap operator dan metode untuk menyimpan dan mengambil dokumen dari koleksi. Penyortiran di MongoDB dapat dilakukan dari berbagai perspektif; seperti urutkan berdasarkan tanggal dapat digunakan untuk mencetak dokumen dalam urutan menaik/turun sehubungan dengan bidang tanggal. Dalam posting tutorial MongoDB ini, kami telah membuat daftar beberapa kemungkinan cara untuk mengurutkan dokumen sehubungan dengan tanggal. Panduan ini terdiri dari beberapa contoh yang menunjukkan penggunaan $urutkan operator dengan metode agregat dan menyortir() metode. Kedua cara digunakan untuk mengambil dokumen berdasarkan fungsi tanggal.
Contoh penggunaan metode sort()
```
