# mongodb-query

## 1. Membuat database academic

```
use academic
```

## 2. Menampilkan semua database
```
show dbs
```

## 3. Membuat atau mengaktifkan database

```
use academic
```

## 4. Membuat collection Prodi

```
db.createCollection("Prodi")
```

## 5. Membuat collection Mahasiswa berserta referencenya
```
db.createCollection("Mahasiswa")
```

## 6. Melihat struktur collection Mahasiswa
```
var schema_mahasiswa = db.Mahasiswa.findOne();
for (var key in schema_mahasiswa) { print (key);}
```

## 7. Menginput 5 data kedalam collection prodi
```
db.Prody.insertMany([
  {"kode_prodi": 91,"nama_prodi":"Multimedia","jurusan":"Ilmu Komputer"},
  {"kode_prodi": 92,"nama_prodi":"teknik informatika","jurusan":"Ilmu Komputer"},
  {"kode_prodi": 93,"nama_prodi":"Game Developer","jurusan":"Ilmu Komputer"},
  {"kode_prodi": 94,"nama_prodi":"teknik jembatan dan irigasi","jurusan":"Civil"},
  {"kode_prodi": 95,"nama_prodi":"teknik bangunan","jurusan":"Civil"}
  ])
```


## 8. Menginputkan 3 data kedalam collection Mahasiswa
```
db.Mahasiswa.insertMany([
  {"nim":07092028,"nama":"Sahbana","alamat":"rao-rao","prodi":92},
  {"nim":07092027,"nama":"Tevinstein Amos","alamat":"makassar","prodi":92},
  {"nim":07092026,"nama":"Sephtianto Digachandra","alamat":"tangerang","prodi":92}
  ])
```
## 9. Melihat isi Collection Mahasiswa
```
db.Mahasiswa.find();
```


## 10. Menampilkan key nama dan alamat dalam collection Mahasiswa

```
db.Mahasiswa.find({ },{"nama":1,"alamat":1,"_id":0});
```
## 11. Menampilkan semua key nim, nama dan alamat dari data mahasiswa yang mempunyai nim tertentu

```
db.Mahasiswa.find({ },{"nim":1,"nama":1,"alamat":1,"_id":0});
```

## 12. Menampilkan semau data mashasiswa secara berurut berdasarkan nama dengan sort() secra ascending dan descending

Ascending
```
db.Mahasiswa.find().sort({"nama":1});

```
Descending
```
db.Mahasiswa.find().sort({"nama":-1});

```
## 13. Menampilkan semau data mashasiswa secara berurut berdasarkan nama dengan sort() secra ascending dan descending

Ascending
```
db.Prodi.find().sort({"nama":1});

```
Descending
```
db.Prodi.find().sort({"nama":-1});
