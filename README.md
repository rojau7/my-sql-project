# my-sql-project

# SQL String Function Assignments

This project demonstrates the use of SQL string functions like `LEFT()`, `SUBSTRING()`, `CHARINDEX()`, and `RIGHT()` on sample tables. It includes two assignments with different types of data extraction.

---

## 📘 Assignment 1 – Extracting Name and ID from Employee Data

From the `Employee_raw` table, the query extracts:
- **FIRSTNAME** – First word
- **MIDDLENAME** – Second word
- **LASTNAME** – Third word
- **IDWITHBRACKET** – ID including brackets `()`
- **IDWITHOUTBRACKET** – ID inside the brackets only

### SQL Query:

```sql
SELECT *,  
  LEFT(DATA1, CHARINDEX(' ', DATA1) - 1) AS FIRSTNAME,  
  SUBSTRING(DATA1, CHARINDEX(' ', DATA1) + 1, CHARINDEX(' ', DATA1, CHARINDEX(' ', DATA1) + 1) - CHARINDEX(' ', DATA1) - 1) AS MIDDLENAME,  
  SUBSTRING(DATA1, CHARINDEX(' ', DATA1, CHARINDEX(' ', DATA1) + 1) + 1, CHARINDEX('(', DATA1) - CHARINDEX(' ', DATA1, CHARINDEX(' ', DATA1) + 1) - 1) AS LASTNAME,  
  SUBSTRING(DATA1, CHARINDEX('(', DATA1), CHARINDEX(')', DATA1) - CHARINDEX('(', DATA1) - 1) AS IDWITHBRACKET,  
  SUBSTRING(DATA1, CHARINDEX('(', DATA1) + 1, CHARINDEX(')', DATA1) - CHARINDEX('(', DATA1) - 1) AS IDWITHOUTBRACKET  
FROM Employee_raw;

## 📘 Assignment 2 – Splitting Dot-Separated Data

From the `country_data` table, the query extracts parts of a dot-separated string:
- **FirstDot** – Text before the 1st dot
- **SecondDot** – Text between 1st and 2nd dot
- **ThirdDot** – Text between 2nd and 3rd dot
- **FourthDot** – Everything after the 3rd dot

### SQL Query:

```sql
SELECT *,  
  LEFT(dataC, CHARINDEX('.', dataC) - 1) AS FirstDot,  
  SUBSTRING(dataC, CHARINDEX('.', dataC) + 1, CHARINDEX('.', dataC, CHARINDEX('.', dataC) + 1) - CHARINDEX('.', dataC) - 1) AS SecondDot,  
  SUBSTRING(dataC, CHARINDEX('.', dataC, CHARINDEX('.', dataC) + 1) + 1, CHARINDEX('.', dataC, CHARINDEX('.', dataC, CHARINDEX('.', dataC) + 1) + 1) - CHARINDEX('.', dataC, CHARINDEX('.', dataC) + 1) - 1) AS ThirdDot,  
  RIGHT(dataC, LEN(dataC) - CHARINDEX('.', dataC, CHARINDEX('.', dataC, CHARINDEX('.', dataC) + 1) + 1)) AS FourthDot  
FROM country_data;

------------------------------------------------------------------------------------------------------

## 🔄 SQL JOIN Assignment – INNER, LEFT, RIGHT, FULL OUTER

This assignment demonstrates the use of **SQL JOINs** – specifically `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, and `FULL OUTER JOIN` – using two tables: `EmployeeDetail` and `ProjectDetail`.

📄 **Uploaded File:**  
[`SQL_Assignment_Joins.pdf`](./SQL_Assignment_Joins.pdf)

---------------------------------------------------------------------------------------------------------

### 📋 Tables Involved

- **EmployeeDetail**
  - Columns: `EmployeeID`, `FirstName`, `LastName`, `Salary`, `Department`, `Gender`
- **ProjectDetail**
  - Columns: `ProjectDetailID`, `EmployeeDetailID`, `ProjectName`

---------------------------------------------------------------------------------------------------------

### 📌 Assignment Questions:

1. **INNER JOIN** – Get Employee Name and Project Name for employees who are assigned to projects.  
2. **LEFT JOIN** – Get all employees with their project names, even if no project is assigned.  
3. **RIGHT JOIN** – Get all project names, even if no matching employee exists.  
4. **FULL OUTER JOIN** – Get complete records of employees and projects, including unmatched ones.

---------------------------------------------------------------------------------------------------------

### 🔍 Sample Query (FULL OUTER JOIN):

```sql
SELECT 
  Empdetails.FirstName + ' ' + Empdetails.LastName AS EmployeeName,
  Projdetails.ProjectName
FROM 
  Empdetails
FULL OUTER JOIN 
  Projdetails
ON 
  Empdetails.EmployeeID = Projdetails.EmployeeDetailID
ORDER BY 
  Empdetails.FirstName;

-----------------------------------------------------------------------------------------------------------------

📘 SQL Assignment – Employee Tables
This repository contains an SQL assignment involving queries on two tables:

EmployeeDetails

EmployeeSalary

📄 Description
The assignment consists of 10 SQL questions that test knowledge of:

SELECT statements

WHERE clause

Aggregate functions (MIN, MAX, AVG)

DISTINCT

BETWEEN

UNION

🗃️ Files Included
SQL_Assignment.pdf: Contains all 10 assignment questions with answers.

EmpTable.csv: Sample data for the EmployeeDetails table.

SalaryTable.csv: Sample data for the EmployeeSalary table.

✅ Sample Questions Covered
Fetch employees under a specific manager.

Get distinct projects.

Count employees in a project.

Salary range filters.

Use of aggregate functions and conditional clauses.

## 🛠 Tools Used

- **SQL Server / Azure Data Studio**
- **Git & GitHub**

-----------------------------------------------------------------------------------------------------------------
If you'd like to get in touch, you can reach me at: [roja.au1994@gmail.com](mailto:roja.au1994@gmail.com)


