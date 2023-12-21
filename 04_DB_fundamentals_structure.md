# $${\color{orange}Database \space \ Fundamentals \space and \space Structure}$$

- **Fields:** are at the top of the database table and refers to the type of the data value.

- **Records:** are the line of fields in a database table.
<br><br>

| Field 1   | Field 2 |    Fruits      |  Price |
|----------|:-------------:|:-------------:|------:|
| value 1 | valueInfield2 | bananas | $1600 |
| value 2 |  anotherValue | tomatoes   |   $12 |
| This | line | is a  |   Register |

<br><br>

## $${\color{green}NULL \space\space Value}$$

**NULL value**

A **NULL** value represents the *absence of a value* in a column of a table. This indicates that no value has been assigned in that particular column.

***NULL*** *values* are different from blank values or numeric values like 0 (zero), as the latter are valid values that can be assigned to a column. For example, in a Taxes table, some values in a column may contain 0 (zero), while others may have no tax value assigned yet, in which case the column would have a `NULL value`.

<br><br>

## $${\color{green}Primary\space\space Key\space\space and\space\space Foreign\space\space Key}$$

**Primary Key**

A **Primary Key** is a concept in relational databases that refers to a field or set of fields in a table whose *values are unique for each row* in the table. The main function of a *Primary Key* is to provide a *unique way to identify each record in the table*.

1. **Uniqueness**: Each value in the designated column or set of columns as the `primary key must be unique for each row` in the table. This ensures that there are no duplicates in the primary key column.

2. **Non-nullability**: Values in the primary key `cannot be null` (NULL). Each row must have a unique and non-null value in the primary key column.

3. **Unique Identification**: The primary key is `used to uniquely identify each row in the table`. This is essential for `establishing relationships between tables` in relational databases.

4. **Composite Key**: a table may have `more than one PK field as a Secondary Key field`

5. **Just One PK**: In a relational database, *each table can have only one Primary Key*.

<br><br>

**Foreign Key**

- A **foreign key** refers to a field (or set of fields) in a database table that `references the Primary Key in another table`. Its main purpose is to establish a relationship between the two tables.

- The `Foreign Key serves as a link between tables` and ensures referential integrity in the database. This means that the values in the `Foreign Key column must match the values in the Primary Key of the referenced table` or can be null if allowed.

- The relationship created by the Foreign Key is crucial for maintaining consistency in the database and enables queries and operations involving data from both tables.

- A table may have more than one Foreign Key.

<br><br>

## $${\color{green}Database\space\space Normalization}$$


**Database normalization** is a process in database design that involves organizing tables and fields to reduce redundancy and dependency. The goal is to improve data integrity and minimize data anomalies in a relational database.

The primary objectives of database normalization include:

1. **Eliminating data redundancy:** Storing data in a way that avoids unnecessary duplication.

2. **Reducing data anomalies:** Ensuring that updates, inserts, and deletes in the database do not lead to unexpected issues, such as inconsistencies or errors.

3. **Improving data integrity:** Establishing relationships between tables to maintain accuracy and reliability of data.

<br>

**Normal Forms**

***First Normal Form (1NF):***
A table is said to be in First Normal Form if and only `if all its fields (attributes) contain atomic values.` This means that each attribute of the table should have a unique value for an occurrence of the entity. Repeating groups are not allowed.

***Second Normal Form (2NF):***
A table is in Second Normal Form if and only `if it is in 1NF, and all non-key attributes are fully functionally dependent on the primary key.`

***Third Normal Form (3NF):***
A table is in Third Normal Form if and only `if it is in 2NF, and non-key attributes are independent of each other.` This means that the values of attributes depend only on the primary key and do not depend on another non-key attribute. The value of the attribute should not depend on the value of another non-key attribute.

<br>

#### *Patient Table* non-normalized:

| Nombre | Pais | IdMedico | Medico |
|--------|:----:|:--------:|-------:|
| Juan Carlos Ruber | España | 1 | PEREZ, Juan |
| Carlos Andrés Montoya | México | 1 | PEREZ, Juan |
| Juan Sanchez | México | 2 | Lopez, Mónica |
| Juan Sanchez | México | 2 | Lopez, Mónica |

<br>

#### *Patient Table* (1NF):

| IdPatient(PK)| Nombre | Pais | IdMedico | Medico |
| ------------ |:--------:|:----:|:--------:|-------:|
| 1 | Juan Carlos Ruber | España | 1 | PEREZ, Juan |
| 2 | Carlos Andrés Montoya | México | 1 | PEREZ, Juan |
| 3 | Juan Sanchez | México | 2 | Lopez, Mónica |
| 4 | Juan Sanchez | México | 2 | Lopez, Mónica |

<br>

#### *Patient Table* (2NF and 3NF):

| IdPatient(PK)| Nombre | IdPais |
| ------------ |:--------:|----:|
| 1 | Juan Carlos Ruber | ESP |
| 2 | Carlos Andrés Montoya | MEX |
| 3 | Juan Sanchez | MEX |
| 4 | Juan Sanchez | MEX |

<br>

#### *Pais Table:*
| IdPais (PK) | Pais |
| ------------ |----:|
| MEX | Mexico |
| ESP | Spain |

<br>

#### *Medico Table:*
| IdMedico (PK) | Medico |
| ------------ |----:|
| MEX | PEREZ, Juan |
| ESP | Lopez, Mónica |

<br>

#### *TurnoPatiente Table:*
| IdTurno(PK)| IdPatient | IdMedico |
| ------------ |:--------:|----:|
| 1 | 1 | 1 |
| 2 | 2 | 1 |
| 3 | 3 | 2 |
| 4 | 4 | 2 |

<br><br>

## $${\color{green}Data \space\space Types}$$

**Data Types**

In SQL, a data type `refers to the type of values that can be stored` in a column of a table. Data types in SQL specify the kind of information each column can hold and also determine how that information is stored and manipulated.

#### Units of Measurement in Computer Science:

- *Bit* = 0 ó 1
- *Byte* = 8 bits
- *Kilobyte* = 1024 bytes
- *Megabyte* = 1024 kilobytes
- *Gigabyte* = 1024 megabytes
- *Terabyte* = 1024 gigabytes
- *Petabyte* = 1024 terabytes 

#### Common data types:

1. **INTEGER/INT:** To store whole numbers.

2. **VARCHAR(n)/CHAR(n):** VARCHAR for variable-length strings and CHAR for fixed-length strings, where "n" represents the maximum length of the string.

3. **FLOAT/REAL/DOUBLE:** To store decimal or floating-point numbers.

4. **DATE/TIME/DATETIME:** To store dates and times.

5. **BOOLEAN/BOOL:** To store logical values (true/false).

6. **NUMERIC/DECIMAL:** To store decimal numbers with fixed precision.

#### Data types Description:

|$${\color{orange}Numbers}$$|
|-------------|
**BIT** 1 byte 
0 or 1 
True o False
--
**TINYINT** 1 byte
0 To 255
--
**SMALLINT** 2 bytes
From -32,768 To 32,767
--
**INT** 4 bytes
From -2,147,483,648 To 2,147,483,647
--
**BIGINT** 8 bytes
From -9,223,372,036,854,775,808 To 9,223,372,036,854,775,807
--
**MONEY** 8 bytes
From -922,337,203,685,477.5808 To 922,337,203,685,477.5807
--
**DECIMAL** (10,2) Precisión y Escala
1 To 9: 5 bytes
10 To 19: 9 bytes
20 To 28: 13 bytes
29 To 38: 17 bytes

|$${\color{orange}String}$$|
|-------------|
**CHAR** 1 byte per character
From 1 To 8000
--
**VARCHAR** 1 byte per character variable
From 1 To 8000
--
**NCHAR** 2 bytes per character
From 1 To 4000
--
**NVARCHAR** 2 bytes per character variable
From 1 To 4000
--
**BINARY** 1 byte por valor
From 1 To 8000
--
**VARBINARY** 1 byte por valor variable
From 1 To 8000
<br><br>

|$${\color{orange}Date \space and \space Time}$$|
|-------------|
**DATETIME** 8 bytes
YYYY-MM-DD hh:mm:ss:nnn
01/01/1753 To 31/12/9999
00:00:00 To 23:59:59.997
--
**DATE** 3 bytes
YYYY-MM-DD
From 01/01/0001 To 31/12/9999
--
**TIME** 5 bytes
hh:mm:ss:nnnnnnn
From 00:00:00.0000000 To 23:59:59.9999999
--
**SMALLDATETIME** 4 bytes
YYYY-MM-DD hh:mm:ss
01/01/1900 To 06/06/2079
00:00:00 To 23:59:59