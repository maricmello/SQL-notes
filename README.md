# SQL Basic Commands

This file contains SQL commands for creating a database, managing tables, inserting, updating, and deleting data.

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

-- Inserting data into the table
INSERT INTO Clients (Name, Email, Age) 
VALUES ('Maria Silva', 'maria@email.com', 30);

INSERT INTO Clients (Name, Email, Age) 
VALUES ('João Souza', 'joao@email.com', 25);

-- Viewing all data from the table
SELECT * FROM Clients;

-- Filtering data by condition
SELECT * FROM Clients WHERE Age > 25;
SELECT * FROM Clients WHERE Name = 'Maria Silva';

-- Updating data in the table
UPDATE Clients  
SET Age = 32  
WHERE ID = 1;  -- Replace 1 with the correct ID

-- Viewing updated data
SELECT * FROM Clients;

-- Deleting a record
DELETE FROM Clients WHERE ID = 1;

-- Viewing the table after deletion
SELECT * FROM Clients;
