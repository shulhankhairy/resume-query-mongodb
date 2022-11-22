## Nama  : Sabila Nadia Islamia
## NIM   : 2141762046
## Kelas : SIB2E

# **UPDATE, DELETE AND SORTING DATA IN MONGODB**



 ### UPDATE DATA
 Untuk memperbarui (update) data, MongoDB menyediakan ==update operators== berupa **$set** , untuk memodifikasi value atau nilai data. Bentuk umumnya adalah sebagai berikut:

{
  <update operator>: { <field1>: <value1>, ... },
  <update operator>: { <field2>: <value2>, ... },
  ...
}

 * **$**   : merupakan placeholder untuk memperbarui elemen pertama yang match atau sesaui dengan query condition.
 * **set** : merupakan variabel yang menampung nilai yang akan digunakan untuk memperbarui field di dalam dokumen. 

 **Perlu diketahui:**
 Beberapa operator update akan menciptakan/membuat field baru yang sebelumnya belum ada. 

 Query yang digunakan adalah mengikuti ketentuan ==mongosgh== pada MongoDB documentary. Pada dasarnya terdapat 3 cara memperbarui (update) dokumen atau data di dalam MongoDB, yakni:
1. 'db.collection.updateOne(<filter>, <update>, <options>)'
2. 'db.collection.updateMany(<filter>, <update>, <options>)'
3. 'db.collection.replaceOne(<filter>, <update>, <options>)'

**Contoh:**

db.inventory.insertMany( [
   { item: "canvas", qty: 100, size: { h: 28, w: 35.5, uom: "cm" }, status: "A" },
   { item: "journal", qty: 25, size: { h: 14, w: 21, uom: "cm" }, status: "A" },
   { item: "mat", qty: 85, size: { h: 27.9, w: 35.5, uom: "cm" }, status: "A" },
   { item: "mousepad", qty: 25, size: { h: 19, w: 22.85, uom: "cm" }, status: "P" },
   { item: "notebook", qty: 50, size: { h: 8.5, w: 11, uom: "in" }, status: "P" },
   { item: "paper", qty: 100, size: { h: 8.5, w: 11, uom: "in" }, status: "D" },
   { item: "planner", qty: 75, size: { h: 22.85, w: 30, uom: "cm" }, status: "D" },
   { item: "postcard", qty: 45, size: { h: 10, w: 15.25, uom: "cm" }, status: "A" },
   { item: "sketchbook", qty: 80, size: { h: 14, w: 21, uom: "cm" }, status: "A" },
   { item: "sketch pad", qty: 95, size: { h: 22.85, w: 30.5, uom: "cm" }, status: "A" }
] );

**Update a Single Document**
Dalam contoh dan kasus tersebut, saya akan memperbarui data dengan field item : "paper", dengan mengganti dokumen di dalamnya sebagai berikut:

db.inventory.updateOne(
   { item: "paper" },
   {
     $set: { "size.uom": "cm", status: "P" },
     $currentDate: { lastModified: true }
   }
)

Keterangan:
* Operator $set akan memperbarui nilai size.oum di dalam field menjadi "cm" dan nilai di dalam status di dalam field menjadi "p"
* Operator $currentDate akan memperbarui nilai di dalam field lastModified menjadi current date. Jika field lastModified tidak ada, maka operator $currentDate akan membuat field baru. 

**Update a Multiple Document**
Dalam contoh kasus, saya akan belajar memperbarui beberapa data/dokumen sekaligus. Menggunakan updateMany(), sebagai berikut:

db.inventory.updateMany(
   { "qty": { $lt: 50 } },
   {
     $set: { "size.uom": "in", status: "P" },
     $currentDate: { lastModified: true }
   }
)

Keterangan:
* Operator $set akan memperbarui data di dalam item = "qty" dimana terdapat operator $lt yang menjadi parameter/tolak ukur perubahan data. Maksud dari operator $lt adalah **MongDB tolong pilihkan saya data atau dokumen dimana value/nilai di dalam field adalah kurang dari (lt = less than) nilai yang telah dideskripsikan**. Sehingga, nantinya semua item yang bernilai "qty" yang berjumlah kurang dari 50 akan di update/diperbarui.

**Replace a Document**
Replace akan me paling tidak single document yang sesuai (matches) dengan spesifik filter meskipun dokumen lain juga sesuai (matches).

Contoh:
db.inventory.replaceOne(
   { item: "paper" },
   { item: "paper", instock: [ { warehouse: "A", qty: 60 }, { warehouse: "B", qty: 40 } ] }
)

Macam-macam metode:
* db.collection.findOneAndReplace()
* db.collection.findOneAndUpdate()
* db.collection.findAndModify()
* db.collection.bulkWrite()










 ### DELETE DATA
Terdapat beberapa cara yang dapat digunakan untuk menghapus data/dokumen di dalam MongoDB, pada prinsip ==mongosh== yakni:
 * db.collection.deleteOn()
 * db.collection.deleteMany()

 Contoh studi kasus
 db.inventory.insertMany( [
   { item: "journal", qty: 25, size: { h: 14, w: 21, uom: "cm" }, status: "A" },
   { item: "notebook", qty: 50, size: { h: 8.5, w: 11, uom: "in" }, status: "P" },
   { item: "paper", qty: 100, size: { h: 8.5, w: 11, uom: "in" }, status: "D" },
   { item: "planner", qty: 75, size: { h: 22.85, w: 30, uom: "cm" }, status: "D" },
   { item: "postcard", qty: 45, size: { h: 10, w: 15.25, uom: "cm" }, status: "A" },
] );

**Delete All Documents**
Untuk menghapus semua dokumen di dalam collection, dapat menggunakan metode db.collection.deleteMany() dan kurung awal-akhir untuk menghimpun data. 

db.inventory.deleteMany({})

Keterangan:
* Semua value atau data di dalam collection inventory akan terhapus. 

**Delete All Documents that Match a Condition**
Sesuai dengan studi kasus, query yang digunakan adalah sebagai berikut:

db.inventory.deleteMany({ status : "A" })

Keterangan:
* Semua data di dalam field status bernilai "A" akan terhapus. 

**Delete Only One Document that Matches a Condition**
Untuk menghapus paling tidak single document yang sesuai dengan kondisi (meskipun banyak dokumen yang bisa saja sesuai), query yang digunakan adalah sebagai berikut:

db.inventory.deleteOne( { status: "D" } )

Keterangan:
* Data pertama dimana status bernilai "D" akan terhapus.











 ### SORTING DATA
Sorting adalah salah satu operasi database yang sangat penting. Operasi tersebut membantu pembacaan data menjadi lebih mudah dikarenakan fungsinya sendiri yakni mengurutkan data sesuai dengan kebutuhan yang diperlukan (ASC : kecil ke besar | DESC : besar ke kecil). 

Di dalam MongoDB operasi sort didefinisikan dengan query sort(). Untuk mengindikasi urutan sorting, terdapat dua aturan yakni:
* 1     =   Sort ascending, pengurutan data akan dilakukan dari data bernilai kecil ke besar
* -1    =   Sort descending, pengurutan data akan dilakukan dari data bernilai besar ke kecil

Maksimum data yang dapat diurutkan sekaligus adalah dengan 32 keys, dan jika pengurutan dilakukan untuk multiples data, maka dokumen akan dieksekusi dari kiri ke kanan, sesuai dengan cara komputer mengeksekusi code program. 

Query:
{ $sort: { <field1>: <sort order>, <field2>: <sort order> ... } }

Contoh studi kasus:

db.cafe.insertMany( [
   { "_id" : 1, "name" : "Central Cafe", "city" : "Malang"},
   { "_id" : 2, "name" : "Titik Koma Cafe", "city" : "Malang"},
   { "_id" : 3, "name" : "Senja Cafe", "city" : "Kediri"},
   { "_id" : 4, "name" : "Pizzaria and Cafe", "city" : "Kediri"},
   { "_id" : 5, "name" : "Nadia Smiley Cafe", "city" : "Malang"},
] );

**Ascending Sorting**

db.cafe.aggregate(
   [
     { $sort : { name : 1 } }
   ]
)

Keterangan:
* Data akan ditampilkan dengan mengacu pada field name, terurut dari data bernilai (alfabet) kecil ke besar. 

**Descending Sorting**

db.cafe.aggregate(
   [
     { $sort : { city : -1 } }
   ]
)

Keterangan:
* Data akan ditampilkan dengan mengacu pada field city, terurut dari data bernilai (alfabet) besar ke kecil. 


Terima Kasih Bapak..