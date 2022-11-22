```
Nama    : Jati Wahyu Kusuma
Kelas   : SIB2E
Absen   : 10
Nim     : 2141762139
```

```                                                    
                                                              LAPORAN TEORI
                                                            BASIS DATA LANJUT
                                                                MERESUME
                                                           
```

**I.	QUERY MONGODB**

Arti query pada bahasa pemrograman komputer adalah informasi yang diterima ataupun diambil dari suatu database. Hal tersebut berguna untuk memanipulasi, menambah, menghapus serta mengubah data. MongoDB ada cara query tersendiri untuk mengolah data. Tabel di MongoDB biasa disebut collection dan query untuk mencari data tertentu disebut sebagai criteria.contoh query yaitu seperti mengubah data atau update,menghapus data atau remove dan lain lain.

**II.	UPDATE DATA**

Perintah update data merupakan salah satu perintah yang digunakan untuk mengubah data sesuai dengan kondisi yang diinginkan.didalam mongodb perintah update menggunakan rumus db.collection_name.update().contohnya sbagai berikut :

```
db.collection_name.update({nilai document lama}, {$set:{nilai document baru}})
```

Contohnya :
```
db.mahasiswa.update({"alamat":"padang"},{$set:{"alamat":"surabaya"}})
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
```




**III.	DELETE DATA**

Jadi didalam mongodb perintang menghapus data/delete data yaitu perintah remove().yang berfungsi untuk menghapus data yang digunakan saat ini. penghapusan data juga memiliki <query> untuk menentukan data yang akan dihapus.update data yang MongoDB bisa menggunakan update () fungsi. Pertunjukan hapus () Fungsi pertama sebelum eksekusi find () perintah untuk menentukan apakah kondisi untuk melakukan dengan benar, ini adalah kebiasaan yang baik.
 sintaks menghapus data:
```
db.collection.remove(
   <query>,
   <justOne>
)

```

Jika MongoDB versi 2.6 kemudian, sintaks adalah sebagai berikut:
```
db.collection.remove(
   <query>,
   {
     justOne: <boolean>,
     writeConcern: <document>
   }
)
```

Contoh :
```
>db.col.remove({'title':'MongoDB 教程'})
WriteResult({ "nRemoved" : 2 })           # 删除了两条数据
>db.col.find()
……                                        # 没有数据

})
```



**IV.	SORTING  DATA**

Dalam sistem manajemen basis data, fenomena penyortiran atau sorting data digunakan untuk mengambil dokumen secara berurutan atau pengurutan. Dukungan pengurutan berdasarkan tanggal dari MongoDB membantu untuk mendapatkan dokumen yang disusun menurut bidang tanggal.
Sebagai, penyortiran dapat dilakukan baik secara menaik atau menurun; sama halnya, pengurutan berdasarkan tanggal juga memungkinkan pengambilan dokumen di kedua pesanan.

**1.	Mengurutkan Hasil**

    Gunakan metode sort() untuk mengurutkan hasil dalam urutan secara naik atau menurun.
    Metode sort() mengambil satu parameter untuk “fieldname” dan satu parameter untuk “direction” naik atau turun (naik adalah arah default).
```
    import pymongo
    myclient = pymongo.MongoClient("mongodb://localhost:27017/")
    mydb = myclient["mydatabase"]
    mycol = mydb["customers"]
    mydoc = mycol.find().sort("name")
    for x in mydoc:
    print(x)
```


**2.	Urutkan secara Menurun dan naik (ascending) dan (Descending)**

    Gunakan nilai -1 sebagai parameter kedua untuk mengurutkan dokumen secara menurun dan naik.

    sintaks :
    ```
    sort (“name”, 1) #ascending
    sort (“name”, -1) #descending

    ```

    Contoh:

    ```
    import pymongo
    myclient = pymongo.MongoClient("mongodb://localhost:27017/")
    mydb = myclient["mydatabase"]
    mycol = mydb["customers"]
    mydoc = mycol.find().sort("name", -1)
    for x in mydoc:
    print(x)

    ```




