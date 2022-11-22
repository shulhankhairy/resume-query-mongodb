# MONGO DB

## 	Mongo db 
MONGODB merupakan database NOSQL (Not Only Sql) yang tidak mempunyai table, field, dan baris namun hanya memiliki collection dan document.
Seperti halnya database pada umumnya MongoDB juga memiliki 4 fungsi utama yaitu select  insert update delete. seperti kita ketahui bersama bahwa select digunakan untuk menampilkan data, insert digunakan untuk menyimpan data, update digunakan untuk mengubah data, delete digunakan untuk menghapus data.

Pada MongoDB query yang digunakan bukan select insert update dan delete namun menggunakan seperti berikut ini :

1.	select --> find()
2.	insert --> save()
3.	update --> update()
4.	delete --> remove()

Singkatnya, proses agregasi dalam mongodb adalah memproses data (record) untuk dikumpulkan menjadi satu atau dipisah-pisah. 

1.	INSERT
yang pertama dilakukan ialah masuk ke database anda kemudian untuk insert anda tidak perlu membuat table terlebih dahulu. Cukup aneh memang tapi seperti yang dijelaskan diatas MongoDB tidak memiliki table maupun field jadi untuk melakukan insert kita hanya perlu mengetikkan query seperti :

"( db.nama_collation.save({nama_kolom1:"isi",nama_kolom2:"isi"}); )"

Jika berhasil melakukan query itu akan muncul pemberitahuan WriteResult ({"nInserted" : jumlah_baris_data }). Kemudian kita bisa mengeceknya dengan melakukan query select . 

2. SELECT
Perintah SELECT pada MySQL adalah perintah yang digunakan untuk menampilkan data dari tabel yang ada di database dan dapat juga menjadi sebuah ekspesi. Namun pada dasarnya, perintah SELECT berfungsi untuk menampilkan data pada tabel secara keseluruhan.

db.nama_collation.find();

Untuk melakukan select secara spesifik, secara garis besar adalah seperti ini.

Model.find().select().exec(callback)

Jika kita pecah kode tersebut, mungkin bisa seperti ini

const schema = mongoose.schema({
   // schema collection})
mongoose.model(nama collection, schema).find().select(nama document yang ingin diselect).exec((err,data)=>{
    res.send(data) // data dari collection setelah spesific select})

Kunci dari tutorial kali ini ada di function select(). Disitulah nama document yang diseleksi saja yang akan keluar sebagai output "data" .
Tiap nama document tidak perlu dipisah dengan tanda koma, cukup dipisah dengan spasi. Cara penggunaan function select untuk seleksi nama document seperti berikut ini misalnya.

.select('nama email komentar')


3. UPDATE
maka akan muncul data anda dengan sudah memiliki id unik yang tercipta secara otomatis. Lalu untuk bagaimana untuk update data ?? caranya adalah seperti ini :
db.nama_collation.update({nama_kolom_syarat:"isi",{$set:(nama_kolom:"isi_baru")},false,true});

4. DELETE
untuk mengecek data silahkan gunakan query .find() seperti yang saya jelaskan diatas. lalu untuk melakukan delete data anda dapat menggunakan query seperti ini :

db.nama_collation.remove(nama_kolom:'isi');

Menghapus Database di MongoDB
MongoDB menyediakan perintah dropDatabase() untuk menghapus database yang digunakan saat ini. Sebelum menghapus, pastikan database yang digunakan terlebih dahulu, gunakan perintah db.
( > db
contohdb ) 

Jika yang muncul bukan database yang ingin dihapus, gunakan perintah ini:

( > use contohdb ) 

Pada dasarnya MongoDB tidak memberikan perintah apa pun untuk membuat database. Lalu bagaimana cara kita membuat database? Jawabannya adalah kita tidak membuat langsung database dalam MongoDB, kita hanya perlu menggunakan database dengan nama yang Anda sukai dan perlu menyimpan satu collection dalam database tersebut, lalu database baru akan terbuat. 


5. SORTING 
Secara garis besarnya, Sorting (Pengurutan) adalah suatu proses penyusunan kembali kumpulan objek menggunakan tata aturan tertentu. Sorting disebut juga sebagai suatu algoritma untuk meletakkan kumpulan elemen data ke dalam urutan tertentu berdasarkan satu atau beberapa kunci dalam tiap-tiap elemen.

Gunakan metode sort() untuk mengurutkan hasil dalam urutan secara naik atau menurun.
Metode sort() mengambil satu parameter untuk “fieldname” dan satu parameter untuk “direction” naik atau turun (naik adalah arah default).

