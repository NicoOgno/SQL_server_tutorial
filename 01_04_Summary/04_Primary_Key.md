# $${\color{orange}Primary\space Key\space 🔑}$$

## $${\color{green}Stablishing\space a\space Primary\space Key\space PK}$$

🔹 Go to the table (example: dbo.DBName) right click on it and click *`Design`*. Then select a field to be the `PK`, and click the button at the top right `Set Primary Key` 🗝️. Then set `Identity Specification` to YES. The `PK` will be stored in the *keys* folder in the specific Table (dbo.DBName).

> [!NOTE]
> 📝
> `PK` fields don't allow nulls 🚫.
> `Composed PK's` don't need to set `Identity Specification` to YES 🚫.

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