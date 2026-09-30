# Library Management System

## 1. Project Overview

The **Library Management System** is a database project developed using MySQL and MySQL Workbench. It is designed to manage library information, including students, authors, books, librarians, and book issue and return records.

The project demonstrates relational database design, SQL queries, primary and foreign keys, integrity constraints, table relationships, and database normalization principles.

## 2. Objectives

* To design a relational database for managing library records.
* To store student, author, book, librarian, and issue details.
* To establish relationships between related tables.
* To maintain data accuracy using keys and constraints.
* To retrieve and manage information using SQL queries.
* To understand database normalization and reduce unnecessary data duplication.

## 3. Technologies Used

* **Database:** MySQL
* **Database Tool:** MySQL Workbench
* **ER Diagram Tool:** Draw.io
* **Language:** SQL

## 4. Database Tables

The database contains five tables.

| Table     | Description                                                                     |
| --------- | ------------------------------------------------------------------------------- |
| STUDENT   | Stores student details such as ID, name, email, phone, and department.          |
| AUTHOR    | Stores author IDs and names.                                                    |
| BOOK      | Stores book IDs, titles, prices, categories, and author references.             |
| ISSUE     | Stores issue IDs, student IDs, book IDs, issue dates, return dates, and status. |
| LIBRARIAN | Stores librarian IDs, names, and email addresses.                               |

## 5. Database Relationships

The database contains the following relationships:

* **AUTHOR to BOOK:** One author can be associated with multiple books.
* **STUDENT to ISSUE:** One student can have multiple issue records.
* **BOOK to ISSUE:** One book can appear in multiple issue records over time.
* **LIBRARIAN:** Maintained as a separate table in the current design.

Foreign keys connect the related tables and help maintain referential integrity.

## 6. Features

* Create and manage library database tables.
* Store student and author information.
* Maintain book details and prices.
* Record book issue and return transactions.
* Track whether a book is issued or returned.
* Retrieve data using SELECT queries.
* Filter records using WHERE conditions.
* Sort data using ORDER BY.
* Combine related records using INNER JOIN and LEFT JOIN.
* Count records using COUNT().
* Group records using GROUP BY.
* Update issue status and return dates.
* Apply constraints to maintain data integrity.

## 7. SQL Concepts Covered

### DDL (Data Definition Language)

* CREATE DATABASE
* CREATE TABLE

### DML (Data Manipulation Language)

* INSERT
* UPDATE

### Data Retrieval

* SELECT
* WHERE
* ORDER BY
* INNER JOIN
* LEFT JOIN
* GROUP BY
* COUNT()

### Constraints

* PRIMARY KEY
* FOREIGN KEY
* NOT NULL
* UNIQUE
* CHECK
* DEFAULT

### Other Database Concepts

* NULL value handling
* Relational database design
* One-to-many relationships
* Entity Relationship (ER) modelling
* Database integrity
* Normalization principles up to Third Normal Form (3NF)

## 8. Database Normalization

The database design follows basic normalization principles to reduce unnecessary duplication and maintain data consistency.

* **First Normal Form (1NF):** Columns contain atomic values, and each record is identified by a primary key.
* **Second Normal Form (2NF):** Tables use single-column primary keys, avoiding partial dependencies on composite keys.
* **Third Normal Form (3NF):** Student, author, book, issue, and librarian information are stored in separate tables to reduce unnecessary duplication.

The design uses separate entities and foreign keys to represent relationships between records.

*Note: These are design principles. A formal normalization proof requires documenting the functional dependencies and candidate keys for each relation.*

## 9. Example SQL Queries

### Display all books

```sql
SELECT * FROM BOOK;
```

### Display books with their authors

```sql
SELECT
    BOOK.Book_ID,
    BOOK.Title,
    AUTHOR.Author_Name
FROM BOOK
JOIN AUTHOR
ON BOOK.Author_ID = AUTHOR.Author_ID;
```

### Display issued books with student details

```sql
SELECT
    ISSUE.Issue_ID,
    STUDENT.Name AS Student_Name,
    BOOK.Title AS Book_Title,
    ISSUE.Issue_Date,
    ISSUE.Return_Date,
    ISSUE.Status
FROM ISSUE
JOIN STUDENT
ON ISSUE.Student_ID = STUDENT.Student_ID
JOIN BOOK
ON ISSUE.Book_ID = BOOK.Book_ID;
```

### Display currently issued books

```sql
SELECT *
FROM ISSUE
WHERE Status = 'Issued';
```

### Count books by category

```sql
SELECT
    Category,
    COUNT(*) AS Total_Books
FROM BOOK
GROUP BY Category;
```

### Display books from highest to lowest price

```sql
SELECT *
FROM BOOK
ORDER BY Price DESC;
```

## 10. Project Files

The repository may contain the following files:

* `library_management.sql` — SQL script for creating tables, inserting data, and executing queries.
* `Library_Management_ER_Diagram.png` — Exported ER diagram image.
* `Library_Management_ER_Diagram.drawio` — Editable ER diagram source file.
* `README.md` — Project documentation.

## 11. How to Run the Project

1. Install MySQL Server and MySQL Workbench.
2. Open MySQL Workbench and connect to your MySQL server.
3. Open the `library_management.sql` script.
4. Execute the SQL statements to create the database and tables and insert sample records.
5. Run the SELECT and JOIN queries to view and verify the records.

If the SQL script contains only queries and not the database creation or sample INSERT statements, add those statements before using this procedure.

## 12. Future Enhancements

* Add a graphical user interface.
* Implement student and librarian login.
* Add book search functionality.
* Track available book copies.
* Generate overdue book reports.
* Add fine calculation for late returns.

## 13. Conclusion

The Library Management System demonstrates the practical application of relational database concepts using MySQL. It provides experience in designing tables, defining relationships, applying constraints, writing SQL queries, retrieving related information, and understanding normalization principles.
