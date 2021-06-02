---
title: Strategy in SQL injection
date: 2020-09-08 03:47:03
updated:
tags:
 - CTF
cover: /img/SQL-injection.jpg
---
### Union Operator

<https://www.w3schools.com/sql/sql_union.asp>

### use ORDER BY keyword to guess the number of column in O(logN)

```text
DB_NAME: Customers
CustomerID 	CustomerName 	          Country
1           Alfreds Futterkiste       Germany
2 	        Ana Trujillo Emparedados  Mexico
3  	        Antonio Moreno Taquería   Mexico
4           Around the Horn 	      UK
5 	        Berglunds snabbköp 	      Sweden

```

For example, `SELECT * FROM Customers ORDER BY Country` will sort customers column in Country order.

Fortunately(or unfortunately), you can use numbers of the column to indicate the column you want, which means you can do exactly the same thing using `SELECT * FROM Customers ORDER BY 3`.

So, if you apply binary search idea here, you can guess the column number very quickly:

 - `SELECT * FROM Customers ORDER BY 3` will not return an error since the number of columns is less than or equal of 3
 - `SELECT * FROM Customers ORDER BY 4` will return an error since the number of columns is more than 3
 - `SELECT * FROM Customers ORDER BY 2` will not return an error since the number of columns is less than or equal of 2

After a few query, we can assert the column number is *3*. You can then use this number in _UNION_ command

### get information about current SQL database

`@@version` shows the SQL version. For example: `SELECT * FROM Customers UNION SELECT 1,2,@@version`
`current_user()` shows the current user. For example: `SELECT * FROM Customers UNION SELECT 1,2,current_user()`
`database()` shows the current database. For example: `SELECT * FROM Customers UNION SELECT 1,2,database()`

Using meta information, you can access more information. 
<https://www.mssqltips.com/sqlservertutorial/179/sql-server-informationschema-views-tutorial/>

`SELECT table_name FROM information_schema.tables`
you can union this when doing SQL injection.

you can use `CONCAT` to get more information if you are limit by the column number in UNION.
`SELECT * FROM Customers UNION SELECT 1,2,CONCAT(3,4),5`