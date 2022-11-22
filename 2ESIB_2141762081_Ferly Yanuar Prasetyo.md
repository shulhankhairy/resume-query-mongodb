Nama : Ferly Yanuar Prasetyo
NIM : 2141762081
No Absen : 06

QUERY

Query adalah permintaan data dari database. Permintaan harus diajukan dalam bentuk tabel database atau kombinasi tabel menggunakan kode yang disebut dengan bahasa kueri. 
Dengan begitu, sistem bisa memahami dan memproses kueri yang sesuai. query adalah permintaan informasi. Begitu juga dalam bahasa pemrograman komputer, query atau kueri 
mengacu pada permintaan informasi, tapi informasi ini diambil dari database. Penulisan query memerlukan serangkaian kode yang telah ditentukan agar database bisa memahami instruksi yang diberikan.
Nah, kode ini umumnya disebut sebagai bahasa query. MongoDB adalah database yang memiliki kemampuan untuk menangani query dengan baik. Selain itu, akses terhadap data juga mudah dilakukan 
sehingga Anda dapat  melihat hasil suatu data yang rumit atau tak terstruktur dengan cepat. 

Bahasa yang digunakan sebagai standar untuk DBMS adalah Structured Query Language (SQL), sedangkan bahasa query lain yang bisa memudahkan komunikasi database meliputi AQL, Datalog, dan DMX.
Berbeda dengan SQL, MongoDB ada cara query tersendiri untuk mengolah data. Tabel di MongoDB biasa disebut collection dan query untuk mencari data tertentu disebut sebagai criteria.  
Berikut ini adalah contoh query MongoDB :

1. Mencari Data Dalam Array of Object Dengan dan Tanpa elemMatch
Misal ada kolom berisi data suatu array.

Query MongoDB mencari detail description berisi “example description”.

db.getCollection('example_collection').findOne({"description.detail": "example description"})

Query diatas bisa juga diganti dengan elemMatch dimana berdasarkan pengalaman memiliki performansi yang lebih baik ketika data kita banyak

db.getCollection('example_collection').find({description: {$elemMatch: {language: "id", detail: "contoh deskripsi"}}})

2. Update Data 

Untuk mengubah data, kita bisa menggunakan fungsi update().

db.<koleksi>.update(<query>, <data baru>)
Keterangan:

<query> adalah kata kunci data yang akan kita ubah, sama seperti WHERE dalam SQL.
<data baru> adalah data barunya.
Sekarang, mari kita coba mengubah harga bukunya dari 98000 menjadi 75000.

db.buku.update(
    {
        judul: "Pemrograman Javascript dan MongoDB"
    },
    {
        judul: "Pemrograman Javascript dan MongoDB",
        sinopsis: "Panduan Pemrograman Js dan MongoDB",
        pengarang: "Petani Kode",
        harga: 75000
    }
)
Maka hasilnya, semua buku yang berjudul "Pemrograman Javascript dan MongoDB" akan diturunkan harganya menjadi 75000.

3. Delete Data

Untuk menghapus data, kita bisa menggunakan perintah remove().

db.<koleksi>.remove(<query>)
Sama seperti update data, penghapusan data juga memiliki <query> untuk menentukan data yang akan dihapus.

Contoh:

Kita akan menghapus buku yang berjudul "Belajar MongoDB", karena stoknya sudah habis 😄.

db.buku.remove({judul: "Belajar MongoDB"})
Maka data buku yang berjudul "Belajar MongoDB" sudah tiada.

Update Data
Untuk menghapus semua data dalam koleksi, kita bisa kosongkan nilai query-nya.

db.<koleksi>.remove({})
Menhapus Dabase dan Koleksi
Bila kita ingin menghapus database dan koleksi, kita bisa menggunakan method drop() dan dropDatabase().

Menghapus koleksi:

db.<koleksi>.drop();
Menghapus database:

db.dropDatabase();

4, Sorting Data

Menggunakan operator $sort: NS $urutkan operator digunakan di dalam pengumpulan() metode dan Anda dapat menggunakan sintaks berikut untuk menerapkan $urutkan operator:

db.collection-name.aggregate({$urutkan: {<bidang tanggal>: <memesan>}})

Dalam sintaks di atas, contoh yang digunakan adalah:

nama-koleksi: Mengacu pada nama koleksi tempat Anda ingin menerapkan metode ini.
: Harus diganti dengan nama field yang berisi fungsi tanggal.
: Mewakili urutan; dan akan ditukar dengan “1” untuk naik atau “-1” untuk urutan menurun.
Bagian yang akan datang berisi beberapa contoh yang menjelaskan konsep menyortir() metode dan $urutkan operator untuk mengurutkan dokumen berdasarkan tanggal.