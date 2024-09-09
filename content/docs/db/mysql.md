---
type: "docs"
title: MySQL
url: /docs/misc/mysql/
---

# MySQL

### Resources

[PostgreSQL Official](https://www.postgresql.org/docs/) |
[SQLite](https://devdocs.io/sqlite/)  
[Cheatsheet](https://overapi.com/mysql) |
[All DB SQL Injection CC](https://portswigger.net/web-security/sql-injection/cheat-sheet) |
[SQL Zoo](https://sqlzoo.net/wiki/SQL_Tutorial) |
[SQL Practise](https://www.sql-practice.com) |
[Data Lemur - SQL practise, interviews](https://datalemur.com) |  
[SQL Bolt](https://sqlbolt.com) |
[SQL PD](https://sqlpd.com) |
[SQL Murder Mystery- SQLite](https://mystery.knightlab.com) |
[Pagila](https://github.com/devrimgunduz/pagila) |

---

### Quick Links to Frequently Searched Topics

---

MySQL Installation Link : [MySQL](https://dev.mysql.com/downloads/installer/)

**Notes**:

- DBMS - Data Base Management System
- RDBMS - Relational Data Base Management System
- SQL - Structured Query Language
- SQL is basically 4 kinds of languages in one package:
  1. Data Query Language
  2. Data Definition Language
  3. Data Control Language
  4. Data Manipulation Language

---

### Tables

- A table is a database object that is made of rows and columns. It contains data.Table is created using CREATE TABLE command
- A field is a column in a table that is supposed to provide specific info about all the records in the table
- A record is a row in a table. It is also called horizontal entity while field is the vertical entity of the table
- A NULL value is no value, it is neither a space nor a zero, it is nothing

#### Creating a Table

```SQL
CREATE TABLE tableName (
    column1 datatype,
    column2 datatype,
    PRIMARY KEY(column1)
    -- column1 becomes primary key
);
```

To check if the table is created or not, run `DESC tableName;`

### Creating a table from other Tables

```SQL
CREATE TABLE newTable AS
SELECT column1, column2.....column5
FROM oldTable
[WHERE]; # WHERE condition is optional
```

| Command                            | Description                                                              |
| ---------------------------------- | ------------------------------------------------------------------------ |
| `DROP TABLE tabName;`              | Deletes a Table                                                          |
| `SHOW TABLES;` / `DESC tableName;` | Verify the existence of a Table                                          |
| `TRUNCATE table_name`              | Deletes all the records existing inside a table but not the Table itself |
|                                    |                                                                          |

### Using **INSERT INTO** query to enter data into tables

```sql
INSERT INTO tableName column1, column2, column3
VALUES value1, value2, value3;
```

**Notes :**

- When the order of the input is in the same order as the field/column order, the columns in the code are omitted
- `SELECT * FROM tableName;` to verify if the data was entered.

### Populating a Table With Data From Other Table

The two tables must be compatible for this to work.

```sql
INSERT INTO TABLE1 column1, column2, column3
SELECT column1, column2, column3
FROM table2
[WHERE]; -- optional WHERE condition
```

### Inserting Multiple Rows Into a Table In One Go

```sql
INSERT INTO table(column1)
VALUES (value1),
       (value2),
       (value3); -- 3 rows of data inserted into column1
```

### Alter Table

The `ALTER TABLE` statement is used to add, delete, or modify columns in an existing table. It is also used to add and drop various constraints on an existing table.

```sql
-- Adding Column
ALTER TABLE table_name
ADD column_name datatype;

-- Dropping Column
ALTER TABLE table_name
DROP COLUMN column_name;

-- Modify Column by changing datatype
ALTER TABLE table_name
MODIFY COLUMN column_name datatype;
```

---

## Querying Functions

### Nested Query

> Name all the employees who have sold over $30,000 to a single client
> (problem from Mike Dane's Course)

```sql
SELECT employee.firstName, employee.lastName
FROM employee
WHERE employee.emp_id IN (
    SELECT works_with.emp_id
    FROM works_with
    WHERE works_with.total_sales > 30000
); -- Nested Query
```

### SELECT Query

```sql
SELECT *
FROM tableName;
-- Use * to select every column in the table

SELECT firstName, lastName
FROM employees;
-- Selects firstName, lastName columns from the table employees

SELECT fistName, lastName
CONCAT(firstName, lastName) AS fullName
FROM employees;
-- Selects firstName, lastName and creates a new column fullName
-- which is a concatenation of firstName, whitespace and lastName columns
```

**Note:** Arithmetic Operations can also be performed on the columns during `SELECT` query

### WHERE Clause

```sql
SELECT *
FROM customers
WHERE points > 30000;
```

### ORDER BY Clause

```sql
SELECT *
FROM customers
ORDER BY state;
-- DESC/ASC keywords to order in descending/ascending order respectively.
```

```sql
SELECT firstName, lastName
FROM customers
ORDER BY 1, 2
```

> In the above query, the records are first sorted by firstName followed by lastName. This approach is not recommended and the column name approach should be followed instead.

### GROUP BY Clause

```sql
-- MOSH
SELECT client_id,
    SUM(invoice_total) AS total_sales
FROM invoices
GROUP BY client_id
ORDER BY total_sales DESC;

-- MOSH
SELECT
    date,
    pm.name AS payment_method
    SUM(amount) AS total_payments
FROM payments p
JOIN payment_methods AS total_payments
    ON p.payment_method = pm.payment_method_id
GROUP BY date, payment_method
ORDER BY date;
```

### HAVING Clause

`HAVING` Clause filters data offer GROUP BY clause is applied

```sql
SELECT
    client_id,
    SUM(invoice_total) AS total_sales
FROM invoices
WHERE
GROUP BY client_id
HAVING total_sales > 500;
```

### USING Clause

If two columns in different tables are to be joined and they have same name (same EXACT name) `USING` clause is used to reduce length & increase code readability.

```sql
SELECT
    o.order_id,
    c.first_name,
    sh.name AS shipper
FROM orders o
JOIN customers c
    USING (customer_id)
LEFT JOIN shippers sh
    USING (shipper_id)
```

```sql
SELECT
    payments.date,
    clients.name,
    payments.amount,
    payment_methods.name
FROM payments
JOIN clients
    USING (client_id)
JOIN payment_methods
    ON payments payment_method = payment_methods.payment_method_id
```

---

## Datatypes in MySQL

### Numeric Data Types

```sql
Big INT - Really Big Values
INT - Big Values
smallint - -32,768 to 32,768
tinyint - 0 to 255
decimal(m, d)
float(m, d)
numeric(m, d)
```

**Optional Parameters :** m - display length, d - No. of decimals

### Date & Time Data Types

```sql
Date Time - (YYYY-MM-DD HH:MM:SS)
Date - (YYYY-MM-DD)
Time - (HH:MM:SS)
Year - (YYYY)
```

### Character Data Types

```sql
char(m)
VARCHAR(m)
Text - To store large amount of text
```

**Optional Parameters :** m - display length, d - No. of decimals

### Images

```sql
BLOB - Binary Large Object
```

---

## MySQL Constraints

| Constraint             | Explanation                                                                                                                                                                                               |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NOT NULL CONSTRAINT    | Apply this constraint if a field has to get some value for every row                                                                                                                                      |
| DEFAULT CONSTRAINT     | While populating a table, if a column misses out on input, then the default value will be used to fill the entry                                                                                          |
| UNIQUE CONSTRAINT      | This constraint makes sure that all the values entered for the field to which the constraint is applied are unique i.e., different Error message is generated if duplicate values are input.              |
| PRIMARY KEY CONSTRAINT | This constraint is a combination of NOT NULL & UNIQUE constraints. In this constraint, some value would have to be provided for each record(row) and entered values must be unique & not have duplicates. |

```sql
CREATE TABLE student (
    id INT Primary,
    name VARCHAR(20) NOTNULL,
    majors VARCHAR(20) UNIQUE
);
```

Using Auto Increment for id column

```sql
CREATE TABLE student (
    id INT AUTO_INCREMENT,
    name VARCHAR(20)
);
```

---

## Database Operations

| Command                  | Function                                     |
| ------------------------ | -------------------------------------------- |
| `CREATE DATABASE dbName` | Create Database                              |
| `USE dbName`             | Use a Database                               |
| `DROP database dbName`   | Drop Database Note : The delete is permanent |

---

## Trivial Functions

### DELETE Function

```sql
DELETE FROM tableName
[WHERE];
```

### DISTINCT Function

```sql
SELECT DISTINCT columnName
FROM tableName;
-- Picks all the distinct values in the selected column
```

### UNION Function

- Union can be used to join two rows from different tables.

- Unifies two different columns into one column. Each SELECT query should have same No. of columns & same datatype.

  ```sql
  SELECT columnX
  FROM table1
  UNION
  SELECT branchName
  FROM table2;
  ```

---

## Operators in MySQL

### Arithmetic Operators

- Addition (+)
- Subtraction (-)
- Multiplication (\*)
- Division (/)
- Modular Division (%)

### Comparison Operators

- Equal (=)
- Greater Than (>)
- Lesser Than (<)
- Greater Than or Equal to (>=)
- Lesser Than or Equal to(<=)
- Not Equal to (<> or !=)

**Examples**

```sql
SELECT *
FROM employees
WHERE age >= 30 AND salary >= 15000;
```

### Logical Operators

- OR
- ISNULL
- ALL
- AND
- BETWEEN
- IN
- LIKE

**Examples**

```sql
SELECT *
FROM employees
WHERE salary IS NULL;
```

```sql
SELECT *
FROM employees
WHERE name LIKE 'p%'
-- % is a wildcard character
```

```sql
SELECT *
FROM employee
WHERE age IN (28, 30, 36);
```

### REGEXP Operators

```sql
SELECT *
FROM customers
WHERE last_name REGEXP '^field'
```

| Command | Search                                     |
| ------- | ------------------------------------------ |
| %b      | search term has last character b           |
| %b%     | search term has 'b' in it somewhere        |
| -y      | second character is y                      |
| --z     | third character is z                       |
| %       | any No. of characters                      |
| ^       | beginning of a string                      |
| $       | end of a string                            |
| / or \| | logical OR                                 |
| [abcd]  | Searches for the chars inside the brackets |
| [a-f]   | Searches for the chars in the range        |

**REGEXP Operator Examples**

```sql
-- MOSH'S DATABASES

SELECT *
FROM customers
WHERE last_name REGEXP 'field'
-- O/P : Brushfield

SELECT *
FROM customers
WHERE last_name REGEXP 'field$'
-- O/P : Brushfield

SELECT *
FROM customers
WHERE last_name REGEXP '^field'
-- O/P : No Result. No last name starting with field exist.

SELECT *
FROM customers
WHERE last_name REGEXP 'field|mac'
-- O/P : MacCaffey, Brushfield

SELECT *
FROM customers
WHERE last_name REGEXP '^field|mac|rose'
-- O/P : MacCaffrey, Roseburgh

SELECT *
FROM customers
WHERE last_name REGEXP 'field$|mac|rose'
-- O/P : MacCaffrey, Brushfield, Roseburgh

SELECT *
FROM customers
WHERE last_name REGEXP '[gim]e'
-- Looks for customers with lastname containing ge or ie or me
-- O/P : Brushfield, Boagey

SELECT *
FROM customers
WHERE last_name REGEXP 'e[a-h]'
-- Looks for lastnames containing ea, eb, ec,.........eh
-- O/P: Roseburgh, Naseby
```

## Joining In MySQL

### Inner Join

A `JOIN` command is `INNER JOIN` by default.

```sql
-- MOSH
USE sql_store
SELECT
    oi.order_id,
    oi.product_id, p.name,
    p.name,
    oi.quantity,
    oi.unit_price
FROM products p
JOIN order_items oi
    ON oi.product_id = p.product_id;
```

#### Joining Along Databases

```sql
-- MOSH
SELECT *
FROM sql_store.order_items oi
JOIN products p
    ON oi.product_id = p.product_id;
```

#### Self JOIN

```sql
USE sql_hr
SELECT
    e.employee_id,
    e.first_name,
    m.first_name AS manager
FROM employees e
JOIN employees m
    ON e.reports_to = m.employee_id;
```

#### Joining Multiple Tables

```sql
-- MOSH
USE sql_store
SELECT
    o.order_id,
    o.order_date,
    c.first_name,
    c.last_name,
    os.name AS status
FROM orders o
JOIN customers c
    ON o customer_id = c.customer_id
JOIN order_statuses os
    ON o.status = os.order_status_id;
```

```sql
-- MOSH EXERCISE
USE sql_invoicing

SELECT
    c.name,
    p.invoice_id,
    p.date,
    p.amount,
    pm.name AS pay_mode
FROM payments p
JOIN clients c
    ON p.client_id = c.client_id
JOIN payment_methods pm
    ON p.payment_method = pm.payment-method-id;
```

#### Compound JOIN Conditions

Compound Join is done when there are more than one primary key existing ina table and the record cannot be chosen uniquely with just one join.

`USE sql_store`

```sql
SELECT *
FROM order_items oi
JOIN order_item_notes oin
    ON oi.order_id = oin.order_id
    AND oi.product_id = oin.product_id;
```

#### Implicit Join

```sql
-- MOSH
SELECT *
FROM orders o, customers c
WHERE o.customer_id = c.customer_id;
```

**Note:** Failure to include the WHERE condition would result in all columns in table 1 joining to all the columns in table 2

### Outer Join

#### Left & Right Join

> As a rule, avoid RIGHT JOIN as it may make code-reading harder

```sql
-- MOSH
SELECT
    c.customer_id,
    c.first_name,
    o.order_id
FROM customers c
RIGHT JOIN orders o
    ON c.customer_id = o.customer_id
ORDER BY c.customer_id;
```

> **NOTE :** The word `OUTER` after `RIGHT` & before `JOIN` keywords is optional

#### Outer Joins Between Multiple Tables

```sql
-- MOSH
SELECT
    c.customer_id,
    c.first_name,
    o.order_id,
    sh.name AS shipper
FROM customers c
LEFT JOIN orders o
    ON c.customers_id = o.customer_id
LEFT JOIN shippers sh
    ON o.shipper_id = sh.shipper_id
ORDER BY c.customer_id;
```

```sql
-- MOSH
SELECT
    o.order_id,
    o.order_date,
    c.first_name AS customer,
    sh.name AS shipper,
    os.name AS status
FROM orders o
JOIN customers c
    ON o.customers_id = c.customers_id
LEFT JOIN shippers sh
    ON o.shipper_id = sh.shipper_id,
JOIN order_statuses os
    ON o.status = os.order_status_id;
```

#### SELF OUTER JOINS

In the previous self join which is INNER, the manager's record does not get shown because the manager doesn't report to the manager. In order to include this record too, SELF OUTER JOIN is used.

```sql
SELECT
    e.employee_id,
    e.first_name,
    m.first_name AS manager
FROM employees e
LEFT JOIN employees m
    ON e.reports_to = m.employees_id;
```

#### NATURAL JOIN & CROSS JOIN

Natural Join may produce unexpected results. Use with caution.

```sql
-- MOSH, NATURAL JOIN
SELECT
    o.order_id,
    c.first_name
FROM orders o
NATURAL JOIN customers c;
```

```sql
-- MOSH, CROSS JOIN
SELECT
    c.first_name AS customer,
    p.name AS product,
FROM customers c
CROSS JOIN products p  -- Explicit Syntax
ORDER BY c.first_name;
SELECT
    c.first_name AS customer,
    p.name AS product
FROM customers c, orders o -- Implicit Syntax
ORDER BY c.first_name;
```

---

## Unions in MySQL

```sql
SELECT
    order_id,
    order_date,
    'Active' AS status
FROM orders
WHERE order_datwe >= '2019-01-01';

UNION

SELECT
    order_id,
    order_date,
    'Archived' AS status
FROM orders
WHERE order_date < '2019-01-01';
```

#### Inserting Hierarchical Rows

```sql
INSERT INTO orders(
    customer_id,
    order_date,
    status
    )
VALUES(1, '2019-01-02', 1);
INSERT INTO order_items
VALUES(LAST_INSERT_ID(), 1, 1, 2.95),
      (LAST_INSERT_ID(), 2, 1, 3.95);
```
