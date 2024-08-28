---
type: "docs"
title: SQL Python
draft: false
url: "/docs/sql-python/"
---

# SQL in Python

- Use the command `pip install mysql-connector-python` to install MySQL Python.
- Import the module as `import mysql.connector`

## Creating a Database

```python
import mysql.connector
db = mysql.connector.connect(
    host="localhost",
    user="root",
    passwd="0334"
)

mycursor = db.cursor()
mycursor.execute('CREATE DATABASE sampleDB')

db.close()
```

- A database called **sampleDB** is created.

## Checking if a Database Exists

```python
import mysql.connector
db = mysql.connector.connect(
    host="localhost",
    user="root",
    passwd="0334"
)

mycursor = db.cursor()
mycursor.execute('SHOW DATABASES')
for x in mycursor:
    print(x)

db.close()
```

- Prints all the databases in the server. Or you can try to access the databases while creating the connection.

```python
import mysql.connector

db = mysql.connector.connect(
    host="localhost",
    user="user",
    passwd="xyzw",
    database="sampleDB"
)

db.close()
```

## Creating a Table

```python
import mysql.connector

db = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="sampleDB"
)

mycursor = db.cursor()
mycursor.execute("CREATE TABLE customers (
    name VARCHAR(255),
    address VARCHAR(255)
    )")

db.close()
```

### Checking if a Table Exists

```python
import mysql.connector

db = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="sampleDB"
)

mycursor = db.cursor()
mycursor.execute("SHOW TABLES")

for x in mycursor:
  print(x)

db.close()
```

## Updating a Table Using **ALTER** Command

- And using **PRIMARY KEY** on an existing table

  ```python
  import mysql.connector
  ```

db = mysql.connector.connect(
host="localhost",
user="yourusername",
password="yourpassword",
database="sampleDB"
)

mycursor = db.cursor()

mycursor.execute("ALTER TABLE customers ADD COLUMN id INT AUTO_INCREMENT PRIMARY KEY")

db.close()

````
## INSERT INTO TABLE

### Single Row Insertion
``` python
import mysql.connector

db = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="mydatabase"
)

mycursor = db.cursor()

sql = "INSERT INTO customers (name, address) VALUES (%s, %s)"
val = ("John", "Highway 21")
mycursor.execute(sql, val)

db.commit() # Required to make changes in the table

print(mycursor.rowcount, "Record Inserted.")
````

### Multiple Row Insertion

- Execute the **executemany()** method

```python
# Fill the customers table with multiple records of data

import mysql.connector

db = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="sampleDB"
)

mycursor = db.cursor()

sql = "INSERT INTO customers (name, address) VALUES (%s, %s)"
val = [
  ('Peter', 'Lowstreet 4'),
  ('Amy', 'Apple st 652'),
  ('Hannah', 'Mountain 21'),
  ('Michael', 'Valley 345'),
  ('Sandy', 'Ocean blvd 2'),
  ('Betty', 'Green Grass 1'),
  ('Richard', 'Sky st 331'),
  ('Susan', 'One way 98'),
  ('Vicky', 'Yellow Garden 2'),
  ('Ben', 'Park Lane 38'),
  ('William', 'Central st 954'),
  ('Chuck', 'Main Road 989'),
  ('Viola', 'Sideway 1633')
]

mycursor.executemany(sql, val)

db.commit()
print(mycursor.rowcount, "was inserted.")
db.close()
```

### GET INSERTED ID

- Get the ID of the last entered row by asking the cursor object.

```python
import mysql.connector

db = mysql.connector.connect(
    host="localhost",
    user="username",
    password="123456",
    database="sampleDB"
)

mycursor = db.cursor()

sql = "INSERT INTO customers (name, address) VALUES (%s, %s)
val = ("Michelle", "Blue Village")
mycursor.execute(sql, val)

db.commit()
print("1 Record inserted, ID:", mycursor.lastrowid)
db.close()
```

## SELECT QUERY

```python
# Select all records from the customers table and display the result
import mysql.connector

db = mysql.connector.connect(
    host="localhost",
    user="yourusername",
    password="yourpassword",
    database="sampleDB"
)

mycursor = db.cursor()
mycursor.execute("SELECT * FROM customers")
result = mycursor.fetchall()
for i in result:
    print(i)

db.close()
```

### USING THE FETCHONE() METHOD

- To fetch only one record from the selected query

```python
import mysql.connector

db = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="sampleDB"
)

mycursor = db.cursor()

mycursor.execute("SELECT * FROM customers")

myresult = mycursor.fetchone()
print(myresult)
db.close()
```

## WHERE FILTER

```python
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="mydatabase"
)

mycursor = mydb.cursor()

sql = "SELECT * FROM customers WHERE address ='Park Lane 38'"

mycursor.execute(sql)

myresult = mycursor.fetchall()

for x in myresult:
  print(x)

mydb.close()
```

## PREVENT SQL INJECTION

- **SQL Injection** is a common web hacking technique to destroy or misuse the database. To prevent this attack, you should escape the values provided in the query by using placeholder `%s` method

```python
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="mydatabase"
)

mycursor = mydb.cursor()

sql = "SELECT * FROM customers WHERE address = %s"
adr = ("Yellow Garden 2", )

mycursor.execute(sql, adr)

myresult = mycursor.fetchall()

for x in myresult:
  print(x)
mydb.close()
```

## ORDER BY STATEMENT

```python
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="mydatabase"
)

mycursor = mydb.cursor()

sql = "SELECT * FROM customers ORDER BY name"

mycursor.execute(sql)

myresult = mycursor.fetchall()

for x in myresult:
  print(x)
mydb.close()
```

## DELETE FROM STATEMENT

```python
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="mydatabase"
)

mycursor = mydb.cursor()

sql = "DELETE FROM customers WHERE address = 'Mountain 21'"

mycursor.execute(sql)

mydb.commit() # Required when making changes to the Database

print(mycursor.rowcount, "record(s) deleted")
mydb.close()
```

- In the above example, the query variable **Mountain 21** is directly entered into the statement which may cause **SQL Injection**. Therefore, placeholder is used. The above code can be written as :

```python
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="mydatabase"
)

mycursor = mydb.cursor()

sql = "DELETE FROM customers WHERE address = %s" # Statement does not have query value
adr = ("Yellow Garden 2", ) # Query is done usiong a variable to which the value is assigned

mycursor.execute(sql, adr)

mydb.commit()

print(mycursor.rowcount, "record(s) deleted")
mydb.close()
```

## DROP (Delete) TABLE

```python
# Delete the table customers
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="mydatabase"
)

mycursor = mydb.cursor()
sql = "DROP TABLE customers"

mycursor.execute(sql)
mydb.close()
```

- Use the **IF EXISTS** keyword if you want to delete something that may or may not already be deleted.

```python
import mysql.connector

db = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="mydatabase"
)

mycursor = db.cursor()

sql = "DROP TABLE IF EXISTS customers"

mycursor.execute(sql)
db.close()
```

## UPDATE THE TABLE

- Update existing records byusing the **UPDATE** statement

  ```python
  # Change the address in the column from "Valley 345" to "Canyon 123"
  ```

import mysql.connector

mydb = mysql.connector.connect(
host="localhost",
user="yourusername",
password="yourpassword",
database="mydatabase"
)

mycursor = mydb.cursor()

sql = "UPDATE customers SET address = '%s' WHERE address = '%s'"
val = ("Canyon 123", "Valley 345")
mycursor.execute(sql, val) # Injection-proof statement

mydb.commit() # Required to make changes to the database

print(mycursor.rowcount, "record(s) affected")
mydb.close()

````
## LIMIT THE FILTER

- Limit the No. of records returned from the query, by using the **LIMIT** filter

``` python
import mysql.connector

db = mysql.connector.connect(
    host="localhost",
    user="yourusername",
    password="password123",
    datanase="sampleDB"
)

mycursor = db.cursor()
mycursor.execute("SELECT * FROM customers LIMIT 5")
result = mycursor.fetchball()

for x in result:
    print(x)
db.close()
````

### START FROM ANOTHER POSITION

-If you want to return five records, starting from the third record, you can use the **OFFSET** keyword

```python
import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="mydatabase"
)

mycursor = mydb.cursor()

mycursor.execute("SELECT * FROM customers LIMIT 5 OFFSET 2")

myresult = mycursor.fetchall()

for x in myresult:
  print(x)
mydb.close()
```

## JOIN STATEMENT

```python
 import mysql.connector

mydb = mysql.connector.connect(
  host="localhost",
  user="yourusername",
  password="yourpassword",
  database="mydatabase"
)

mycursor = mydb.cursor()

sql = "SELECT \
  users.name AS user, \
  products.name AS favorite \
  FROM users \
  INNER JOIN products ON users.fav = products.id"

mycursor.execute(sql)

myresult = mycursor.fetchall()

for x in myresult:
  print(x)

mydb.close()
```
