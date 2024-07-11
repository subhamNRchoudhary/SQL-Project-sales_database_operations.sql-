# SQL-Project-sales_database_operations.sql



### SQL Script File (sales_database_operations.sql)

```sql
-- SQL script to create and operate on SalesData table

-- Create database
CREATE DATABASE sales_database;
USE sales_database;

-- Create SalesData table
CREATE TABLE SalesData (
    CustomerID INT,
    Age INT,
    Gender VARCHAR(10),
    Product VARCHAR(50),
    Category VARCHAR(50),
    SalesAmount DECIMAL(10, 2),
    Region VARCHAR(50),
    Feedback INT
);

-- Insert data into SalesData table
INSERT INTO SalesData (CustomerID, Age, Gender, Product, Category, SalesAmount, Region, Feedback)
VALUES
(36, 16, 'Male', 'Shoes', 'Apparel', 10, 'West', 1),
-- Add the rest of the data...

-- SQL operations
-- 1. Selecting All Data
SELECT * FROM SalesData;

-- 2. Selecting Specific Columns
SELECT CustomerID, Age, Gender, Product FROM SalesData;

-- 3. Filtering Data with WHERE Clause
SELECT * FROM SalesData WHERE Gender = 'Female';

-- 4. Using Aggregate Functions (SUM)
SELECT SUM(SalesAmount) AS TotalSales FROM SalesData;

-- 5. Using Aggregate Functions (AVG)
SELECT AVG(SalesAmount) AS AverageSales FROM SalesData;

-- 6. Grouping Data (GROUP BY)
SELECT Region, SUM(SalesAmount) AS TotalSales FROM SalesData GROUP BY Region;

-- 7. Filtering Grouped Data (HAVING)
SELECT Region, SUM(SalesAmount) AS TotalSales FROM SalesData GROUP BY Region HAVING SUM(SalesAmount) > 1000;

-- 8. Counting Records
SELECT COUNT(*) AS TotalRecords FROM SalesData;

-- 9. Ordering Data (ORDER BY)
SELECT * FROM SalesData ORDER BY SalesAmount DESC;

-- 10. Combining Conditions (AND, OR)
SELECT * FROM SalesData WHERE Gender = 'Female' AND Age > 30;

-- 11. Using IN Clause
SELECT * FROM SalesData WHERE Region IN ('West', 'East');

-- 12. Using BETWEEN Clause
SELECT * FROM SalesData WHERE SalesAmount BETWEEN 100 AND 200;

-- 13. Using LIKE for Pattern Matching
SELECT * FROM SalesData WHERE Product LIKE 'B%';

-- 14. Using DISTINCT to Remove Duplicates
SELECT DISTINCT Product FROM SalesData;

-- 15. Updating Records
UPDATE SalesData SET Feedback = 5 WHERE CustomerID = 36;

-- 16. Deleting Records
DELETE FROM SalesData WHERE CustomerID = 36;

-- 17. Joining Tables (Inner Join)
CREATE TABLE CustomerDetails (
    CustomerID INT,
    CustomerName VARCHAR(50)
);

INSERT INTO CustomerDetails (CustomerID, CustomerName)
VALUES
(36, 'John Doe'),
(122, 'Jane Smith');

SELECT SalesData.CustomerID, SalesData.Product, CustomerDetails.CustomerName
FROM SalesData
INNER JOIN CustomerDetails ON SalesData.CustomerID = CustomerDetails.CustomerID;

-- 18. Using Subqueries
SELECT * FROM SalesData WHERE SalesAmount > (SELECT AVG(SalesAmount) FROM SalesData);

-- 19. Using CASE Statement
SELECT CustomerID, 
       SalesAmount,
       CASE 
           WHEN SalesAmount < 50 THEN 'Low'
           WHEN SalesAmount BETWEEN 50 AND 100 THEN 'Medium'
           ELSE 'High'
       END AS SalesCategory
FROM SalesData;

-- 20. Creating Views
CREATE VIEW HighValueSales AS
SELECT * FROM SalesData WHERE SalesAmount > 150;

SELECT * FROM HighValueSales;
```

