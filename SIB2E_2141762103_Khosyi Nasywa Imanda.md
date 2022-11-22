=-=-==-=-=-=-=-=-=-=-=-===-=--=-=-=-=-=-=-=-=-=-=-=-=-=--=-=-=-=-==-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-==-=-=-=

                        “UPDATE DATA, DELETE DATA, SERTA SORTING DATA PADA MONGODB”
                                 Mata Kuliah : Teori Basis Data Lanjutan

 
                                           Disusun oleh :
                                      Khosyi Nasywa Imanda
                                            2141762103
                                              SIB-2E

                                PROGRAM STUDI D-IV SISTEM INFORMASI BISNIS 
                                       JURUSAN TEKNOLOGI INFORMASI
                                        POLITEKNIK NEGERI MALANG

                 Jl. Soekarno Hatta No.9,Jatimulyo, Kec, Lowokwaru, Kota Malang, JawaTimur
                                                 65141
=-=-==-=-=-=-=-=-=-=-=-===-=--=-=-=-=-=-=-=-=-=-=-=-=-=--=-=-=-=-==-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-==-=-=-=
                                    
pada umumnya MongoDB memiliki 4 fungsi utama yaitu select ,  insert ,  update dan delete. seperti kita ketahui bersama bahwa select digunakan untuk menampilkan data, insert digunakan untuk menyimpan data, update digunakan untuk mengubah data, dan delete digunakan untuk menghapus data.
Selain memiliki 4 fungsi utama , MongoDb juga memiliki fungsi untuk melakukan persortiran data baik itu secara ascending maupun descending . Pada kali ini saya hanya menjelaskan bebrapa fungsi yang terdapat pada mongoDb yaitu Update Data , Delete Data dan Sorting Data pada MongoDb

# **1. Update Data**

a.	Fungsi Update Data
Seperti kita ketahui bersama bahwa fungsi “update” digunakan untuk  mengubah data atau memperbarui suatu data pada database yang kita miliki . fungsi tersebut dapat kita gunakan ketika kita ingin melakukan suatu perubahan atau pembaruan suatu data pada database yang kita miliki .

b.	Sintaks Update Data
Metode update () digunakan untuk memperbarui atau mengubah suatu data yang telah ada. Sintaks dalam “update-data” adalah sebagai berikut:
```
  db.collection.update(
     <query>,
     <update>,
     {
       upsert: <boolean>,
       multi: <boolean>,
       writeConcern: <document>
     }
  ) 
```

c.	Parameter Deskripsi
    - query: kriteria permintaan pembaruan, mirip dengan update sql query di mana bagian belakang batin.
    - update: pembaruan objek dan beberapa operator baru (seperti $, $ inc ...), dll, juga dapat dipahami sebagai diatur kembali dalam update sql query
    - upsert: opsional, yang berarti argumen ini adalah bahwa jika tidak ada update catatan, dimasukkan objNew, benar untuk menyisipkan, default adalah palsu, tidak dimasukkan.
    - multi-: Opsional, mongodb default adalah palsu, hanya untuk menemukan rekaman pertama untuk memperbarui, jika argumen ini benar, sesuai dengan kondisi mengeluarkan banyak catatan periksa semua pembaruan.
    - writeConcern: tingkat opsional eksepsi dilemparkan.

d.	Contoh “Update-data”
    Misal disini kita memasukkan bebrapa kumpulan data , seperti query dibawah ini :
```
  >db.col.insert({
      title: 'Update Data MongoDb', 
      description: ' Metode update () digunakan untuk memperbarui atau mengubah suatu data yang telah ada ',
      by: 'Khosyi Nasywa ',
      url: 'http://www.resumeMongoDb.com',
      tags: ['mongodb', 'database', 'NoSQL'],
      likes: 1000
  })
```
    Lalu dari data tersebut , kita ingin melakukan perubahan data pada suatu bagian tertentu . Misal disini saya ingin melakukan perubahan data pada judul yang telah ada sebelumnya , makan sintaks dari update tersebut yaitu :

```
   >db.col.update({'title':''Update Data MongoDb'},{$set:{'title':'MongoDB update'}})
   WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })   
   > db.col.find().pretty()
   {
           "_id" : ObjectId("56064f89ade2f21f36b03136"),
           "title" : "MongoDB update",
           "description" : " Metode update () digunakan untuk memperbarui atau mengubah suatu data yang telah ada ",
           "by" : "'Khosyi Nasywa ",
          "url" : 'http://www.resumeMongoDb.com'
          "tags" : [
                  "mongodb",
                  "database",
                  "NoSQL"
           ],
           "likes" : 100
}
>
```

# **2. Delete Data**

a.	Fungsi Delete Data
Seperti kita ketahui bahwa fungsi “delete” digunakan untuk  menghapus data pada database yang kita miliki . fungsi tersebut dapat kita gunakan ketika kita ingin melakukan penghapusan suatu data pada database yang kita miliki .

b.	Sintaks Delete Data
Metode delete () digunakan untuk menghapus suatu data yang telah ada. Sintaks dalam “delete-data” adalah sebagai berikut:
```
 db.collection.remove(
   <query>,
   {
     justOne: <boolean>,
     writeConcern: <document>
   }
)
```

c.	Parameter Deskripsi
    - permintaan :( opsional) kondisi dokumen dihapus.
    - JustOne: (Opsional) Jika diatur ke benar atau 1, hanya untuk menghapus dokumen.
    - writeConcern :( opsional) tingkat pengecualian dilemparkan.

d.	Contoh “Delete-data”
Semisial disini saya akan menghapus judul pada data yang telah saya buat sebelumnya , maka sintaks dari delete tersebut yaitu :
```
>db.col.remove({'title':'MongoDB update'})
WriteResult({ "nRemoved" : 2 })           
>db.col.find()
……  
```      

Jika kita  ingin menghapus semua data, maka dapat menggunakan metode berikut :
```
>db.col.remove({})
>db.col.find()
>
```

# **3. Sorting Data**

a.	Fungsi Sorting Data
Seperti kita ketahui bahwa fungsi “sorting” digunakan untuk mengurutkan data dalam urutan secara naik atau menurun dalam suatu dokumen pada database . fungsi tersebut dapat kita gunakan ketika kita ingin mengurutkan suatu data pada database yang kita miliki .
Pada pengurutan data ini , kita dapat mengurutkan secara Ascending maupun Descending . pada pengurutan Ascending , kita mengurutkan data mulai dari data yang terkecil hingga terbesar , Sedangkan pengurutan Descending kita mengurutkan data mulai dari data yang terbesar hingga terkecil.

b.	Sintaks Sorting Data
Metode sort() digunakan untuk pengurutan suatu data pada dokumen dalam suatu database , baik itu secara ascending maupun descending . Sintaks dalam “sort-data” adalah sebagai berikut:
sort (“name”, 1) #ascending
sort (“name”, -1) #descending

c.	Contoh “Sorting-data”
Semisial disini saya mengrutkan hasil secara terbalik (menurun) menurut abjad berdasarkan nama , maka sintaksnya yaitu :
```
import pymongo

myclient = pymongo.MongoClient("mongodb://localhost:27017/")
mydb = myclient["mydatabase"]
mycol = mydb["customers"]

mydoc = mycol.find().sort("name", -1)

for x in mydoc:
  print(x)
```

 







