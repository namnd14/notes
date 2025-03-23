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

