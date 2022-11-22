{
  "metadata": {
    "language_info": {
      "codemirror_mode": {
        "name": "python",
        "version": 3
      },
      "file_extension": ".py",
      "mimetype": "text/x-python",
      "name": "python",
      "nbconvert_exporter": "python",
      "pygments_lexer": "ipython3",
      "version": "3.8"
    },
    "kernelspec": {
      "name": "python",
      "display_name": "Python (Pyodide)",
      "language": "python"
    }
  },
  "nbformat_minor": 4,
  "nbformat": 4,
  "cells": [
    {
      "cell_type": "markdown",
      "source": "### **Nama     : Indah Retno Iriani**\n### **NIM       : 2141762104**\n### **Kelas    : SIB-2E**\n\n---\n\n#### Resume :\n1.\tQuery\nQuery merupakan permintaan data atau informasi dari database menggunakan kode yang disebut dengan bahasa query. Dengan begitu sistem dapat memahami dan memproses query yang sesuai. \n\n2.\tUpdate data\nUntuk mengubah data,  dapat menggunakan fungsi update().\n> db.koleksi.update(query, data baru).\n    \n    Keterangan: \n    - query adalah kata kunci data yang akan kita ubah, sama seperti Where dalam SQL.\n    - data baru adalah data baru atau pembaruan dari data yang lama.\n\n    Untuk melakukan update dokumen dapat menggunakan metode *updateOne()* atau *updateMany()*. \n    - Metode updateOne() digunakan untuk melakukan update pada satu dokumen yang ditemukan.\n    > db.posts.find({title : \"Post Title 1\"})\n    \n        > db.posts.updateOne( { title: \"Post Title 1\" }, { $set: { likes: 2 } } )\n    \n    - Metode updateMany() digunakan untuk melakukan update pada seluruh data yang cocok. Contoh :\n\n    > db.posts.updateMany({}, {$inc: { likes: 1 }})\n    \n\n3.\tDelete data \nUntuk menghapus data, kita bisa menggunakan perintah \n> remove(). db.koleksi.remove(query)\n\n    Sama seperti update data, penghapusan data juga memiliki query untuk menentukan   data yang akan dihapus. Untuk menghapus dapat dilakukan metode seperti dibawah :\n    - Metode deleteOne() yaitu menghapus dokumen pertama yang memiliki kecocokan dengan query. Contohnya :\n    > db.posts.deleteOne({ title: \"Post Title 5\" })\n    \n    - Metode deleteMany() adalah metode yang digunakan untuk menghapus seluruh dokumen yang memiliki kecocokan dengan query. Contohnya :\n    > db.posts.deleteMany({ category: \"Technology\" })\n\n4.\tSorting data \nUntuk mengurutkan menggunakan metode sort() yang dapat diurutkan dari beaar ke kexil.ataulun dari kecil ke besar. Metode sort() mengambil satu parameter untuk fieldname dan satu parameter untuk direction (naik adalah default).\n    - Pengurutan menurun (descending)\n        Gunakan nilai -1 sebagai parameter kedua untuk mengurutkan dokumen secara menurun.\n    > Sort(“name”, -1) #descending\n\n    - \tPengurutan naik (ascending)\n    Pengurutan ascending adalah pengurutan dari kecil ke besar \n    > Sort(“name”, 1) #ascending\n\n    - \tContoh\n    Mengurutkan secara descending sesuai abjad berdasarkan nama\n    > Import pymongo\n    \n        > Myclient = pymobgi.MongoClient(mongodb://localhost:27017/”)\n    \n        > Mydb = myclient[“mydatabase”]\n    \n        > Mycol = mydb[“customers”]\n    \n        > mYdoc = mycol.find().sort(“name”, -1)\n    \n        > for × in mydoc:\n    \n        > Print(x)\n\n\n",
      "metadata": {}
    },
    {
      "cell_type": "code",
      "source": "",
      "metadata": {},
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": "",
      "metadata": {},
      "execution_count": null,
      "outputs": []
    }
  ]
}