# TEORI BASIS DATA LANJUT RANGKUMAN QUERY UPDATE, DELETE, SORTING
## RASYID RAZEKA ALAMSYAH_2141762077_18_D4-SIB 2E
======================================================================================================================================
### PENGERTIAN MONGODB
MongoDB adalah salah satu jenis database NoSQL yang cku populer digunakan dalam pengembangan website dan MongoDB menggunakan dokumen dengan format JSON. Sistem database ini menggunakan beberapa komponen penting, yaitu database, collection, dan document. Database merupakan wadah dengan struktur penyimpanan yang disebut collection. Collection adalah  tempat kumpulan informasi data yang berbentuk dokumen. Collection dipadankan seperti tabel-tabel yang berisi data pada database SQL. Sedangkan document satuan unit terkecil dalam MongoDB. Query yang digunakan ialah find() untuk select, 
### UPDATE DATA
Pada MongoDB kita juga bisa melakukan perubahan ada data yang telah dimasukkan. Query yang digunakan ialah db.namaCollection.update(). Sebelum dilakukannya update harus dilakukan find() terlebih dahulu dengan query yang digunakan db.namaCollection.find(). Contoh penggunaannya seperti dibawah ini :
![alt text](http://2.bp.blogspot.com/-OTs7hJWByak/VoSZqSl4v-I/AAAAAAAAAm0/itu3hFBUUus/s640/update.PNG)
### DELETE DATA
Pada MongoDB kita juga bisa melakukan penghapusan data yang telah dimasukkan. Query yang digunakan ialah db.namaCollection.remove(). Sebelum dilakukan remove harus dilakukan find terlebih dahulu dengan query yang digunakan db.namaCollection.find(). Contoh penggunaannya seperti dibawah ini :
![alt text](http://4.bp.blogspot.com/-qpSownPf7EE/VoSbJ8c8RqI/AAAAAAAAAnA/BUm1X4UT570/s640/delete.PNG)
### SORTING DATA
Pada MongoDB kita juga bisa melakukan pengurutan data yang telah dimasukkan. Query yang digunakan ialah db.namaCollection.sort(). Sebelum dilakukan sort harus dilakukan find terlebih dahulu dengan query yang digunakan db.namaCollection.find(). Contoh penggunaannya seperti dibawah ini :
![alt text](https://www.sridianti.com/wp-content/media/2022/09/text-description-automatically-generated-111-400x167.png)