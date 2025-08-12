# Online Bookstore SQL Project

## 📌 Project Overview
This project demonstrates a complete **SQL-based database design** for an online bookstore.  
It includes **database creation, table structures, relationships, sample data insertion, and example queries** for analysis.

## 🗂 Database Structure
The database contains the following tables:
- **Authors** – Stores author details.
- **Books** – Stores book details, linked to authors.
- **Customers** – Stores customer information.
- **Orders** – Stores order records for customers.
- **OrderDetails** – Stores books purchased in each order.

## ⚙ Features
- Create and manage a relational database for a bookstore.
- Insert sample data for testing.
- Run queries to retrieve useful insights such as:
  - Books with their authors
  - Total sales per book
  - Orders with customer details

## 🛠 Technologies Used
- MySQL (compatible with MariaDB or other SQL-based systems)
- ANSI SQL for queries

## 📋 Example Queries
```sql
-- List all books with their authors
SELECT b.Title, a.Name AS Author, b.Price
FROM Books b
JOIN Authors a ON b.AuthorID = a.AuthorID;

-- Find total sales per book
SELECT b.Title, SUM(od.Quantity) AS TotalSold
FROM OrderDetails od
JOIN Books b ON od.BookID = b.BookID
GROUP BY b.Title;
