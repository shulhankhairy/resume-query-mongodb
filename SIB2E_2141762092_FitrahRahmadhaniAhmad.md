### Nama    : Fitrah Rahmadhani Ahmad  
### NIM     : 2141762092
### Kelas   : SIB-2E  
---
# Update Data MongoDB  
Perubahan data sering kali dapat dilakukan atau terjadi karena suatu alasan tertentu. Update data pada Mongo DB juga bisa terjadi karena adanya perubahan perancangan pada sistem yang mengharuskan satu atau beberapa data harus diubah. Terdapat dua query update pada Mongo DB, yaitu.  
**1. Query updateOne()**  
    Query updateOne() akan memperbarui data pertama yang ditemukan cocok dengan query yang telah disusun.Contoh terdapat data seperti di bawah ini dan akan dilakukan update pada field likes.    

    [{  
        _id: ObjectId("62c350dc07d768a33fdfe9b0"),  
        title: 'Post Title 1',  
        body: 'Body of post.',  
        category: 'News',  
        likes: 1,  
        tags: [ 'news', 'events' ],  
        date: 'Mon Jul 04 2022 15:43:08 GMT-0500(Central Daylight Time)'  
    }]

Query seperti pada uraian berikut.

    Query updateOne:  
    'db.posts.updateOne( { title: "Post Title 1" }, { $set: { likes: 2 } } )'  

*Keterangan: title digunakan sebagai indeks pencarian dan $set digunakan untuk memasukkan perubahan data*  


Maka data tersebut akan berubah menjadi:  

    [{  
        _id: ObjectId("62c350dc07d768a33fdfe9b0"),  
        title: 'Post Title 1',  
        body: 'Body of post.',  
        category: 'News',  
        likes: 2,  
        tags: [ 'news', 'events' ],  
        date: 'Mon Jul 04 2022 15:43:08 GMT-0500(Central Daylight Time)'  
    }]  


**2. Query updateMany()**  
Berbeda dengan updateOne(), updateMany() digunakan untuk memperbarui semua data yang cocok dengan query yang telah disusun.  

    Query updateMany:  
    'db.posts.updateMany({}, { $inc: { likes: 1 } })'  

Maka semua data pada fiels likes akan bernilai 1.  

---

# Delete Data MongoDB  
Delete Statement digunakan untuk menghapus data berdasarkan query yang sesuai dengan keinginan pengguna. Terdapat dua query update pada Mongo DB, yaitu.  
**1. Query deleteOne()**  
Query deleteOne() akan menghapus data pertama yang ditemukan cocok dengan query yang telah disusun. Misalkan menghapus data pada field title dengan value Post Title 5.  

    Query deleteOne:  
    'db.posts.deleteOne({ title: "Post Title 5" })'  

maka, data yang berada pada field title dengan value Post Title 5 akan terhapus.  


**2. Query deleteMany()**  
Query deleteMany() akan menghapus semua data yang ditemukan cocok dengan query yang telah disusun. Sebagai contoh ketika ingin menghapus semua data yang memiliki kategori Technology.  

    Query deleteMany():
    'db.posts.deleteMany({ category: "Technology" })'  

maka, data pada field category dengan value Technology akan dihapus.  

--- 
# Sorting Data MongoDB (Aggregation)  
Terkadang pada saat menampilkan data dengan kondisi-kondisi tertentu, kita membutuhkan pengurutan data secara ascending maupun descending.  
*Ascending mengggunakan 1 sedangkan descending menggunakan -1*

    Query basic sorting data:  
    'db.COLLECTION_NAME.find().sort({KEY:1})'

Sebagai contoh terdapat data seperti berikut.  

    {_id : ObjectId("507f191e810c19729de860e1"), title: "MongoDB Overview"}
    {_id : ObjectId("507f191e810c19729de860e2"), title: "NoSQL Overview"}
    {_id : ObjectId("507f191e810c19729de860e3"), title: "Tutorials Point Overview"}

Dilakukan pengurutan data secara descending, maka query yang disusun adalah sebagai berikut.

    Query sort():
    db.description.find().sort({KEY:-1})

maka, hasil dari query di atas sebagai berikut.

    db.mycol.find({},{"title":1,_id:0}).sort({"title":-1})
    {"title":"Tutorials Point Overview"}
    {"title":"NoSQL Overview"}
    {"title":"MongoDB Overview"}



