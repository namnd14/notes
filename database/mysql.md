MySQL:
- free
- open source
- ideal for both small and large applications
- cross-platform
- developed, distributed, and supported by Oracle Corporation

keywords are NOT case-sensitive but keep in mind that always use upper case
use semicolon at the end of each query  

structure: schema (database) => tables, views, stored procedures, functions, triggers, etc.

SELECT  
SELECT DISTINCT

WHERE => filter records  
operators in WHERE clause: =, <>, !=, >, <, >=, <=, BETWEEN, LIKE, IN, IS NULL, IS NOT NULL

ORDER BY + column name + ASC/DESC

INSERT INTO + table name + (column1, column2, ...) + VALUES (value1, value2, ...)

NULL value => check by IS NULL, IS NOT NULL

UPDATE + table name + SET column1 = value1, column2 = value2, ... + WHERE condition

DELETE FROM + table name + WHERE condition

LIMIT + number => limit the number of records  
example: SELECT * FROM people LIMIT 3;

LIMIT OFFSET + number => skip the number of records  
SELECT * FROM people LIMIT 3 OFFSET 4;

MIN, MAX, AVG, SUM, COUNT + column name => aggregate functions

ex: SELECT COUNT(*) FROM people;

SELECT AVG(id) FROM people WHERE id > 5;

IN => filter records based on multiple values  
SELECT * FROM people WHERE id IN (1, 4, 6);  
SELECT * FROM people WHERE id IN (SELECT id FROM people WHERE id > 9);

BETWEEN => filter records based on a range of values, use for numbers, text, and dates  
SELECT * FROM people WHERE id BETWEEN 3 AND 7;  
SELECT * FROM people WHERE date_of_birth BETWEEN '1990-05-15' AND '2000-07-19';

The LIKE operator is used in a WHERE clause to search for a specified pattern in a column  
There are two wildcards often used in conjunction with the LIKE operator:  
- The percent sign (%) represents zero, one, or multiple characters
- The underscore (_) represents a single character  
Example:
- SELECT * FROM people WHERE name LIKE 'a%'; => names starting with 'a'
- SELECT * FROM people WHERE name LIKE '%a'; => names ending with 'a'
- SELECT * FROM people WHERE name LIKE '%or%'; => names containing 'or'
- SELECT * FROM people WHERE name LIKE '_r%'; => names with second letter 'r'
- SELECT * FROM people WHERE name LIKE 'a_%_%'; => names starting with 'a' and at least 3 characters long
- SELECT * FROM people WHERE name LIKE 'a%o'; => names starting with 'a' and ending with 'o'

A wildcard character is used to substitute any other character(s) in a string.

AS => alias  
We can alias column names and table names in SQL by using the AS keyword.

A JOIN clause is used to combine rows from two or more tables, based on a related column between them.  
Types of JOIN:  
- INNER JOIN (default) => returns records that have matching values in both tables
- LEFT JOIN (or LEFT OUTER JOIN) => returns all records from the left table, and the matched records from the right table
- RIGHT JOIN (or RIGHT OUTER JOIN) => returns all records from the right table, and the matched records from the left table
- FULL JOIN (or FULL OUTER JOIN) => returns all records when there is a match in either left (table1) or right (table2) table records
- CROSS JOIN => returns the Cartesian product of the two tables  
Example:
- SELECT column_name(s) FROM table1 INNER JOIN table2 ON table1.column_name = table2.column_name;
- SELECT column_name(s) FROM table1 LEFT JOIN table2 ON table1.column_name = table2.column_name;
- SELECT column_name(s) FROM table1 RIGHT JOIN table2 ON table1.column_name = table2.column_name;
- SELECT column_name(s) FROM table1 FULL JOIN table2 ON table1.column_name = table2.column_name;
- SELECT column_name(s) FROM table1 CROSS JOIN table2;  
Note: If add a WHERE clause in the CROSS JOIN, it will work like an INNER JOIN.  

Self JOIN => a regular join, but the table is joined with itself.  
SELECT column_name(s) FROM table1 T1, table1 T2 WHERE condition;  
The T1 and T2 are different table aliases for the same table.  

UNION => used to combine the result-set of two or more SELECT statements.  
- Each SELECT statement within UNION must have the same number of columns
- The columns must also have similar data types
- The columns in each SELECT statement must also be in the same order  
SELECT column_name(s) FROM table1 UNION SELECT column_name(s) FROM table2;  
The UNION operator selects only distinct values by default.  
UNION ALL => return all rows from the combined result sets of two or more SELECT statements, including duplicate rows.  
SELECT column_name(s) FROM table1 UNION ALL SELECT column_name(s) FROM table2;  
