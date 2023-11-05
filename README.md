## MySQL Data types

#### Character Types:
1. ***CHAR***: Represents a fixed-length string. The length of the stored string is specified in parentheses, e.g., CHAR(10), which indicates a string of ten characters. If a shorter string (e.g., 6 characters) is stored in this column, it is padded with spaces to reach the specified length (10 characters). CHAR can store up to 255 bytes.
2. ***VARCHAR***: Represents a variable-length string. The length of the stored string is also specified in parentheses, e.g., VARCHAR(10). Unlike CHAR, VARCHAR only uses as much space as needed, so a string of 6 characters will occupy 6 characters plus an additional byte to store the length of the string. VARCHAR can store up to 65,535 bytes. Starting from MySQL 5.6, CHAR and VARCHAR types default to using the UTF-8 encoding, allowing variable-length storage based on character encoding.

***Additional Variable-Length Text Types:***

3. ***TINYTEXT***: Stores text with a maximum length of 255 bytes.
4. ***TEXT***: Stores text with a maximum length of 65 KB.
5. ***MEDIUMTEXT***: Stores text with a maximum length of 16 MB.
6. ***LONGTEXT***: Stores text with a maximum length of 4 GB.

#### Numeric Types:
1. ***TINYINT***: Represents integers from -128 to 127 and occupies 1 byte.
2. ***BOOL (or BOOLEAN)***: It is essentially an alias for TINYINT(1) and can store values 0 and 1. It can also accept TRUE (equivalent to 1) and FALSE (equivalent to 0) as values.
3. ***TINYINT UNSIGNED***: Represents integers from 0 to 255 and occupies 1 byte.
4. ***SMALLINT***: Represents integers from -32,768 to 32,767 and occupies 2 bytes.
5. ***SMALLINT UNSIGNED***: Represents integers from 0 to 65,535 and occupies 2 bytes.
6. ***MEDIUMINT***: Represents integers from -8,388,608 to 8,388,607 and occupies 3 bytes.
7. ***MEDIUMINT UNSIGNED***: Represents integers from 0 to 16,777,215 and occupies 3 bytes.
8. ***INT***: Represents integers from -2,147,483,648 to 2,147,483,647 and occupies 4 bytes.
9. ***INT UNSIGNED***: Represents integers from 0 to 4,294,967,295 and occupies 4 bytes.
10. ***BIGINT***: Represents integers from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 and occupies 8 bytes.
11. ***BIGINT UNSIGNED***: Represents integers from 0 to 18,446,744,073,709,551,615 and occupies 8 bytes.
12. ***DECIMAL***: Stores numbers with fixed precision. It accepts two parameters, precision and scale, as DECIMAL(precision, scale). Precision represents the maximum number of digits, and scale represents the maximum number of digits after the decimal point. The data size in bytes for DECIMAL depends on the stored value.
13. ***FLOAT***: Stores single-precision floating-point numbers with optional precision and scale specified as FLOAT(M,D), where M is the total number of digits, and D is the number of digits after the decimal point.
14. ***DOUBLE***: Stores double-precision floating-point numbers with optional precision and scale specified as DOUBLE(M,D), where M is the total number of digits, and D is the number of digits after the decimal point.

#### Date and Time Types:
1. ***DATE***: Stores dates in the range from January 1, 1000, to December 31, 9999. It uses the "yyyy-mm-dd" format by default and occupies 3 bytes.
2. ***TIME***: Stores time values in the range from -838:59:59 to 838:59:59. It uses the "hh:mm:ss" format by default and occupies 3 bytes.
3. ***DATETIME***: Combines date and time values in the range from January 1, 1000, to December 31, 9999. It uses the "yyyy-mm-dd hh:mm:ss" format by default and occupies 8 bytes.
4. ***TIMESTAMP***: Stores date and time values in the range from "1970-01-01 00:00:01" UTC to "2038-01-19 03:14:07" UTC. It occupies 4 bytes.
5. ***YEAR***: Stores a 4-digit year value in the range from 1901 to 2155 and occupies 1 byte.

#### Composite Types:
1. ***ENUM***: Stores a single value from a list of allowed values and occupies 1-2 bytes.
2. ***SET***: Stores multiple values (up to 64 values) from a list of allowed values and occupies 1-8 bytes.

#### Binary Types:
1. ***TINYBLOB***: Stores binary data as a string with a maximum length of 255 bytes.
2. ***BLOB***: Stores binary data as a string with a maximum length of 65 KB.
3. ***MEDIUMBLOB***: Stores binary data as a string with a maximum length of 16 MB.
4. ***LONGBLOB***: Stores binary data as a string with a maximum length of 4 GB.

## Base Commands 

### SELECT
```
SELECT column_name 
FROM table_name;
```

***SELECT statements are used to fetch data from a database. Every query will begin with SELECT.***

### SELECT DISTINCT
```
SELECT DISTINCT column_name
FROM table_name;
```

***SELECT DISTINCT specifies that the statement is going to be a query that returns unique values in the specified column(s).***

### WHERE
```
SELECT column_name(s)
FROM table_name
WHERE column_name operator value;
```

***WHERE is a clause that indicates you want to filter the result set to include only rows where the following condition is true.***

### CREATE TABLE
```
CREATE TABLE table_name (
  column_1 datatype, 
  column_2 datatype, 
  column_3 datatype
);
```

***CREATE TABLE creates a new table in the database. It allows you to specify the name of the table and the name of each column in the table.***

### ALTER TABLE
```
ALTER TABLE table_name 
ADD column_name datatype;
```

***ALTER TABLE lets you add columns to a table in a database.***

### UPDATE
```
UPDATE table_name
SET some_column = some_value
WHERE some_column = some_value;
```

***UPDATE statements allow you to edit rows in a table.***

### INSERT
```
INSERT INTO table_name (column_1, column_2, column_3) 
VALUES (value_1, 'value_2', value_3);
```

***INSERT statements are used to add a new row to a table.***

### DELETE
```
DELETE FROM table_name
WHERE some_column = some_value;
```

***DELETE statements are used to remove rows from a table.***

### AND
```
SELECT column_name(s)
FROM table_name
WHERE column_1 = value_1
  AND column_2 = value_2;
```

***AND is an operator that combines two conditions. Both conditions must be true for the row to be included in the result set.***

### AS
```
SELECT column_name AS 'Alias'
FROM table_name;
```

***AS is a keyword in SQL that allows you to rename a column or table using an alias.***

### AVG()
```
SELECT AVG(column_name)
FROM table_name;
```

***AVG() is an aggregate function that returns the average value for a numeric column.***

### BETWEEN
```
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value_1 AND value_2;
```

***The BETWEEN operator is used to filter the result set within a certain range. The values can be numbers, text or dates.***

### CASE
```
SELECT column_name,
  CASE
    WHEN condition THEN 'Result_1'
    WHEN condition THEN 'Result_2'
    ELSE 'Result_3'
  END
FROM table_name;
```

***CASE statements are used to create different outputs (usually in the SELECT statement). It is SQL’s way of handling if-then logic.***

### COUNT()
```
SELECT COUNT(column_name)
FROM table_name;
```

***COUNT() is a function that takes the name of a column as an argument and counts the number of rows where the column is not NULL.***

### GROUP BY
```
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name;
```

***GROUP BY is a clause in SQL that is only used with aggregate functions. It is used in collaboration with the SELECT statement to arrange identical data into groups.***

### HAVING
```
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name
HAVING COUNT(*) > value;
```

### Foreign key
```
CREATE TABLE Vendors (
    VendorID INT PRIMARY KEY,
    VendorName VARCHAR(255)
);

-- Create the 'Products' table with a foreign key
CREATE TABLE Products (
    ProductID INT PRIMARY KEY,
    ProductName VARCHAR(255),
    VendorID INT, -- This is the foreign key column
    FOREIGN KEY (VendorID) REFERENCES Vendors(VendorID)
);
```

***HAVING was added to SQL because the WHERE keyword could not be used with aggregate functions.***

### INNER JOIN
```
SELECT column_name(s)
FROM table_1
JOIN table_2
  ON table_1.column_name = table_2.column_name;
```

***An inner join will combine rows from different tables if the join condition is true.***

### OUTER JOIN
```
SELECT column_name(s)
FROM table_1
LEFT JOIN table_2
  ON table_1.column_name = table_2.column_name;
```

***An outer join will combine rows from different tables even if the join condition is not met. Every row in the left table is returned in the result set, and if the join condition is not met, then NULL values are used to fill in the columns from the right table.***

### LEFT JOIN (or LEFT OUTER JOIN)
```
SELECT column_name(s)
FROM table_1
LEFT JOIN table_2
ON table_1.column_name = table_2.column_name;
```

***Returns all records from the left table, and the matched records from the right table***

### RIGHT JOIN (or RIGHT OUTER JOIN)
```
SELECT column_name(s)
FROM table_1
RIGHT JOIN table_2
ON table_1.column_name = table_2.column_name;
```

***Returns all records from the right table, and the matched records from the left table***

### FULL JOIN (or FULL OUTER JOIN)
```
SELECT column_name(s)
FROM table_1
FULL JOIN table_2
ON table_1.column_name = table_2.column_name;
```

***Returns all records when there is a match in either left or right table***

### IS NULL / IS NOT NULL
```
SELECT column_name(s)
FROM table_name
WHERE column_name IS NULL;
```

***IS NULL and IS NOT NULL are operators used with the WHERE clause to test for empty values.***

### LIKE
```
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE pattern;
```

***LIKE is a special operator used with the WHERE clause to search for a specific pattern in a column.***

### LIMIT
```
SELECT column_name(s)
FROM table_name
LIMIT number;
```

***LIMIT is a clause that lets you specify the maximum number of rows the result set will have.***

### MAX()
```
SELECT MAX(column_name)
FROM table_name;
```

***MAX() is a function that takes the name of a column as an argument and returns the largest value in that column.***

### MIN()
```
SELECT MIN(column_name)
FROM table_name;
```

***MIN() is a function that takes the name of a column as an argument and returns the smallest value in that column.***

### OR
```
SELECT column_name
FROM table_name
WHERE column_name = value_1
   OR column_name = value_2;
```

***OR is an operator that filters the result set to only include rows where either condition is true.***

### ORDER BY
```
SELECT column_name
FROM table_name
ORDER BY column_name ASC | DESC;
```

***ORDER BY is a clause that indicates you want to sort the result set by a particular column either alphabetically or numerically.***

### ROUND()
```
SELECT ROUND(column_name, integer)
FROM table_name;
```

***ROUND() is a function that takes a column name and an integer as arguments. It rounds the values in the column to the number of decimal places specified by the integer.***

### SUM
```
SELECT SUM(column_name)
FROM table_name;
```

***SUM() is a function that takes the name of a column as an argument and returns the sum of all the values in that column.***

### WITH
```
WITH temporary_name AS (
   SELECT *
   FROM table_name)
SELECT *
FROM temporary_name
WHERE column_name operator value;
```

***WITH clause lets you store the result of a query in a temporary table using an alias. You can also define multiple temporary tables using a comma and with one instance of the WITH keyword.***

## Types of relations

### One-to-one (one person has only one passport)

**Person Table:**

| person_id | first_name | last_name | date_of_birth |
|----------|------------|-----------|---------------|
| 1        | John       | Doe       | 1980-05-15    |
| 2        | Jane       | Smith     | 1990-03-20    |

**Passport Table:**

| passport_id | passport_number | expiration_date | person_id |
|-------------|-----------------|-----------------|----------|
| 101         | P123456789     | 2025-10-15      | 1        |
| 102         | P987654321     | 2024-12-31      | 2        |


### One-to-many relation (one city has many customers)

***Create cities table***
```
CREATE TABLE cities ( id INT AUTO_INCREMENT PRIMARY KEY, city_name VARCHAR(255) );
INSERT INTO cities (city_name) VALUES ('Berlin'), ('Lviw'), ('Zagreb'), ('New York'), ('Los Angeles'), ('Warsaw');
```
| id | city_name     |
|----|-------------- |
| 1  | Berlin        |
| 2  | Lviv          |
| 3  | Zagreb        |
| 4  | New York      |
| 5  | Los Angeles   |
| 6  | Warsaw        |

***Create customers table***
```
REATE TABLE customers (id INT AUTO_INCREMENT PRIMARY KEY, customer_name VARCHAR(255), city_id INT, FOREIGN KEY (city_id) REFERENCES cities(id));
INSERT INTO customers(customer_name, city_id) VALUES ('Jewerly', 4), ('Bakery', 1), ('Cafe', 1), ('Restaurant', 3);
```
| id | customer_name | city_id |
|----|--------------- | ------- |
| 1  | Jewelry       | 4       |
| 2  | Bakery        | 1       |
| 3  | Cafe          | 1       |
| 4  | Restaurant    | 3       |

***Select Data***
```
SELECT * FROM `customers` INNER JOIN cities ON customers.city_id = cities.id;
SELECT * FROM `customers` LEFT JOIN cities ON customers.city_id = cities.id;
SELECT * FROM `customers` RIGHT JOIN cities ON customers.city_id = cities.id;
```
The first query (using INNER JOIN) returned only rows where cities and customers had a pair. Since we had 4 rows for customers and all 4 had related city defined, the final result also has 4 rows.
| id | customer_name | city_id | id | city_name   |
|----|---------------|---------|----|------------ |
| 2  | Bakery        | 1       | 1  | Berlin      |
| 3  | Cafe          | 1       | 1  | Berlin      |
| 4  | Restaurant    | 3       | 3  | Zagreb      |
| 1  | Jewelry       | 4       | 4  | New York    |


The second query (customer LEFT JOIN city) returned the same result as the first one. That happened because all customers had related city defined. In case some customers wouldn’t have city_id defined (NULL), these customers would be included in this result too.
| id | customer_name | city_id | id | city_name   |
|----|---------------|---------|----|------------ |
| 1  | Jewelry       | 4       | 4  | New York    |
| 2  | Bakery        | 1       | 1  | Berlin      |
| 3  | Cafe          | 1       | 1  | Berlin      |
| 4  | Restaurant    | 3       | 3  | Zagreb      |


The last query (city LEFT JOIN customer) returns more rows than the previous two queries. It returns all 4 rows they’ve returned, but also returns 3 more rows for cities where we have no customers. And that’s completely ok because if we wrote query this way, we obviously wanted to point to that fact.
| id | customer_name | city_id | id | city_name   |
|----|---------------|---------|----|------------ |
| 3  | Cafe          | 1       | 1  | Berlin      |
| 2  | Bakery        | 1       | 1  | Berlin      |
| NULL | NULL        | NULL    | 2  | Belgrade    |
| 4  | Restaurant    | 3       | 3  | Zagreb      |
| 1  | Jewelry       | 4       | 4  | New York    |
| NULL | NULL        | NULL    | 5  | Los Angeles |
| NULL | NULL        | NULL    | 6  | Warsaw      |


### Many-to-many (One student can enroll in multiple courses, and one course can be attended by multiple students)
***students***
```
CREATE TABLE students ( student_id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255) NOT NULL );
INSERT INTO students (name) VALUES ('Alice'), ('Bob'), ('Carol'), ('David');
```
| student_id | name    |
|---------|-----------|
| 1       | Alice   |
| 2       | Bob     |
| 3       | Carol   |
| 4       | David   |

***courses***
```
CREATE TABLE courses ( course_id INT AUTO_INCREMENT PRIMARY KEY, course_name VARCHAR(255) NOT NULL );
INSERT INTO courses (course_name) VALUES ('Math'), ('Science'), ('History');
```
| course_id | course_name      |
|----------|------------------|
| 101      | Math            |
| 102      | Science         |
| 103      | History         |

***student_courses***
```
CREATE TABLE student_courses
(id INT PRIMARY KEY AUTO_INCREMENT,
student_id INT,
course_id INT,
FOREIGN KEY (student_id) REFERENCES students(student_id),
FOREIGN KEY (course_id) REFERENCES courses(course_id) );
INSERT INTO student_courses (student_id, course_id) VALUES (1, 1), (1, 2), (2, 2), (3, 3);
```
| student_id  | course_id |
|-------------|-----------|
| 1           | 101       |
| 1           | 102       |
| 2           | 102       |
| 3           | 103       |

***Get data***
#### All students with courses
```
SELECT students.student_id, students.name, student_courses.course_id FROM students
INNER JOIN student_courses
ON students.student_id = student_courses.student_id;
```
| student_id | name    | course_id |
|----------- |---------|----------- |
| 1          | Alice   | 101       |
| 1          | Alice   | 102       |
| 2          | Bob     | 102       |
| 3          | Carol   | 103       |

#### All students without courses
```
SELECT students.student_id, students.name, student_courses.course_id FROM students
LEFT JOIN student_courses
ON students.student_id = student_courses.student_id
WHERE student_courses.course_id IS NULL;
```
| student_id | name    | course_id |
|----------- |---------|----------- |
| 4          | David   | NULL      |
