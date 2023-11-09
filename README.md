MongoDB Exercise 01

**01.Create a Database called movies.**
``use movies
switched to db movies``

***02.Create a collection called moviedetails.***
``db.createCollection("moviedetails")
{ ok: 1 }``

**03.Create above 5 movie documents into a moviedetails collection.**

``db.moviedetails.insertMany([{MovieTitle: "Jurassic Park ", GenreType:"Adventure",Director:"Steven Spielberg",ReleaseYear:"1993"},{MovieTitle: "Forrest Gump ", GenreType:"Drama",Director:"Robert Zemeckies",ReleaseYear:"1994"},])
movies> db.moviedetails.insertMany([{MovieTitle: "Jurassic Park ", GenreType:"Adventure",Director:"Steven Spielberg",ReleaseYear:"1993"},{MovieTitle: "Forrest Gump ", GenreType:"Drama",Director:"Robert Zemeckies",ReleaseYear:"1994"},{MovieTitle: "Titanic ", GenreType:"Romance",Director:"James Cameron",ReleaseYear:"1997"},{MovieTitle: "The Dark Knight", GenreType:"Action",Director:"Christopher Nolan",ReleaseYear:"2008"},{MovieTitle: "Avatar", GenreType:"Science Fiction",Director:"James Cameron",ReleaseYear:"2009"}])
{
  acknowledged: true,
  insertedIds: {
    '0': ObjectId("654c9af930b4759db2324f73"),
    '1': ObjectId("654c9af930b4759db2324f74"),
    '2': ObjectId("654c9af930b4759db2324f75"),
    '3': ObjectId("654c9af930b4759db2324f76"),
    '4': ObjectId("654c9af930b4759db2324f77")
  }
}``

**04.List all documents created.**
``movie> db.moviedetails.find()
[
  {
    _id: ObjectId("654c9c2883231ea19eb525e5"),
    MovieTitle: 'Jurassic Park ',
    GenreType: 'Adventure',
    Director: 'Steven Spielberg',
    ReleaseYear: '1993'
  },
  {
    _id: ObjectId("654c9c2883231ea19eb525e6"),
    MovieTitle: 'Forrest Gump ',
    GenreType: 'Drama',
    Director: 'Robert Zemeckies',
    ReleaseYear: '1994'
  },
  {
    _id: ObjectId("654c9c2883231ea19eb525e7"),
    MovieTitle: 'Titanic ',
    GenreType: 'Romance',
    Director: 'James Cameron',
    ReleaseYear: '1997'
  },
  {
    _id: ObjectId("654c9c2883231ea19eb525e8"),
    MovieTitle: 'The Dark Knight',
    GenreType: 'Action',
    Director: 'Christopher Nolan',
    ReleaseYear: '2008'
  },
  {
    _id: ObjectId("654c9c2883231ea19eb525e9"),
    MovieTitle: 'Avatar',
    GenreType: 'Science Fiction',
    Director: 'James Cameron',
    ReleaseYear: '2009'
  }
]``


**05.List James Cameron’s movies.**

``movie> db.moviedetails.find({ "Director": "James Cameron" })
[
  {
    _id: ObjectId("654c9c2883231ea19eb525e7"),
    MovieTitle: 'Titanic ',
    GenreType: 'Romance',
    Director: 'James Cameron',
    ReleaseYear: '1997'
  },
  {
    _id: ObjectId("654c9c2883231ea19eb525e9"),
    MovieTitle: 'Avatar',
    GenreType: 'Science Fiction',
    Director: 'James Cameron',
    ReleaseYear: '2009'
  }
]``


**06.List  James Cameron’s movies released in 2009.**

``db.moviedetails.find({ "Director": "James Cameron" , "ReleaseYear":"2009"})
[
  {
    _id: ObjectId("654c9c2883231ea19eb525e9"),
    MovieTitle: 'Avatar',
    GenreType: 'Science Fiction',
    Director: 'James Cameron',
    ReleaseYear: '2009'
  }
]``


**07.Delete the movie which you don’t like.**
``db.moviedetails.remove({ "MovieTitle": "Jurassic Park" })
DeprecationWarning: Collection.remove() is deprecated. Use deleteOne, deleteMany, findOneAndDelete, or bulkWrite.
{ acknowledged: true, deletedCount: 0 }``

**08.Add the movie which is your favourite. **
``db.moviedetails.insertOne({MovieTitle: "Leo", GenreType:"Action",Director:"Lokesh",ReleaseYear:"2023"})
{
  acknowledged: true,
  insertedId: ObjectId("654ca12083231ea19eb525ea")
}``


**09.List movie Directed  by Christopher Nolan in 1994.**
``db.moviedetails.find({ "Director": "Christopher Nolan","Release Year":"1994" })``



**10.List out the Director’s Name in your document.**

``db.moviedetails.distinct("Director")
[
  'Christopher Nolan',
  'James Cameron',
  'Lokesh',
  'Robert Zemeckies',
  'Steven Spielberg'
]``


