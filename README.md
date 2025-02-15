Library Management System Using MongoDB

This project demonstrates the implementation of a Library Management System using MongoDB (mongosh). It covers key concepts like database creation, collection setup, CRUD operations, and advanced queries.

Features

- Database Name: LibraryDB
- Collections:
  - Books: Stores information about the books.
  - Authors: Contains details about authors.
  - Patrons: Tracks the library's patrons.

Included Commands

- Create the database and collections.
- Insert multiple documents using insertMany.
- Perform CRUD operations (Create, Read, Update, Delete).
- Execute advanced MongoDB queries.

Prerequisites

1. Install MongoDB: Download and install MongoDB from the official website.
2. Install and Configure Mongosh: Ensure mongosh is installed and accessible in your terminal.
3. Start MongoDB Server: Run mongod in your terminal to start the MongoDB server.

Step-by-Step Guide

1. Start MongoDB Shell
- Open your terminal and start the MongoDB shell by typing:  
  mongosh

- Verify the connection with:  
  show dbs

2. Create the Database
- Switch to the LibraryDB database with:  
  use LibraryDB

3. Create Collections and Insert Data
- Books Collection: Insert details about books.
- Authors Collection: Insert information about authors.
- Patrons Collection: Insert details about library patrons.

CRUD Operations

READ:
- Find all books:  
  db.Books.find().pretty();

- Find a specific book by title:  
  db.Books.find({ title: "To Kill a Mockingbird" }).pretty();

- Find books by a specific author:  
  db.Books.find({ author_id: 5 }).pretty();

- Find all available books:  
  db.Books.find({ available: true }).pretty();

UPDATE:
- Mark a book as borrowed:  
  db.Books.updateOne({ _id: 3 }, { $set: { available: false } });

- Add a genre to a book:  
  db.Books.updateOne({ _id: 8 }, { $addToSet: { genres: "Classic" } });

- Add a borrowed book to a patron’s record:  
  db.Patrons.updateOne({ _id: 5 }, { $addToSet: { borrowed_books: 10 } });

DELETE:
- Delete a book by title:  
  db.Books.deleteOne({ title: "Brave New World" });

- Delete an author:  
  db.Authors.deleteOne({ _id: 3 });

Advanced Queries

- Find books published after 1950:  
  db.Books.find({ published_year: { $gt: 1950 } }).pretty();

- Find all American authors:  
  db.Authors.find({ nationality: "American" }).pretty();

- Set all books to available:  
  db.Books.updateMany({}, { $set: { available: true } });

- Find available books published after 1950:  
  db.Books.find({ available: true, published_year: { $gt: 1950 } }).pretty();

- Find authors whose names contain "George":  
  db.Authors.find({ name: { $regex: "George" } }).pretty();

- Increment the published year of books from 1869 by 1:  
  db.Books.updateMany({ published_year: 1869 }, { $inc: { published_year: 1 } });

Verification

- Verify database creation:  
  show dbs

- Verify collections:  
  show collections

- Verify inserted data:  
  db.Books.find().pretty(),  
  db.Authors.find().pretty(),  
  db.Patrons.find().pretty();
