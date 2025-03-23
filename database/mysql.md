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

