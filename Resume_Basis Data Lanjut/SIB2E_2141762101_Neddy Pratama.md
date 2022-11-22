Nama	: Neddy Pratama Wiryawan
Kelas	: SIB 2E
NIM	: 2141762101
UPDATE DATA MONGODB
A.	Update Data di MongoDB
Untuk meng-update data ke document kita dapat menggunakan method updateOne() atau updateMany(). 
Untuk parameter pertama adalah objek query untuk menetukan dokumen yang ingin diupdate atau dokumen yang akan diupdate. 
Lalu untuk parameter kedua adalah data yang akan diupdate.

1.	updateOne()
updateOne() akan memperbaruhi 1 dokumen yang ditemukan cocok denga query yang disediakan. Contoh:
db.posts.updateOne( {title: "Post Title 1" }, {$set: {likes: 2 } } )
update judul dukumen "Post Title 1" bagian likes dengan "2"

Jika memasukkan dokumen tetapi dokumen tidak ditemukan, maka gunakan upsert.
db.posts.updateOne(
	{title: "Post Title 5" },
	{ $set:
		{
			title : "Post Title 5",
			body: "Body of post.",
			category: "Event",
			likes: 5,
			tags: ["news", "events"],
			date: Date()
		}
	},
	{ upsert : true }
)

2.	updateMany()
Metode updateMany() akan memperbaruhi semua dokumen yang cocok denga query yang disediakan. 
Contoh:
db.posts.updateMany({}, {$inc: { likes: 1 } })
Memperbaruhi semua dokumen dengan “1” menggunakan increment operator

B.	delete di MongoDB
Untuk menghapus dokumen dapat menggunakan metode deleteOne() atau deleteMany(). 
1.	deleteOne()
Metode deleteOne() akan menghapus menghapus 1 dokumen yang cocok dengan query yang akan dihapus.
Contoh:
db.posts.deleteOne({ title: "Post Title 5" })
Menghapus dokumen dengan nama “Post Title 5”

2.	deleteMany()
Metode deleteMany() akan menghapus semua dokumen yang cocok dengan query yang ingin dihapus.
Contoh:
db.posts.deleteMany({ category: "Tecnology" })
Menghapus semua dokumen yang category = “Tecnology”

C.	Sort di MongoDB
Agregasi ini mengurutkan semua dokumen dalam urutan sortir yang telah ditentukan.
Dan ingat bahwa urutan tahapan itu penting.
Setiap tahap hanya bertindak berdasarkan dokumen yang disediakan oleh tahap sebelumnya.
Untuk model pengurutannya dapat menggunakan 1 atau -1.
Untuk ascending adalah 1 dan unutk descending adalah -1.
Contoh:
db.listingsAndReviews.aggregate([
	{ $sort: { "accommodates" : -1 }}
])
Mengurutkan dokumen dari berdasarkan “accommodates” dalam DESC
