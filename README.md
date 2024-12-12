# MongoDB CRUD Operations Task

This repository demonstrates MongoDB CRUD (Create, Read, Update, Delete) operations using the MongoDB shell. The task is aimed at practicing essential database operations and building a deeper understanding of MongoDB commands.



## **Description**

The project uses a "library" database containing a "books" collection. The collection includes information about books, such as their title, author, published year, and genre. The following operations are performed:

### **1. Create Operation**
- **Create a new database:** `library`
- **Create a collection:** `books`
- **Insert a document** with details of a book.

### **2. Read Operation**
- Retrieve all documents.
- Find documents matching specific criteria (e.g., author is "J.K. Rowling").
- Fetch the document with the earliest published year.

### **3. Update Operation**
- Update the published year of a specific book.
- Add a new field `genre` to all documents.

### **4. Delete Operation**
- Remove a specific book by title.
- Delete all books published before a certain year.

### **5. Advanced Query**
- Retrieve the top 3 recently published books.
- Search for books where the title contains "MongoDB" or "NoSQL".

---

## **Prerequisites**

- MongoDB installed and running.
- Access to MongoDB shell (`mongosh`) or a client like MongoDB Compass.

---

## **Setup and Execution**

1. **Connect to MongoDB shell**:
   ```bash
   mongosh
   ```
2. **Switch to the database**:
   ```javascript
   use library
   ```
3. **Execute the following queries** for each operation (see below).

---

## **Queries Used**

### **1. Create Operation**
```javascript
// Create and switch to the "library" database
use library

// Insert a book document into the "books" collection
db.books.insertOne({
  title: "The Alchemist",
  author: "Paulo Coelho",
  published_year: 1988
})
```

### **2. Read Operation**
```javascript
// Retrieve all documents
db.books.find()

// Find books by "J.K. Rowling"
db.books.find({ author: "J.K. Rowling" })

// Fetch the earliest published book
db.books.find().sort({ published_year: 1 }).limit(1)
```

### **3. Update Operation**
```javascript
// Update the published year of "The Catcher in the Rye"
db.books.updateOne(
  { title: "The Catcher in the Rye" },
  { $set: { published_year: 2024 } }
)

// Add a "genre" field to all documents
db.books.updateMany(
  {},
  { $set: { genre: "Mystery" } }
)
```

### **4. Delete Operation**
```javascript
// Remove the book "1984"
db.books.deleteOne({ title: "1984" })

// Delete all books published before 2000
db.books.deleteMany({ published_year: { $lt: 2000 } })
```

### **5. Advanced Query**
```javascript
// Retrieve the top 3 recently published books
db.books.find().sort({ published_year: -1 }).limit(3)

// Search for books with "MongoDB" or "NoSQL" in the title
db.books.find({ title: { $regex: "MongoDB|NoSQL", $options: "i" } })
```

---

## **How to Use**

1. Clone this repository:
   ```bash
   git clone <repository_url>
   ```
2. Follow the steps in the `Queries Used` section to execute the commands in MongoDB shell.

---

## **License**

This project is licensed under the MIT License. See the LICENSE file for details.



