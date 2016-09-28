# mongodb-query

#### 1. Query Membuat Database Akademik
use academic


#### 2. Query Menampilkan semua database
show dbs

#### 3. Query Membuat atau mengaktifkan database
use academic


#### 4. Membuat Collection Prodi
db.createCollection("prodi" )

#### 5. Membuat Collection Mahasiswa beserta referencenya
db.mahasiswa.insert({"nim":"1401078576","nama":"Ivan Gerard","alamat":"Citra Garden","prodi":{"$ref":"prodi","$id":ObjectId("57eb667818a6897a638f8b90"),"$db":"academic"}})

#### 6. Melihat struktur Collection Mahasiswa
var schematodo = db.mahasiswa.findOne()
for (var key in schematodo) { print (key, typeof key) ; }

#### 7. Menginput 5 data kedalam collection prodi
db.prodi.insert({"namaprogram":"Ilmu Komputer","jurusan":"Sistem Informasi"})


#### 8. Menginput 3 data kedalam collection mahasiswa
db.mahasiswa.insert({"nim":"1401078576","nama":"Ivan Gerard","alamat":"Citra Garden","prodi":{"$ref":"prodi","$id":ObjectId("57eb667818a6897a638f8b90"),"$db":"academic"}})


#### 9. melihat isi collection mahasiswa
db.mahasiswa.find().pretty()


#### 10. Menampilkan key nama dan alamat dalam collection mahasiswa
db.mahasiswa.find({}, {key:true,nama:true,alamat:true}).pretty()

#### 11. Menampilkan key nim,nama,alamat, dari data mahasiswa yang mempunyai nim tertentu
db.mahasiswa.find({"nim" : "1401078576"}).pretty()


#### 12. Menampilkan semua data mahasiswa secara urut berdasarkan nama secara orderby
db.mahasiswa.find()._addSpecial( "$orderby", { nama : -1 } )
db.mahasiswa.find().sort( { "nama": 1 } ).pretty()

#### 11. Menampilkan semua data prodi secara urut berdasarkan nama prodi secara ascending maupun descending
db.mahasiswa.find().sort( { "nama": 1 } ).pretty()
db.mahasiswa.find().sort( { "nama": -1 } ).pretty()
