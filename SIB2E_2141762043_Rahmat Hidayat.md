
# __RESUME__
## __QUERY__
Query pada pemrograman adalah perintah untuk memanggil sebuah informasi pada sebuah database. Penulisan query memerlukan serangkaian kode agar database bisa memahami intruksi yang diberikan.
Berbeda dengan SQL, MongoDB ada cara query tersendiri untuk mengolah data. Tabel di MongoDB biasa disebut collection dan query untuk mencari data tertentu disebut sebagai criteria.
Untuk instalasi MongoDB dapat dilihat melalui postingan sebelumnya tentang cara instalasi dan menjalankan MongoDB.

## __UPDATE DATA__
Query ubah data berdasarkan suatu ID dan mengubah isi dari exampleColumn.
### __update satu baris__
db.getCollection('example_collection').updateOne({_id: ObjectId("5d8927e1a344a7b795a19746")}, {$set: {exampleColumn: "new value"}})
### __update banyak baris__
db.getCollection('example_collection').updateMany({someColumn: {$eq: null}}, {$set: {exampleColumn: "new value"}})

## __HAPUS DATA__
### __Hapus satu baris__
db.getCollection('example_collection').remove({_id: ObjectId("5bf70ac567f041b69724f910")})
### __Hapus semua baris, tapi tidak menghapus collection / tabel__
db.getCollection('example_collection').remove({})
### __Hapus Suatu Data Dalam List atau Array__
{
  name: "Example Name",
  description: [
    "hello",
    "world"
  ]
}


