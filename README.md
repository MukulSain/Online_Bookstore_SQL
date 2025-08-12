-- Database: Online Bookstore
CREATE DATABASE OnlineBookstore;
USE OnlineBookstore;

-- Table: Authors
CREATE TABLE Authors (
    AuthorID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL,
    Country VARCHAR(50)
);

-- Table: Books
CREATE TABLE Books (
    BookID INT PRIMARY KEY AUTO_INCREMENT,
    Title VARCHAR(150) NOT NULL,
    AuthorID INT,
    Price DECIMAL(6,2),
    PublishedYear INT,
    FOREIGN KEY (AuthorID) REFERENCES Authors(AuthorID)
);

-- Table: Customers
CREATE TABLE Customers (
    CustomerID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100) NOT NULL,
    Email VARCHAR(100) UNIQUE NOT NULL
);

-- Table: Orders
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY AUTO_INCREMENT,
    CustomerID INT,
    OrderDate DATE,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);

-- Table: OrderDetails
CREATE TABLE OrderDetails (
    OrderDetailID INT PRIMARY KEY AUTO_INCREMENT,
    OrderID INT,
    BookID INT,
    Quantity INT,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    FOREIGN KEY (BookID) REFERENCES Books(BookID)
);

-- Insert sample authors
INSERT INTO Authors (Name, Country) VALUES
('J.K. Rowling', 'UK'),
('George R.R. Martin', 'USA'),
('Chetan Bhagat', 'India');

-- Insert sample books
INSERT INTO Books (Title, AuthorID, Price, PublishedYear) VALUES
('Harry Potter and the Sorcerer''s Stone', 1, 499.99, 1997),
('A Game of Thrones', 2, 699.50, 1996),
('Five Point Someone', 3, 299.99, 2004);

-- Insert sample customers
INSERT INTO Customers (Name, Email) VALUES
('Rahul Sharma', 'rahul@example.com'),
('Sneha Verma', 'sneha@example.com');

-- Insert sample orders
INSERT INTO Orders (CustomerID, OrderDate) VALUES
(1, '2025-08-10'),
(2, '2025-08-11');

-- Insert sample order details
INSERT INTO OrderDetails (OrderID, BookID, Quantity) VALUES
(1, 1, 2),
(1, 3, 1),
(2, 2, 1);

-- Example Queries

-- 1. List all books with author names
SELECT b.Title, a.Name AS Author, b.Price
FROM Books b
JOIN Authors a ON b.AuthorID = a.AuthorID;

-- 2. Find total sales per book
SELECT b.Title, SUM(od.Quantity) AS TotalSold
FROM OrderDetails od
JOIN Books b ON od.BookID = b.BookID
GROUP BY b.Title;

-- 3. Get all orders with customer names
SELECT o.OrderID, c.Name AS Customer, o.OrderDate
FROM Orders o
JOIN Customers c ON o.CustomerID = c.CustomerID;
