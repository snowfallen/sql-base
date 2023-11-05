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
```sql
SELECT column_name 
FROM table_name;
```

***SELECT statements are used to fetch data from a database. Every query will begin with SELECT.***

### LIMIT
```sql
SELECT column_name(s)
FROM table_name
LIMIT number;
```

***LIMIT is a clause that lets you specify the maximum number of rows the result set will have.***

### SELECT DISTINCT
```sql
SELECT DISTINCT column_name
FROM table_name;
```

***SELECT DISTINCT specifies that the statement is going to be a query that returns unique values in the specified column(s).***

### AS
```sql
SELECT column_name AS 'Alias'
FROM table_name;
```

***AS is a keyword in SQL that allows you to rename a column or table using an alias.***

### WHERE
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator value;
```

***WHERE is a clause that indicates you want to filter the result set to include only rows where the following condition is true.***

### IN 
```sql
WHERE expression [NOT] IN (expression)
```
***The IN operator defines a set of values that columns should have. The expression within the parentheses after IN defines a set of values.***

### OR
```sql
SELECT column_name
FROM table_name
WHERE column_name = value_1
   OR column_name = value_2;
```

***OR is an operator that filters the result set to only include rows where either condition is true.***

### AND
```sql
SELECT column_name(s)
FROM table_name
WHERE column_1 = value_1
  AND column_2 = value_2;
```

***AND is an operator that combines two conditions. Both conditions must be true for the row to be included in the result set.***

### GROUP BY
```sql
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name;
```

***GROUP BY is a clause in SQL that is only used with aggregate functions. It is used in collaboration with the SELECT statement to arrange identical data into groups.***

### BETWEEN
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name BETWEEN value_1 AND value_2;
```

***The BETWEEN operator is used to filter the result set within a certain range. The values can be numbers, text or dates.***

### CREATE TABLE
```sql
CREATE TABLE table_name (
  column_1 datatype, 
  column_2 datatype, 
  column_3 datatype
);
```

***CREATE TABLE creates a new table in the database. It allows you to specify the name of the table and the name of each column in the table.***

### ALTER TABLE
```sql
ALTER TABLE table_name 
ADD column_name datatype;
```

***ALTER TABLE lets you add columns to a table in a database.***

### UPDATE
```sql
UPDATE table_name
SET some_column = some_value
WHERE some_column = some_value;
```

***UPDATE statements allow you to edit rows in a table.***

### INSERT
```sql
INSERT INTO table_name (column_1, column_2, column_3) 
VALUES (value_1, 'value_2', value_3);
```

***INSERT statements are used to add a new row to a table.***

### DELETE
```sql
DELETE FROM table_name
WHERE some_column = some_value;
```

***DELETE statements are used to remove rows from a table.***

### CASE
```sql
SELECT column_name,
  CASE
    WHEN condition THEN 'Result_1'
    WHEN condition THEN 'Result_2'
    ELSE 'Result_3'
  END
FROM table_name;
```

***CASE statements are used to create different outputs (usually in the SELECT statement). It is SQL’s way of handling if-then logic.***

### IS NULL / IS NOT NULL
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name IS NULL;
```

***IS NULL and IS NOT NULL are operators used with the WHERE clause to test for empty values.***

### LIKE
```sql
SELECT column_name(s)
FROM table_name
WHERE column_name LIKE pattern;
```

* `%`: Matches any substring, which can have any number of characters, and the substring may not contain any characters at all.
* `_`: Matches any single character.

***LIKE is a special operator used with the WHERE clause to search for a specific pattern in a column.***

### REGEXP
```sql
WHERE expression [NOT] REGEXP regular_expression
```

The regular expression can include the following special characters:
- `^`: Specifies the start of the string.
- `$`: Specifies the end of the string.
- `.`: Matches any single character.
- `[characters]`: Matches any single character from within the brackets.
- `[start_char-end_char]`: Matches any single character from the character range.
- `|`: Separates two string patterns, and the value must match one of these patterns.

***The REGEXP operator allows you to specify a regular expression that a column's value should match. In this regard, REGEXP provides a more sophisticated and complex way of filtering compared to the LIKE operator.***

### MAX()
```sql
SELECT MAX(column_name)
FROM table_name;
```

***MAX() is a function that takes the name of a column as an argument and returns the largest value in that column.***

### MIN()
```sql
SELECT MIN(column_name)
FROM table_name;
```

***MIN() is a function that takes the name of a column as an argument and returns the smallest value in that column.***

### AVG()
```sql
SELECT AVG(column_name)
FROM table_name;
```

***AVG() is an aggregate function that returns the average value for a numeric column.***

### COUNT()
```sql
SELECT COUNT(column_name)
FROM table_name;
```

***COUNT() is a function that takes the name of a column as an argument and counts the number of rows where the column is not NULL.***

### SUM
```sql
SELECT SUM(column_name)
FROM table_name;
```

***SUM() is a function that takes the name of a column as an argument and returns the sum of all the values in that column.***

### HAVING
```sql
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name
HAVING COUNT(*) > value;
```
***HAVING was added to SQL because the WHERE keyword could not be used with aggregate functions. The use of HAVING is largely analogous to using WHERE. However, while WHERE is used to filter rows, HAVING is used for filtering groups!!!***

### ORDER BY
```sql
SELECT column_name
FROM table_name
ORDER BY column_name ASC | DESC;
```

***ORDER BY is a clause that indicates you want to sort the result set by a particular column either alphabetically or numerically.***

### ROUND()
```sql
SELECT ROUND(column_name, integer)
FROM table_name;
```

***ROUND() is a function that takes a column name and an integer as arguments. It rounds the values in the column to the number of decimal places specified by the integer.***

### WITH
```sql
WITH temporary_name AS (
   SELECT *
   FROM table_name)
SELECT *
FROM temporary_name
WHERE column_name operator value;
```

***WITH clause lets you store the result of a query in a temporary table using an alias. You can also define multiple temporary tables using a comma and with one instance of the WITH keyword.***

### Foreign key
```sql
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
## Keys Types
1. **Primary Key**:
   - This is a unique key that identifies each record in a database table.
   - It is typically used to uniquely identify records in a table.

2. **Candidate Key**:
   - This is a set of columns in a table that can also be used as a primary key.
   - A candidate key has the same uniqueness property as the primary key.

3. **Super Key**:
   - This is a larger set of columns that can identify records but may not necessarily be unique.
   - It includes candidate keys and possibly other columns.

4. **Foreign Key**:
   - This is a column or set of columns that references the primary key (or another unique key) in another table.
   - It is used to create a relationship between tables.

5. **Composite Key**:
   - This is a key composed of two or more columns and determines the uniqueness of records only in the combination of these columns.

6. **Alternate Key**:
   - This is a key that could be used as a primary key if the primary key is absent.
   - It can be a candidate key or another unique key.

7. **Unique Key**:
   - This is a key that guarantees the uniqueness of values in a column but allows one value to be NULL.
  
Here are several database tables with examples of different types of keys:

1. **Table "Users"**:
   - Primary Key: "user_id"
   - Candidate Key: "username" (if it is a unique value for each user)
   - Foreign Key: "address_id" (references the user's address)

| user_id | username | address_id |
|--------|----------|------------|
| 1      | user1    | 101        |
| 2      | user2    | 102        |
| 3      | user3    | 103        |

2. **Table "Orders"**:
   - Primary Key: "order_id"
   - Foreign Key: "customer_id" (references the user)

| order_id | order_date | customer_id |
|---------|------------|-------------|
| 101     | 2023-01-15 | 1           |
| 102     | 2023-01-20 | 2           |
| 103     | 2023-01-25 | 1           |

3. **Table "Books"**:
   - Composite Key: "author" and "title" (if both together are unique)
   - Alternate Key: "ISBN" (can be used as a primary key if the ISBN is unique)

| author          | title                 | ISBN            |
|-----------------|-----------------------|-----------------|
| J.K. Rowling    | Harry Potter          | 9780545582889   |
| George Orwell   | 1984                  | 9780451524935   |
| J.K. Rowling    | The Chamber of Secrets | 9780439064866   |

## Joins 

### INNER JOIN
```sql
SELECT column_name(s)
FROM table_1
JOIN table_2
  ON table_1.column_name = table_2.column_name;
```

***An inner join will combine rows from different tables if the join condition is true.***

### OUTER JOIN
```sql
SELECT column_name(s)
FROM table_1
LEFT JOIN table_2
  ON table_1.column_name = table_2.column_name;
```

***An outer join will combine rows from different tables even if the join condition is not met. Every row in the left table is returned in the result set, and if the join condition is not met, then NULL values are used to fill in the columns from the right table.***

### LEFT JOIN (or LEFT OUTER JOIN)
```sql
SELECT column_name(s)
FROM table_1
LEFT JOIN table_2
ON table_1.column_name = table_2.column_name;
```

***Returns all records from the left table, and the matched records from the right table***

### RIGHT JOIN (or RIGHT OUTER JOIN)
```sql
SELECT column_name(s)
FROM table_1
RIGHT JOIN table_2
ON table_1.column_name = table_2.column_name;
```

***Returns all records from the right table, and the matched records from the left table***

### FULL JOIN (or FULL OUTER JOIN)
```sql
SELECT column_name(s)
FROM table_1
FULL JOIN table_2
ON table_1.column_name = table_2.column_name;
```

***Returns all records when there is a match in either left or right table***

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
```sql
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
```sql
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
```sql
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
```sql
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
```sql
CREATE TABLE courses ( course_id INT AUTO_INCREMENT PRIMARY KEY, course_name VARCHAR(255) NOT NULL );
INSERT INTO courses (course_name) VALUES ('Math'), ('Science'), ('History');
```
| course_id | course_name      |
|----------|------------------|
| 101      | Math            |
| 102      | Science         |
| 103      | History         |

***student_courses***
```sql
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
```sql
| student_id | name    | course_id |
|----------- |---------|----------- |
| 1          | Alice   | 101       |
| 1          | Alice   | 102       |
| 2          | Bob     | 102       |
| 3          | Carol   | 103       |

#### All students without courses
```sql
SELECT students.student_id, students.name, student_courses.course_id FROM students
LEFT JOIN student_courses
ON students.student_id = student_courses.student_id
WHERE student_courses.course_id IS NULL;
```
| student_id | name    | course_id |
|----------- |---------|----------- |
| 4          | David   | NULL      |

## Indexes types
1. **Primary Key Index**:
   - This is a unique index created for the primary key of a table.
   - It ensures fast access to specific records as they are unique.
   - It is automatically created for the primary key but can also be created manually.

```sql
CREATE TABLE Users (
    user_id INT PRIMARY KEY,
    username VARCHAR(50) UNIQUE,
    address_id INT,
    FOREIGN KEY (address_id) REFERENCES Addresses(address_id)
);
```

2. **Unique Index**:
   - This is an index that ensures the uniqueness of values in the indexed column.
   - Used when you want values in a specific column to be unique but not necessarily a primary key.
   - Can be created for any column, but the values in this column must be unique.

```sql
CREATE TABLE Products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100),
    product_code VARCHAR(20) UNIQUE,
    price DECIMAL(10, 2)
);
```

or

```sql
CREATE UNIQUE INDEX unique_index_name
ON table_name (column_name);
```

3. **Clustered Index**:
   - This is a special type of index that affects the physical storage of data in a table.
   - It determines the order of rows in the table based on the values of the indexed column.
   - A table can have only one clustered index, and it is automatically created for the primary key.

```sql
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    order_date DATE,
    customer_id INT,
    product_id INT,
    CLUSTERED INDEX (order_id)
);
```

or

```sql
CREATE CLUSTERED INDEX clustered_index_name
ON table_name (column_name);
```

4. **Non-Clustered Index**:
   - This is another type of index that does not affect the physical storage of data in the table.
   - Created to improve the performance of search and sort operations, but it doesn't change the order of data in the table.

```sql
CREATE TABLE Employees (
    employee_id INT PRIMARY KEY,
    employee_name VARCHAR(50),
    department_id INT,
    INDEX (department_id)
);
```

or

```sql
CREATE [UNIQUE] INDEX nonclustered_index_name
ON table_name (column_name);
```

5. **Full-Text Index**:
   - Used to optimize searching full-text data, such as in documents or columns with textual data.
   - Allows advanced searching and filtering of full-text data.

```sql
CREATE TABLE Articles (
    article_id INT PRIMARY KEY,
    title VARCHAR(200),
    content TEXT,
    FULLTEXT INDEX (content)
);
```

or

```sql
CREATE FULLTEXT INDEX fulltext_index_name
ON table_name (column_name);
```

6. **Composite Index**:
   - This is an index created for a combination of two or more columns.
   - Used to optimize operations that involve a combination of multiple columns in queries.

```sql
CREATE TABLE Orders (
    order_id INT,
    product_id INT,
    order_date DATE,
    PRIMARY KEY (order_id, product_id),
    NONCLUSTERED INDEX (order_date)
);
```

or

```sql
CREATE UNIQUE INDEX composite_index_name
ON table_name (column1_name, column2_name);
```

7. **Bitmap Index**:
   - Used to create an index based on bitmaps, where each bit corresponds to a specific value.
   - Typically used to optimize data filtering operations in large tables.

```sql
CREATE TABLE Sales (
    sale_id INT PRIMARY KEY,
    product_id INT,
    sale_date DATE,
    BITMAP INDEX (product_id)
);
```

or

```sql
CREATE UNIQUE BITMAP INDEX bitmap_index_name
ON table_name (column_name);
```

***Summury***
| Index Type | Uniqueness | Clustered | Description |
|---|---|---|---|
| Primary Key | Yes | Yes | A unique index that is automatically created for the primary key of a table. |
| Unique | Yes | No | An index that ensures that no two rows in the table have the same value in the indexed column. |
| Clustered | No | Yes | A special type of index that determines the physical order of rows in the table based on the values of the indexed column. |
| Non-Clustered | No | No | An index that is used to improve the performance of search and sort operations, but does not affect the physical order of rows in the table. |
| Full-Text | No | No | An index that is used to optimize the search performance of textual data. |
| Composite | Yes/No | Yes/No | An index that is created on two or more columns. |
| Bitmap | Yes/No | Yes/No | An index that is used to create an index based on bitmaps, where each bit corresponds to a specific value. |

## Correlated and Non-Correlated Subqueries:

1. **Non-Correlated Subquery (Independent Subquery)**:
   - A non-correlated subquery is a subquery that can be executed independently of the outer query.
   - It does not reference any columns from the outer query.
   - It typically returns a single value or a set of values.
   - Non-correlated subqueries are usually more efficient because they only need to be executed once.

   ```sql
   SELECT product_name
   FROM products
   WHERE product_id IN (SELECT product_id FROM orders WHERE order_date = '2023-01-01');
   ```
   In this case, the subquery is non-correlated because it doesn't depend on the outer query.

2. **Correlated Subquery**:
   - A correlated subquery is a subquery that is dependent on the outer query and references columns from the outer query.
   - It is executed for each row processed by the outer query.
   - Correlated subqueries are typically used when you need to compare values between the subquery and the current row of the outer query.
     
   ```sql
   SELECT employee_name
   FROM employees e
   WHERE e.salary > (SELECT AVG(salary) FROM employees WHERE department_id = e.department_id);
   ```
   In this case, the subquery is correlated because it references the "department_id" column from the outer query.

In summary, non-correlated subqueries are independent and can be executed once, while correlated subqueries are dependent on the outer query and are executed for each row of the outer query. The choice between them depends on the specific requirements of your query.

## Normal forms
1. **First Level (1NF - First Normal Form)**:
   - Each column must have atomic values, meaning the values in the column cannot be complex or arrays. For example, if you have a "Phones" column, it should not contain a list of phone numbers; each number should be in a separate row.
   - All values in each column must have the same data type. This means that all values in a column should be numbers, strings, dates, etc., depending on the defined data type for that column.

2. **Second Level (2NF - Second Normal Form)**:
   - A table that is already in 1NF, meaning all columns have atomic values and the appropriate data type.
   - The second level of normalization additionally requires that all columns, except the primary key, depend on the entire primary key. This means that the data in the table should be organized in such a way that no column depends on another column but depends on the primary key. For example, if you have an "Orders" table with columns "Order Number," "Product," and "Quantity," each order entry should have a unique index, and other columns ("Product" and "Quantity") should depend on the order number.

3. **Third Level (3NF - Third Normal Form)**:
   - The table is already in 2NF, which means it has atomic values, and all columns depend on the primary key.
   - The third level of normalization additionally requires the absence of transitive dependencies, meaning columns should not depend on each other through other columns. For example, if "Salary" depends on "Position," and "Position" depends on "Department," then "Salary" should not depend on "Department" (transitive dependency).
   
4. **Boyce-Codd Normal Form (BCNF) - Enhanced Third Level**:
   - This level of normalization additionally requires the absence of dependencies that are not superkeys. In other words, every non-key column must be fully functionally dependent on superkeys, and there should be no redundant or unnecessary dependencies (they should depend on the full key).

5. **Fourth Level (4NF - Fourth Normal Form)**:
   - The table is in 3NF, which means it has atomic values, all columns depend on the primary key, and there are no transitive dependencies.
   - The fourth level of normalization sets the requirement to avoid multivalued dependencies. This means that if many values in one column correspond to one value in another column, these values should be placed in a separate table. For example, if you have an "Orders" table with columns "Order Number" and "Products" (where each order number has multiple products), you could create a separate "Order Products" table, where each record associates an order number with a product.

6. **Fifth Level (5NF - Fifth Normal Form)**:
   - The table is in 4NF, meaning it has atomic values, all columns depend on the primary key, there are no transitive dependencies or multivalued dependencies.
   - The fifth level of normalization tasks you with avoiding join dependencies. This means that data that can be reconstructed by joining tables should be separated into individual tables that are stored without redundancy.
     
## Transaction 
```sql
START TRANSACTION;
COMMIT;
ROLLBACK;
```

## ACID

***ACID*** is an acronym that represents a set of properties ensuring reliable transaction processing in a database. This acronym consists of the following properties:

***Atomicity***: This property ensures that a transaction is treated as a single, indivisible unit of work. It means that all operations within a transaction either fully execute or are fully canceled in case of an error. In other words, a transaction is an all-or-nothing concept.

***Consistency***: Consistency guarantees that a transaction transitions the database from one state of integrity to another. In other words, a transaction must adhere to specific rules and constraints that maintain data integrity. If a transaction violates any rules or constraints, it is rolled back.

***Isolation***: Isolation ensures that the operations of one transaction are isolated from the operations of other transactions. This means that concurrent execution of multiple transactions does not lead to conflicts or anomalies. Isolation levels, such as "Read Uncommitted," "Read Committed," "Repeatable Read," and "Serializable," define the degree of isolation between transactions.

***Durability***: Durability ensures that once a transaction is committed, its changes are permanent and survive any subsequent failures, including system crashes. Typically, this property is achieved by recording the transaction's changes to non-volatile storage, such as a hard disk.   

***Here, we will discuss the main problems of transaction isolation in databases, namely dirty reads, non-repeatable reads, and phantom reads:***

***Dirty Reads***:
Issue: This problem occurs when one transaction reads uncommitted (unapproved) data that may be subsequently rolled back or revoked by another transaction.
Example: Transaction A reads a value from the database that Transaction B changes and revokes before committing.
Consequences: This can lead to incorrect results and data inconsistency. Transaction A reads data that no longer reflects the current state of the system.

***Non-Repeatable Reads***:
Issue: This problem arises when one transaction reads the same value twice, but in the meantime, another transaction changes this value, causing the first reading to differ from the second.
Example: Transaction A reads the "Balance" field and then reads it again, but in the meantime, Transaction B changes this balance.
Consequences: This can lead to unexpected results as the value read by the transaction can change between the first and second readings, violating data consistency.

***Phantom Reads***:
Issue: This problem occurs when one transaction reads a set of records, but in the meantime, another transaction adds or removes records that match the criteria of the first query.
Example: Transaction A reads all customer orders, and another transaction B deletes one of these orders.
Consequences: This can result in unfair outcomes and data inconsistency as Transaction A receives records that should not exist. 

### Transactions isolation levels

***Read Uncommitted***:
At this level, transactions can read even uncommitted changes made by other transactions.
It allows for problems like dirty reads, non-repeatable reads, and phantom reads.
```sql
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
```

***Read Committed***:
Transactions wait for other transactions to finish their changes before reading data.
It prevents problems like dirty reads but can still lead to non-repeatable reads and phantom reads.
```sql
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
```

***Repeatable Read***:
Transactions wait for other transactions to finish their changes before reading data. Additionally, they lock the rows they are reading to prevent changes by other transactions.
It prevents problems like dirty reads and non-repeatable reads but still allows for phantom reads.
```sql
SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
```

***Serializable***:
At the highest level, transactions block each other to avoid all forms of interaction anomalies.
It prohibits all types of reading anomalies, such as dirty reads, non-repeatable reads, and phantom reads. However, it comes at the cost of executing everything sequentially, which can lead to limited resource availability. This level imposes the most restrictions on parallelism, potentially resulting in a high number of waiting transactions and reduced productivity.
```sql
SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
```
