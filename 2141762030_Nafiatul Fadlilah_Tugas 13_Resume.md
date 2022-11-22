

### NIM: 2141762030
### Nama: Nafiatul Fadlilah (13)
### Kelas: SIB2E
### Tugas: Update, Delete, & Sorting Data di MongoDB

--------------------------------------------------------------------------------------------------------------------------------------------
#### **Update**

- **Method update() dalam MongoDB digunakan untuk** memperbarui dokumen dalam *collection* MongoDB. Dokumen tertentu diperbarui dengan menggabungkan kriteria baru dengan pernyataan pembaruan dan hanya akan memperbarui dokumen yang dipilih. Kondisi tertentu dimasukkan dalam bentuk parameter / *argument* untuk memperbarui dokumen di MongoDB. 

- Berikut representasi cara memperbarui dokumen dalam MongoDB:
1. Menggunakan method update().
2. Menentukan id dari dokumen yang ingin diperbarui.
3. Menggunakan *set command* untuk memodifikasi *field name*.
4. Memilih nama *field* yang ingin diubah kemudian memasukkan nilai baru.

- Berikut contoh penerapan method update():
`
db.musicians.update(
    {_id: 4},
    {
        $set: { instrument: [“Vocals”, “Violin”, “Octapad”]}
    }
)
`

- Karakteristik update di MongoDB:
a. Jika *field* tidak ada dalam *current document*, operator **$set** akan memasukkan field baru dengan nilai yang ditentukan sampai dan kecuali itu melanggar batasan tipe. 
b. Pengguna MongoDB juga dapat menggunakan `{ multi: true}` untuk memperbarui *multiple document* yang memenuhi kriteria query. 
c. Memanfaatkan `{upsert: true}` untuk membuat dokumen baru juga dimungkinkan karena tidak ada dokumen yang disertakan dengan query.

- Macam-macam query update di MongoDB:
1. updateOne()
method ini akan memperbarui dokumen yang pertama ditemukan cocok dengan query yang disediakan. 
Contoh sintaks:
`db.posts.updateOne( {title: “Post Title 1” }, { $set: { likes: 2} } )`
2. updateMany()
method ini akan memperbarui semua dokumen yang cocok dengan query yang disediakan. 
Contoh sintaks: 
`db.posts.updateMany({}, {$inc: { likes: 1 } })`

--------------------------------------------------------------------------------------------------------------------------------------------

#### **Delete**

MongoDB memungkinkan untuk menghapus dokumen atau dokumen kolektif menggunakan salah satu dari 3 metodenya, yaitu:
1. db.collection.deletOne()
method ini digunakan untuk meghapus satu dokumen saja, meskipun terdapat lebih dari satu dokumen yang sesuai dengan kriteria. 
Berikut contoh sintaks untuk menghapus satu dokumen:
`db.programmers.deleteOne( { name: { $in: [ "Dennis Ritchie", "Bjarne Stroustrup"] } } )`
2. db.collection.remove()
MongoDB dapat menghapus semua dokumen yang ada dalam koleksi hanya dengan mengecualikan kriteria filter yang disebutkan dalam tanda kurung () dan menentukan nama dokumen di dalamnya. 
Berikut contoh sintaks:
`db.programmers.remove( { name: "James Gosling" } )`
3. db.collection.deleteMany()
MongoDB memungkinkan penghapusan *multiple document* menggunakan method db.collection.deleteMany(). Method tersebut menghapus semua dokumen yang sesuai dengan kriteria yang disebutkan dalam parameter / *argument*. 
Berikut contoh sintaks:
`db.programmers.deleteMany( { name: { $in: [ "Dennis Ritchie", "Bjarne Stroustrup" ] } } )`

--------------------------------------------------------------------------------------------------------------------------------------------

#### **Sorting**

- **Pengurutan (*Sorting*) merupakan** peningkatan maupun penurunan berdasarkan sejumlah hubungan linier antara berbagai item data yang berada dalam basis data. *Sorting* dapat dilakukan pada entitas seperti informasi (yang mencakup nama dan fakta), angka, serta catatan. *Sorting* meningkatkan keterbacaan dan keseragaman data yang ditampilkan dari database.

- **Method sort() digunakan untuk** mengurutkan dokumen di MongoDB. Method tersebut akan menerima dokumen yang memiliki daftar *field* dan urutan penyortiran.Untuk menunjukkan urutan penyortiran perlu ditetapkan nilai 1 atau -1 dengan entitas tertentu berdasarkan urutan yang akan diatur dan ditampilkan. Angka 1 menunjukkan pengorganisasian data dalam urutan menaik (*ascending*) sementara -1 menunjukkan pengorganisasian dalam urutan menurun (*descending*).

- Secara default, jika tidak dituliskan / dinyatakan secara eksplisit preferensi pengurutan (1 atau -1), maka method sort() akan menampilkan dokumen dalam urutan menaik (*ascending*).

- Berikut contoh sintaks *ascending sorting*:
`db.techSubjects.find({}, {"topic":1, _id:0}).sort({"topic":1})`

- Berikut contoh sintaks *descending sorting*:
`db.techSubjects.find({}, {"topic":1, _id:0}).sort({"topic":-1})`

--------------------------------------------------------------------------------------------------------------------------------------------

**Source:** 
[https://www.w3schools.in/mongodb/]
[https://www.w3schools.com/mongodb/]
