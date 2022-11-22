# Resume Materi Tentang Query, Update Data, Delete Data, Sorting Data pada mongoDB #



**Nama      : Rizqi Hendra Ardiansyah**


**Kelas     : SIB2E**


**No.Absen  : 19**


**NIM       : 2141762145**



**A.	Query**


Pada MongoDb ada beberapa cara query yang digunakan untuk mengolah data. Untuk tabel sendiri pada mongoDb biasanya disebut collection dan query yang digunakan untuk mencari data tertentu dan biasanya di sebut criteria


**B.	Update Data**


Pada mongoDb perintah update data merupakan salah satu perintah atau bisa disebut query yang digunakan untuk mengubah data sesuai dengan kondisi yang dinginkan. Untuk query nya sendiri akan dicantumkan pada macam -macam perintah query di bawah ini


**C.	Delete Data**


Pada mongoDb, perintah untuk melakukan delete data merupakan salah perintah yang bisa kita sebut dengan query biasanya digunakan untuk menghapus record yang ada pada sebuah data kolom atau field. Untuk query nya sendiri akan dicantumkan jadi satu pada macam – macam perintah query dibawah ini


**D.	Sorting Data**


Pada mongoDb, sorting data atau bisa kita sebut pengurutan data merupakan salah satu perintah atau query yang tentunya untuk melakukan sortir atau pencarian record yang ada pada kolom atau field. Untuk query nya sendiri akan dicantumkan jadi satu pada macam – macam perintah query dibawah ini

**Berikut macam – macam perintah dari Query Data, Update Data, Delete Data dan Sorting Data**

**1.	List database**

```
db
```

**2.	Membuat atau menggunakan database**

```
use databaseSatu;
```

databaseSatu akan dibuat jika belum ada

**3.	Menampilkan database beserta ukurannya**

```
show dbs;
```

**4.	Menampilkan collections pada database**

```
show collections;
```

**5.	Melakukan insert dan membuat collection**

```
db.users.insertOne( { nama:"azka",umur: 8,status:"pria" } );
```

otomatis membuat collection users jika belum ada

**6.	Melakukan sorting dari users collection**

```
db.users.find();
```

**7.    Menampilkan isi sorting dari users dengan format json yg pretty**

```
db.users.find().pretty();
```

**8.    Melakukan Sorting menggunakan limit**

```
db.users.find().limit(10).pretty();
```

**9.	Melakukan Sorting menggunakan limit dan offset**

```
db.users.find().skip(1).limit(10).pretty();
```

**10.	Insert dokumen banyak sekaligus**

```
db.users.insertMany( [

{ nama:"azkia",umur: 4,status:"wanita" },

{ nama:"adi",umur: 38,status:"pria" },

{ nama:"ina",umur: 34,status:"wanita" }

]);
```

**11.	Update satu dokumen**

```
db.users.updateOne(

    {"nama":"adi"},

    {$set: {"umur": 37} }

);
```

**12.	Update banyak dokumen sekaligus**

```
db.users.updateMany(

  {"umur":30, "nama":"adi"},

  { $set: { "Dewasa" : true } }

);

db.users.updateMany(

  { umur: { $gt: 30 } },

  { $set: { "Dewasa" : true } }

);

db.users.updateMany(

  { umur: { $lt: 30 } },

  { $set: { "Dewasa" : false, "lastUpdate": ISODate("2020-03-24T17:31:01.670Z") } }

);

db.users.updateMany(

  { umur: { $gt: 30 } },

  { $set: { "Dewasa" : true, "lastUpdate": new Date() } }

);

db.users.updateMany(

  { umur: { $gt: 30 } },

  { $set: { "Dewasa" : true, "lastUpdate": new Date("2020-04-04") } }

);
```

**13.	Melakukan insert banyak dokumen**

```
db.users.insertMany( [

{ nama:"budi",umur: 4,status:"wanita" },

{ nama:"rudi",umur: 38,status:"pria" },

{ nama:"ardi",umur: 34,status:"wanita" }

]);
```

**14.	Menghitung baris**

```
db.users.count();
```

**15.	Melakukan Delete dokumen**

```
db.users.deleteOne(

    {"nama":"ardi"}

);

//delete banyak dokumen dengan OR

db.users.deleteMany(

    {$or: [{"nama":"budi"},{"nama":"rudi"}]}

);
```


**16.	Empty collection, semua dokumen dalam colection users dihapus**

```
db.users.remove( { } );
```

**17.	Menghapus collections**

```
db.users.drop();
```
