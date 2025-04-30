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

---

## 🛠 Tools Used

- **SQL Server / Azure Data Studio**
- **Git & GitHub**

---

If you'd like to get in touch, you can reach me at: [roja.au1994@gmail.com](mailto:roja.au1994@gmail.com)


