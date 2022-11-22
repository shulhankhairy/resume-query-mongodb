# RESUME QUERY, UPDATE, DELETE, DAN SORTING
## NAMA  : RIZQI ZAMZAMI JAMIL
## NIM   : 2141762089
## KELAS : SIB-2E
## ABSEN : 19
---
## | QUERY |
---
Query merupakan sintaks permintaan data dari suatu database. MongoDB memiliki cara query tersendiri dalam mengolah data dari database. Query dalam mongoDB memiliki format JSON.
---
JSON sendiri adalah JavaScript Object Notation. Format yang digunakan untuk menyimpan atau mentransfer data. 
---
JSON memiliki 2 struktur, yaitu:
* Value yang saling berpasangan (object)
* Daftar dari value yang berurutan (array)
---

## Contoh Query
---
```js
db.movies.insert(
    {id: 1,
    title: 'Spiderman-No Way Home', 
    description: 'Peter Parker lupa ingatan',
    studios: 'Marvel',
    genre: ['action', 'drama', 'super power'],
    rating: 89}
)
```
---
Query diatas merupakan query pemasukan data (insert) dari movie dengan judul “Spiderman-No Way Home” dengan format query adalah db.namaCollection.insert().
---
* Fungsi {} menandakan isi baris kemudian diikuti dengan namakolom : isi kolom
* Fungsi [] menandakan bahwa data didalamnya merupakan tipe array (banyak value)
---
## | UPDATE DATA | 
Apabila ingin merubah data atau value(isi data) dari suatu collection(tabel), maka menggunaakan format query berikut ini:
---
`db.namaCollection.update({kondisi},{ $set:{datayangdiubah}})`
---
Contoh Penggunaan
---
```js
db.movies.update(
    {"id" : 1},
    {$set: 
        {"rating" : 95}
    }
)
```
Keterangan
* "id" merupakan baris yang akan dirubah atau kondisi perubahan data(seperti where pada sql)
* $set: merupakan sintaks pembaruan data(seperti set pada sql)
---
## | Delete |
---
Apabila ingin menghapus data atau dokumen dari suatu collection(tabel), maka menggunakan format berikut ini:
---
`db.namaCollection.deleteOne({kondisi})` dan `db.namaCollection.deleteMany({kondisi})` untuk menghapus data atau dokumen banyak
---
Contoh penggunaan
---
```js
db.movies.remove(
    {"id" : 1}
)
```
Keterangan
---
* id merupakan kondisi spesifik dokumen yang akan dihapus

## | Sorting |
---
Sorting digunakan untuk mengurutkan data.
---
Terdapat 2 sorting yaitu besar ke kecil atau kecil ke besar.
---
Kondisi
---
* `db.namaCollection.find().sort("name", 1)` sebagai kecil ke besar
* `db.namaCollection.find().sort("name", -1)` sebagai besar ke kecil
---
Contoh penggunaan
```js
db.movies.find().sort({id:1})
{"id": 1},
{"id": 2},
{"id": 3}
```