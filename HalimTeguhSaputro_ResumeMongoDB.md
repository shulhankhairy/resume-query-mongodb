**RESUME TEORI BASIS DATA LANJUT**

**MongoDB**

oleh :

Halim Teguh Saputro

2E

2141762122

**PROGRAM STUDI D-IV SISTEM INFORMASI BISNIS**

**JURUSAN TEKNOLOGI INFORMASI **

**POLITEKNIK NEGERI MALANG **

Jl. Soekarno Hatta No .9, Jatimulyo, Kec. Lowokwaru, Kota Malang,

JawaTimur 65141

# Apa itu MongoDB?

MongoDB adalah salah satu jenis database NoSQL (Not Only SQL) yang berbasis dokumen dengan format JSON. Jadi, MongoDB tidak memiliki relasi, data yang disimpan tidak dalam format table. Database NoSQL ini dapat menutupi kekurangan-kekurangan pada SQL biasa seperti skema database yang kaku (fixed), susah membuat query untuk table dengan relasi yang kompleks, susah di perbesar skalanya, dsb

MongoDB ini banyak digunakan karena memiliki keunggulan utama yaitu dapat menampung dan mengelola data dalam jumlah yang besar dan bervariasi, dan tidak terstruktur. Kita dapat menggunakan MongoDB ini ketika kita menemui data yang diintegrasikan dalam jumlah besar. Missal memiliki Toko Kopi yang popular, bahkan saking populernya setiap 1 jam selalu ada sekitar 50 orang yang masuk. Selain itu, dengan mongoDB data dapat di upgrade dengan cepat dan lebih kompleks. Suatu aplikasi pasti memerlukan pengolahan data dengan performa yang tinggi apalagi menggunakan cloud computing. Sehingga akan lebih baik bila penggunaan datanya menggunakan mongoDB.

# Query pada MongoDB

Pada MongoDB query yang biasa digunakan ada Create() (untuk membuat sebuah collection baru), Insert() (untuk menambahkan data), Update() (untuk mengubah data), dan Remove() (untuk menghapus data).

1. Membuat Collection Baru

Untuk membuat collection baru dapat menggunakan command:

db.createCollections("nama\_collection")

contoh :

db.createCollections("toko\_kopi")

1. Mengisi/menambahkan data

Setelah membuat sebuah collection, saatnya kita untuk mengisikan data tersebut. Sturktur dalam menambahkan data adalah sebagai berikut:

db.(nama\_collection).insert(isi data)

Dalam mengisi data pada sebuah collection terdapat 3 jenis command yaitu, insert(), InsertOne(), dan InsertMany().

1. insertOne(), sesuai dengan namanya command ini digunakan untuk menginput atau menambahkan 1 data saja. Contoh:

{

    db.(toko\_kopi).insertOne(
    {
    nama: "Cappucino",
    harga: 20000
    }
    )

1. insertMany(), untuk insertMany() penggunaannya mirip dengan command sebelumnya namun dengan insertMany() kita dapat mengisi banyak data sekaligus. Contoh:

{

    db.(toko\_kopi).insertMany(
      [
        {
          nama: "Cappucino",
          harga: 20000
        },
        {
        nama: "Coffe Latte",
        harga: 15000
        },
        {
        nama: "Expresso",
        harga: 22000
        },
      ]
    )

1. insert(), untuk command ini mirip dengan sebelumnya namun, memiliki kelebihan dari pada dua command sebelumnya, yaitu dapat mengisikan data yang berisikan sebuah data lain (object of document). Contoh:

db.(toko\_kopi).insert(

  [

    {

      nama: "Cappucino",

      harga: 20000,

      pegawai:

      {

        nama\_pegawai: "Halim",

        alamat: "Malang"

      }

    },

    {

      nama: "Coffe Latte",

      harga: 15000

      {

        nama\_pegawai: "Teguh",

        alamat: "Surabaya"

      }

    }

  ]

)

1. Mengubah data

Selanjutnya, kita dapat mengubah data yang telah kita buat dengan menggunakan command update() dengan strukturnya sebagai berikut:

db.(nama\_collection).update(\<datalama\>, \<databaru)

Contoh:

db.toko\_kopi.update(

  {

    nama: "Coffe Latte",

  },

  {

    nama: "Coffe Latte and Cream"

  }

)

1. Menghapus data

Di dalam mongoDB, kita juga dapat menghapus data yang mungkin tidak dibutuhkan lagi dengan struktur sebagai berikut:

db.(nama\_collection).remove(\<data\_yang\_akan\_dihapus)

Contoh:

db.toko\_kopi.remove(

  {

    nama: "Expresso"

  }

)

1. Sorting data

Dengan menggukan mongoDB, kita juga bisa mengurutkan data-data yang ada pada suatu collection. Untuk mengurutkan suatu data dapat menggunakan command aggreagation dengan struktur sebagai berikut:

db.(nama\_collection).aggregate(

  [

    { $sort : { (nama\_field) : 1 } }

  ]

)

Nb: untuk mengurutkan secara ascending dapat mengisikan data 1, sedangkan descending dapat mengisikan data -1

Contoh:

db.(toko\_buku).aggregate(

  [

    { $sort : { (harga) : 1 } }

  ]

)
