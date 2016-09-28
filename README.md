# mongodb-query

### 1. Create database "academic"

```
use academic
```

### 2. List all active database

```
show dbs
```

### 3. Create or activate database

```
use YOUR_DB_NAME
```

### 4. Create collection "prodi"

```
db.createCollection("prodi")
```

### 5. Create collection "mahasiswa"

```
db.createCollection("mahasiswa")
```

### 6. Show collection structure "mahasiswa"

```
var col_list = db.mahasiswa.findOne()
for (var col in col_list){ print (col, "::", typeof col) }
```

### 7. Insert 5 records to "prodi"

```
db.prodi.insert([
  {"title": "Bio Science"},
  {"title": "Computer Science"},
  {"title": "Computer Engineering"},
  {"title": "Electrical Engineering"},
  {"title": "Mechanical Engineering"}
])
```

### 8. Insert 3 records to "mahasiswa"

```
db.mahasiswa.insert([
  {
    "nim": "1401000001",
    "name": "Septhianto Diga",
    "address": "Jakarta",
    "prodi": {
      "$ref": "prodi",
      "$id": ObjectId("57eb8aacbac062802e7c2836"),
      "$db": "academic"
    }
  },
  {
    "nim": "1401000002",
    "name": "Tevinstein Amosd",
    "address": "Jakarta Barat",
    "prodi": {
      "$ref": "prodi",
      "$id": ObjectId("57eb8aacbac062802e7c2837"),
      "$db": "academic"
    }
  },
  {
    "nim": "1401000003",
    "name": "Lilianti Wibiesono",
    "address": "Jakarta Timur",
    "prodi": {
      "$ref": "prodi",
      "$id": ObjectId("57eb8aacbac062802e7c2838"),
      "$db": "academic"
    }
  },
  {
    "nim": "1401000004",
    "name": "Ronald Ishak",
    "address": "Jakarta Selatan",
    "prodi": {
      "$ref": "prodi",
      "$id": ObjectId("57eb8aacbac062802e7c2839"),
      "$db": "academic"
    }
  },
  {
    "nim": "1401000005",
    "name": "Peter Raswono",
    "address": "Jakarta Pusat",
    "prodi": {
      "$ref": "prodi",
      "$id": ObjectId("57eb8aacbac062802e7c283a"),
      "$db": "academic"
    }
  }
])
```

### 9. List all records of "mahasiswa"

```
db.mahasiswa.find().pretty()
```

### 10. Select only name and address from "mahasiswa"

```
db.mahasiswa.find({},{"nim":1,"name":1,"address":1}).pretty()
```

### 11. Select only nim, name, and address with specific nim from "mahasiswa"

```
db.mahasiswa.find({"nim":"1401000001"},{"nim":1,"name":1,"address":1}).pretty()
```

### 12. Select all records from "mahasiswa" and sort by name ascending

```
db.mahasiswa.find().sort({"name":1}).pretty()
```

### 13. Select all records from "prodi" and sort by title ascending and descending

```
db.prodi.find().sort({"title":1}).pretty() // ascending
db.prodi.find().sort({"title":-1}).pretty() // descending
```

## Bonus - Backup db Mongo

```
mongodump --out YOUR_EXPORT_PATH
```
