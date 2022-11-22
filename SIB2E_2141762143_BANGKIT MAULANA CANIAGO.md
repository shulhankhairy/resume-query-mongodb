--
## RESUME QUERY , UPDATE , DELETE DAN SORTING
---

### Bangkit Maulana Caniago
### 2141762143
### SIB-2E


---
## **Pengertian Query**
---

Arti query pada bahasa pemrograman komputer adalah informasi yang diterima ataupun diambil dari suatu database. Hal tersebut berguna untuk memanipulasi, menambah, menghapus serta mengubah data. Query juga sering disebut dengan bahasa kueri.

---
## **Update Data**
---
\
Untuk mengubah data, kita bisa menggunakan fungsi **`update()`**

``` 
db.<koleksi>.update(<query>, <data baru>) 
```

Keterangan :
- `<query>` adalah kata kunci data yang akan kita ubah, sama seperti `WHERE` dalam SQL
- `<data baru>` adalah data barunya 

Sekarang mari coba mengubah harga bukunya dari **98000** menjadi **75000**.

```
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
```

Maka hasilnya, semua buku yang berjudul **"Pemrograman Javascript dan MongoDB"** akan diturunkan harganya menjadi **75000**.

![alt text](https://www.petanikode.com/img/mongodb/update-data.png)



---
## **Menghapus Data**
---
\
Untuk menghapus data, kita bisa menggunakan fungsi **`remove()`**

``` 
db.<koleksi>.remove(<query>) 
```

Sama seperti update data, penghapusan data juga memiliki **`<query>`** untuk menentukan data yang akan dihapus.

Contoh:
Kita akan menghapus buku yang berjudul **"Belajar MongoDB"**, karena stoknya sudah habis 

```
db.buku.remove({judul: "Belajar MongoDB"})
```

Maka data buku yang berjudul **"Belajar MongoDB"** sudah tiada.

![alt text](https://www.petanikode.com/img/mongodb/hapus-data.png)

``` 
db.<koleksi>.remove({}) 
```

---
## **Sorting Data**
---
\
Untuk mengurutkan data, kita bisa menggunakan fungsi **`sort()`**

``` 
db.collection_name.find().sort({FieldName1: sort order 1 or -1, FieldName2: sort order})
```
Contoh jika kita mempunyai data seperti ini :
```
{ "_id" : ObjectId(5983548781331abf45ec5), "topic":"Cyber Security"}
{ "_id" : ObjectId(5565548781331aef45ec6), " topic ":"Digital Privacy"}
{ "_id" : ObjectId(5983549391331abf45ec7), " topic ":"Application Security Engineering"}
```

Jika kita ingin mendapatkan data terurur secara **`ascending`** , kita akan melakukan perintah :

```
db.techSubjects.find({}, {"topic":1, _id:0}).sort({"topic":1})
```
Maka, kita akan mendapatkan hasil topic yang terurut

![alt text](https://www.w3schools.in/wp-content/uploads/2019/06/sort-method-MongoDB.jpg?ezimgfmt=rs:531x94/rscb18/ng:webp/ngcb18)

\

---
## Referensi
---

[https://www.petanikode.com/tutorial-dasar-mongodb/](https://www.petanikode.com/tutorial-dasar-mongodb/)
[https://www.w3schools.in/mongodb/sorting](https://www.w3schools.in/mongodb/sorting)