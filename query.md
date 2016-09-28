# QUERY

## 1. Membuat database academic##

```
use academic
```

## 2. Menampilkan semua data database##

```
show dbs atau show database
```

## 3. Membuat atau mengaktifkan database##

```
use academic
```

## 4. Membuat collection prodi##

```
db.createCollection("prodi")
```

atau sekaligus insert data

```
db.prodi.insert({"kode_prodi":"GP","nama_prodi":"Game Programming","jurusan":"Teknik Informatika"})
```

## 5. Membuat collection mahasiswa beserta referencenya##
```
db.mahasiswa.insert(
  {"nim":"2",
  "nama":"Donald Duck",
  "alamat":"Silicon Valley",
  "prodi":{
    "$ref":"prodi",
    "$id" : ObjectId("57eb6616ee2d00994f939ec3"),
    "$db" : "academic"
  }})
```

## 6. Melihat struktur collection mahasiswa##
```
var schematodo = db.mahasiswa.findOne()
for (var key in schematodo) {print (key, typeof key);}
```

## 7. Menginput 5 data ke dalam colelction prodi##
```
db.prodi.insertMany(
[
{ "kode_prodi" : "GP", "nama_prodi" : "Game Programming", "jurusan" : "Teknik Informatika" },
{ "kode_prodi" : "SA", "nama_prodi" : "System Analyst", "jurusan" : "Teknik Informatika" },
{"kode_prodi":"AL", "nama_prodi":"Arus Lemah","jurusan":"Teknik Elektronika"}, {"kode_prodi":"AK","nama_prodi":"Arus Kuat", "jurusan":"Teknik Elektronika"},
{"kode_prodi":"AK","nama_prodi":"Arus Kuat", "jurusan":"Teknik Elektronika"},
{
  "kode_prodi" : "MD",
"nama_prodi" : "Mobile Dev",
"jurusan" : "Teknik Informatika"
}
] )
```

## 8. Menginput 3 data ke dalam collection mahasiswa##
```
db.mahasiswa.insertMany([

{ "nim":"1",
  "nama":"Mickey Mouse",
  "alamat":"Bendungan Hilir",
  "prodi": {
    "$ref" : "prodi",
    "$id"  : ObjectId("57eb66c5ee2d00994f939ec4"),
    "$db"  : "academic"
   }
},
{ "nim":"2",
  "nama":"Donald Duck",
  "alamat":"Silicon Valley",
  "prodi":{
    "$ref":"prodi",
    "$id" : ObjectId("57eb6616ee2d00994f939ec3"),
    "$db" : "academic"
  }
},
{ "nim":"3",
  "nama":"Paman Gober",
  "alamat":"Disneyland Jepang",
  "prodi":{
    "$ref" : "prodi",
    "$id"  : ObjectId("57eb66c5ee2d00994f939ec4"),
    "$db"  : "academic"    
  }
}])
```

## 9. Melihat isi collection mahasiswa##
```
db.mahasiswa.find().pretty()
```

## 10. Menampilkan key nama dan alamat dalam collection mahasiswa##
```
db.mahasiswa.find({}, {"nama":1,"alamat":1,"_id":0}).pretty()
```

## 11. Menampilkan key nim, nama, dan alamat dari data mahasiswa yang mempunyai nim tertentu##
```
db.mahasiswa.find({"nim":"1"},{"nim":1,"nama":1,"alamat":1,"_id":0}).pretty()
```

## 12. Menampilkan semua data mahasiswa secara urut berdasarkan nama secara ascending##
```
db.mahasiswa.find().sort({"nama":1}).pretty()
```

## 13. Menampilkan semua data prodi scara urut berdasarkan nama_prodi##
```
db.prodi.find().sort({"nama_prodi":1}).pretty() // Ascending
db.prodi.find().sort({"nama_prodi":-1}).pretty() // Descending
```

## NOTE ##
```
var maha = db.mahasiswa.findOne({"nama":"Donald Duck"})
var dbRef = maha.prodi
db[dbRef.$ref].findOne({"_id":(dbRef.$id)})
for (var key in maha) {print (key, maha[key])}
```

**update**
```
db.mahasiswa.update({"nim":"2"},{$set:{"prodi":{"$ref" : "prodi","$id" : ObjectId("57eb6aa9ee2d00994f939ec6")}}})
```
