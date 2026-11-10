# Library Management System

**Project Type:** DBMS Mini Project
**Course:** Bachelor of Computer Applications (BCA)
**Database:** MySQL (`librarydb`)
**Software:** MySQL Workbench

## 1. Introduction
The Library Management System is a mini project developed using MySQL. It maintains records of library members, available books and book borrowing activities.

The main objective is to understand how databases work and how SQL queries can be used to retrieve and manage information. Using this database we can identify popular books, check books that have not been returned, calculate late return fines and analyse borrowing activities.

## 2. Database Tables

**members** (students and faculty)

| Column | Description |
|--------|-------------|
| member_id | Primary key |
| member_name | Name of the member |
| member_type | Student or Faculty |
| joined_date | Date of joining |

**books**

| Column | Description |
|--------|-------------|
| book_id | Primary key |
| title | Book name |
| author | Author name |
| category | Book category |
| price | Price of the book |
| copies_available | Number of available copies |

**issues**

| Column | Description |
|--------|-------------|
| issue_id | Primary key |
| member_id | Foreign key referencing members |
| book_id | Foreign key referencing books |
| issue_date | Date when the book was issued |
| due_date | Expected return date |
| return_date | Actual return date (NULL = not returned) |

## 3. Database Relationships
- One member can have multiple issue records (1:N).
- One book can have multiple issue records (1:N).
- The `issues` table connects `members` and `books` using foreign keys.

![ERD](erd.jpg)

## 4. Sample Data

| Table | Total Records |
|-------|---------------|
| Members | 12 |
| Books | 15 |
| Issues | 32 |

Categories: Programming, Database, Networking, Fiction, Science and Mathematics.

## 5. Fine Calculation
Fine = Late Days x Rs. 2

- Student borrowing period: 14 days. Faculty borrowing period: 30 days.
- Books returned after the due date are late. Returned on the due date: no fine.
- A NULL return date means the book is currently issued.

## 6. SQL Concepts Used
Database and table creation, primary and foreign keys, SELECT and WHERE, COUNT and SUM, GROUP BY and HAVING, ORDER BY and LIMIT, INNER JOIN and LEFT JOIN, subqueries, NULL handling, DATEDIFF, RANK() window function, stored procedures, triggers.

## 7. Project Questions
**Phase 1 - Database Basics:** C1 ERD, C2 total counts.
**Phase 2 - SQL Queries:** C3 titles and copies per category, C4 top 5 borrowed books, C5 members who never borrowed, C6 currently issued books, C7 late returns and fines, C8 total fine per member, C9 student vs faculty, C10 rank members, C11 most popular category, C12 zero copies with pending issues.
**Phase 3 - Automation:** C13 stored procedure, C14 trigger.
**Phase 4 - Conclusion:** C15 suggestions (see `notes.md`).

## 8. Files Included

| File | Description |
|------|-------------|
| schema.sql | Creates the database and tables |
| insert_data.sql | Inserts sample records |
| queries.sql | SQL queries for C2 to C14 |
| notes.md | Query summaries and conclusions |
| erd.jpg | Entity Relationship Diagram |

## 9. How to Run
1. Open MySQL Workbench.
2. Run `schema.sql` to create the database and tables.
3. Run `insert_data.sql` to insert the sample records.
4. Select the `librarydb` database.
5. Run the queries from `queries.sql`.
6. Check the output for each question.

To verify the records:

```sql
USE librarydb;
SELECT COUNT(*) FROM members;
SELECT COUNT(*) FROM books;
SELECT COUNT(*) FROM issues;
```

Expected output: Members 12, Books 15, Issues 32.

## 10. Learning Outcomes
Through this project, I learned how to create and manage relational databases using MySQL. I gained practical knowledge of SQL queries, joins, aggregate functions, subqueries and window functions. I also learned how stored procedures and triggers can automate database operations in a real-world library system.

## 11. Conclusion
The Library Management System shows how MySQL can be used to maintain and analyse library records. The queries help identify popular books, members with pending returns and late return fines.
