### NAMA : WIRASWANTI RISMANDA PUTRI
### NIM : 2141762021
### KELAS : SIB-2E

#### Tugas Pertemuan 13

# QUERY, UPDATE, DELETE & SORTING DATA MongoDB

**A. QUERY**
Query merupakan sebuah elemen penting dalam sistem basisdata. Seperti halnya pada MySQL pada MongoDB juga tedapat query yang akan digunakan untuk Update, Delete maupun Sorting Data.
Method untuk Melakukan Query di MongoDB :
**1.The find() method**:Metode ini digunakan untuk menanyakan data dari koleksi MongoDB
Syntax : `.collection_name.find()`
Contoh : `b.writers.find()`

**2.The pretty() method** : Metode ini digunakan untuk memberikan format yang tepat pada keluaran yang diekstrak oleh query
Syntax : `b.collection_name.find().pretty()`
Contoh : `b.writers.find().pretty()`

Memfilter Kriteria dalam Query MongoDB : memungkinkan untuk memfilter hasil yang dicari dengan memberikan atau menambahkan beberapa kriteria spesifik dan dapat menambahkan atribut khusus ke method find() untuk mengambil data dari database tertentu.
Contoh : `b.writers.find( { author: “Elon Musk” } )`

Memungkinkan Permintaan dalam Kondisi “AND” : memungkinkan Anda menentukan nilai data dari dokumen yang menyimpan dua atau lebih nilai yang ditentukan untuk diambil dari query.
Contoh : `b.writers.find( { tools: “Netbeans”, born: 1934 } )`

Memungkinkan Permintaan dalam Kondisi “OR” : memungkinkan pengguna untuk menentukan salah satu atau beberapa nilai menjadi benar.
Contoh : `b.musicians.find( {$or: [ { instrument: “Piano” }, { born: 1940 } ] } )`

$in operator : operator khusus lain yang digunakan dalam kueri untuk menyediakan daftar nilai dalam query. Saat dokumen menyimpan salah satu dari nilai yang diberikan tersebut, dokumen tersebut akan dikembalikan.
Contoh : `b.musicians.find( { “instrument”: { $in: [ “Keyboard”, “Gitar” ] } } )`


**B.UPDATE DATA**
Operasi update dalam database digunakan untuk mengubah atau memperbarui nilai dalam dokumen. MongoDB memanfaatkan metode update() untuk memperbarui dokumen dalam collection MongoDB. Untuk memperbarui dokumen tertentu, kriteria baru dapat digabungkan dengan pernyataan pembaruan, yang hanya akan memperbarui dokumen yang dipilih.
Berikut adalah representasi bertahap tentang bagaimana hal ini dapat dilakukan:
•Menggunakan metode update().
•Lebih suka keadaan yang ingin diterapkan untuk memutuskan dokumen mana yang perlu diperbarui dalam database mereka. Contoh di mana ingin memperbarui dokumen yang memiliki id 4.
•Kemudian menggunakan perintah set untuk memodifikasi nama Field.
•Pilih nama Field mana yang ingin Anda ubah dan masuk ke nilai baru secara konsekuen.
Syntax : 
`b.collection.update(
    <query>,
   <update>,
   {
     upsert: <boolean>,
     multi: <boolean>,
     writeConcern: <document>,
     collation: <document>,
     arrayFilters: [ <filterdocument1>, ... ]
   }
)`

Karakteristik Update di MongoDB :
•Jika field tidak ada dalam dokumen saat ini, operator $set akan memasukkan field baru dengan nilai yang ditentukan, sampai dan kecuali itu melanggar batasan tipe.
•Pengguna MongoDB juga dapat menggunakan { multi: true } untuk memperbarui banyak dokumen yang akan memenuhi kriteria query.
•Memanfaatkan { upser: true } untuk membuat dokumen baru juga dimungkinkan karena tidak ada dokumen yang disertakan dengan query.


**C.DELETE DATA**
MongoDB memungkinkan Anda untuk menghapus dokumen atau dokumen secara kolektif menggunakan salah satu dari tiga metodenya. Tiga metode yang disediakan oleh MongoDB untuk menghapus dokumen adalah:
**1.db.collection.deleteOne()**
Metode ini digunakan untuk menghapus satu dokumen saja, meskipun ada lebih dari satu dokumen yang sesuai dengan kriteria.
Contoh : `b.programmers.deleteOne( { name: { $in: [ "Dennis Ritchie", "Bjarne Stroustrup"] } } )`
**2.db.collection.remove()**
Metode ini menghapus semua dokumen yang ada dalam koleksi hanya dengan mengecualikan kriteria filter yang disebutkan dalam tanda kurung () dan menentukan nama dokumen di dalamnya.
Contoh : `b.programmers.remove( {} )`
`b.programmers.remove( { name: "James Gosling" } )`
**3.db.collection.deleteMany()**
Metode ini menghapus semua dokumen Anda yang sesuai dengan kriteria yang disebutkan dalam parameter
Contoh : `b.programmers.deleteMany( { name: { $in: [ "Dennis Ritchie", "Bjarne Stroustrup" ] } } )`

**D.SORTING DATA**
Metode ini akan menerima dokumen yang memiliki daftar bidang dan urutan penyortiran. Untuk menunjukkan urutan penyortiran, Anda harus menetapkan nilai 1 atau -1 dengan entitas tertentu berdasarkan urutan yang akan diatur dan ditampilkan. Satu menunjukkan pengorganisasian data dalam urutan menaik sementara -1 menunjukkan pengorganisasian dalam urutan menurun.
Syntax :
`b.collection_name.find().sort({FieldName1: sort order 1 atau -1, FieldName2: sort order})`

Contoh untuk menampilkan data secara menurun
`b.techSubject.find({}, {“topic”:1, _id:0}).sort({“topic”:-1})
{ “topic” : “Digital Privacy” }
{ “topic” : “Cyber Security” }
{ “topic” : “Application Security Engineering” }`

Contoh untuk menampilkan data secara menaik
`b.techSubject.find({}, {“topic”:-1, _id:0}).sort({“topic”:-1})
{ “topic” : “Digital Privacy” }
{ “topic” : “Cyber Security” }
{ “topic” : “Application Security Engineering” }`