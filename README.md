# mongodb-query

##Membuat databse academic
input : use academic

output : switched to db academic

##Membuat collection department
input : db.createCollection("department")

output : { "ok" : 1 }

##Membuat collection student

input : db.createCollection("student")

output : { "ok" : 1 }

##Melihat struktur collection

var col_list= db.student.findOne();
for (var col in col_list) { print (col) ; }

##Menginput 5 data ke dalam collection

input :
db.department.insert([
    {code : "001", name : "Fakultas Ekonomi", major : { 1 : "akutansi", 2: "bisnis"}},
    {code : "002", name : "Fakultas Kedokteran", major : { 1 : "dokter gigi", 2: "dokter umum"}},
    {code : "003", name : "Fakultas MIPA", major : { 1 : "matematika", 2: "farmasi"}},
    {code : "004", name : "Fakultas ILMU PENDIDIKAN", major : { 1 : "BK", 2: "sastra inggris"}},
    {code : "004", name : "Fakultas TEKNIK", major : { 1 : "mesin", 2: "elektro"}}
  ])

  output :
  BulkWriteResult({
    "writeErrors" : [ ],
    "writeConcernErrors" : [ ],
    "nInserted" : 5,
    "nUpserted" : 0,
    "nMatched" : 0,
    "nModified" : 0,
    "nRemoved" : 0,
    "upserted" : [ ]
})
##Menginput 3 data ke dalam collection

db.student.insert([
{
  studentId:"1",
  name:"wahyu",
  address:"Jakarta",
  department:[{
      $ref: "department",
      $id: ObjectId("58b656028182c30e9d8eeae9"),
      $db: "academic"
  }]
},
{
  studentId:"2",
  name:"hidayat",
  address:"Jakarta",
  department:[{
      $ref: "department",
      $id: ObjectId("58b656028182c30e9d8eeaeb"),
      $db: "academic"
  }]
},
{
  studentId:"3",
  name:"daniel",
  address:"Jakarta",
  department:[{
      $ref: "department",
      $id: ObjectId("58b656028182c30e9d8eeaed"),
      $db: "academic"
  }]
}
])

#Melihat isi collection

db.getCollection('student').find({})

#Menampilkan key name dan address dalam collection
db.getCollection('student').find({},{name:1,address:1})
