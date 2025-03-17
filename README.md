# SQL Basic Commands

This file contains SQL commands for creating a database, managing tables, inserting, updating, deleting data, ordering results, using joins, and performing aggregations.

```sql
-- Creating a database
CREATE DATABASE MyDatabase;

-- Selecting the database
USE MyDatabase;

-- Creating a table named "Clients"
CREATE TABLE Clients (
    ID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(100),
    Email VARCHAR(100) UNIQUE,
    Age INT
);

-- Creating another table named "Orders"
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY AUTO_INCREMENT,
    ClientID INT,
    OrderDate DATE,
    Amount DECIMAL(10, 2),
    FOREIGN KEY (ClientID) REFERENCES Clients(ID)
);

-- Inserting data into the Clients table
INSERT INTO Clients (Name, Email, Age) 
VALUES ('Maria Silva', 'maria@email.com', 30);

INSERT INTO Clients (Name, Email, Age) 
VALUES ('João Souza', 'joao@email.com', 25);

-- Inserting data into the Orders table
INSERT INTO Orders (ClientID, OrderDate, Amount) 
VALUES (1, '2025-03-17', 250.00);

-- Viewing all data from the Clients table
SELECT * FROM Clients;

-- Filtering data by condition
SELECT * FROM Clients WHERE Age > 25;
SELECT * FROM Clients WHERE Name = 'Maria Silva';

-- Updating data in the table
UPDATE Clients  
SET Age = 32  
WHERE ID = 1;  

-- Viewing updated data
SELECT * FROM Clients;

-- Deleting a record
DELETE FROM Clients WHERE ID = 1;

-- Viewing the table after deletion
SELECT * FROM Clients;

-- Ordering data by Age (Ascending)
SELECT * FROM Clients ORDER BY Age;

-- Ordering data by Age (Descending)
SELECT * FROM Clients ORDER BY Age DESC;

-- Limiting the number of results
SELECT * FROM Clients ORDER BY Age DESC LIMIT 2;

-- Joining Clients and Orders tables
SELECT Clients.Name, Orders.OrderDate, Orders.Amount
FROM Orders
INNER JOIN Clients ON Orders.ClientID = Clients.ID;

-- LEFT JOIN (All clients, even those without orders)
SELECT Clients.Name, Orders.OrderDate, Orders.Amount
FROM Clients
LEFT JOIN Orders ON Clients.ID = Orders.ClientID;

-- RIGHT JOIN (All orders, even those without clients)
SELECT Clients.Name, Orders.OrderDate, Orders.Amount
FROM Clients
RIGHT JOIN Orders ON Clients.ID = Orders.ClientID;

-- Aggregation functions
SELECT COUNT(*) FROM Clients;  -- Total number of clients
SELECT SUM(Amount) FROM Orders;  -- Total order amount
SELECT AVG(Amount) FROM Orders;  -- Average order amount
SELECT MAX(Amount) FROM Orders;  -- Highest order amount
SELECT MIN(Amount) FROM Orders;  -- Lowest order amount

-- Grouping and aggregating data
SELECT Clients.Name, SUM(Orders.Amount) AS TotalSpent
FROM Orders
INNER JOIN Clients ON Orders.ClientID = Clients.ID
GROUP BY Clients.Name;
