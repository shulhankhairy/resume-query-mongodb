**Dokumen ini disusun oleh:**
Nanda Shabrina Putri Kurnia / 2141762064 / SIB-2E / 14


# Update, Delete, dan Sorting pada MongoDB

## 1. Update Document pada MongoDB
   
   ### 1.1. Update Pada *Fields* yang Spesifik
   Untuk melakukan *update* pada sebuah *field* yang spesifik, digunakan sebuah operator `$set`.
   
   ### 1.2. Update *Single Document*
   Untuk melakukan *update* pada sebuah dokumen atau data tunggal pada MongoDB, digunakan *method* `db.collection.updateOne()`. 
   
   ```json
   db.collection.updateOne( {nama: "Nanda Shabrina"}, 
   { 
       $set: {
       nama: "Na Jaemin" 
       }
    })
   ```
   
   Keterangan:
   1. Parameter pertama digunakan untuk mendefinisikan baris yang akan diubah nilainya.
   2. Parameter kedua digunakan untuk mendefinisikan nilai baru dari baris yang diubah nilainya.
   3. Jika pada query ditemukan lebih dari satu record, maka hanya record pertama yang akan dilakukan *update*
   
   
   ### 1.3. Update *Multiple Documents*
   Untuk melakukan *update* pada beberapa dokumen atau data sekaligus, dapat menggunakan *method* `db.collection.updateMany()`. Method ini dapat pula diimplementasikan dengan menambahkan kondisi seperti *decision making - 'if else'* untuk melakukan *filtering* record yang akan diubah. 
   
   ```json
   db.collection.updateMany(
       {security_deposit: {$lt: 100} },
       {
           $set: {security_deposit: 100, minimum_nights: 1 }
       }
   )
   ```

   ### 1.4. Mengganti Sebuah Dokumen
   Untuk mengganti keseluruhan konten dalam sebuah dokumen (tidak termasuk id dari field) dapat dilakukan dengan menggantinya menjadi sebuah dokumen baru menggunakan sintaks `db.collection.replaceOne()`. 
   
   Perlu diperhatikan dalam menggunakan sintaks ini, nilai dokumen **tidak boleh berupa hasil operasi**. 
   
   ```json
   db.accounts.replaceOne(
  { account_id: 371138 },
  { account_id: 893421, limit: 5000, products: [ "Investment", "Brokerage" ] }
)
   ```
   

## 2. Delete Document pada MongoDB

   ### 2.1. Menghapus Seluruh Dokumen
   Untuk menghapus keseluruhan dokumen dari sebuah collection, digunakan *method* `db.collection.deleteMany({})'`. Dengan `{}` merupakan sebuah filter untuk mengosongkan dokumen.
   
   ```json
   db.mycollection.deleteMany({})
   ```
   
   ### 2.2. Menghapus Beberapa Dokumen
   Menghapus dokumen dapat pula dilakukan dengan menspesifikkan kriteria atau melakukan *filter* pada *record* dokumen yang ingin dihapus. Sintaks yang digunakan adalah `db.collection.deleteMany()`. 
   
   ```json
   var MongoClient = require('mongodb').MongoClient;
   var url = "mongodb://localhost:27017/";

    MongoClient.connect(url, function(err, db) {
      if (err) throw err;
      var dbo = db.db("mydb");
      var myquery = { address: /^O/ };
      dbo.collection("customers").deleteMany(myquery, function(err, obj) {
          if (err) throw err;
          console.log(obj.result.n + " document(s) deleted");
          db.close();
          });
      });
   ```
   
   ### 2.3. Menghapus Sebuah Dokumen
   Apabila ingin menghapus sebuah dokumen, dapat digunakan *method* `db.collection.deleteOne()`.
   
   ```json
   db.movies.deleteOne( { cast: "Brad Pitt" } )
   ```
   

## 3. Sorting Document pada MongoDB
Adapula batasan dalam melakukan sorting yakni maksimum 32 keys. 

   ### 3.1. Operator 
   Operator `$sort` digunakan untuk melakukan sorting pada sebuah dokumen dengan memasukkan nilai kemudian mengembalikannya dalam sebuah urutan yang tersortir.
   
      
   ### 3.2. Ascending / Descending Sort
   Sedangkan untuk melakukan sorting urut *ascending* atau *descending* dapat menggunakan spesifikasi nilai untuk mengurutkan yakni `1` atau `-1`. Berikut contoh penggunaan sorting secara alfabetis.
   
   ```json
      db.users.aggregate(
       [
         { $sort : { age : -1, posts: 1 } }
       ]
      )
   ```
