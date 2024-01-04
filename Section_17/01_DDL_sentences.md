# $${\color{orange}DDL\space Sentences}$$

### ALTER

The `ALTER statement` in SQL is used to *modify the structure of an existing database object, such as a table, view, or stored procedure*. The specific syntax and options depend on the type of object you want to alter.

- *Example 1:* **Altering a Table (Adding a Column)**

      ALTER TABLE your_table_name
      ADD new_column_name data_type;

<br>

- *Example 2:* **Altering a Table (Modifying a Column)**

      ALTER TABLE your_table_name
      ALTER COLUMN existing_column_name new_data_type;

<br>

- *Example 3:* **Altering a Stored Procedure**

      ALTER PROCEDURE your_stored_procedure_name
      AS
      -- modify the stored procedure logic here

<br>

- *Example 4:* **Altering a View**

      ALTER VIEW your_view_name
      AS
      -- modify the view definition here

<br>

- *Example 5:* **Using ALTER to Drop a Column**

      ALTER TABLE your_table_name
      DROP COLUMN column_to_be_dropped;

<br>

- *Example 6:* **Using DROP to Remove a Table**

      DROP TABLE your_table_name;

<br><br>

### Create Table Script (previously created)

In the *Object Explorer* got to *`Tables`* in your *Database*, right click on the `Table` you want to obtain the *Script* then ➡️ `Script Table as` ➡️ `CREATE To` ➡️ `New Query Editor Window`. That will show the *DDL sentence* according to the creation of such table.

<br><br>

### Default Arguments in CREATE TABLE

    SET ANSI_NULLS ON
    GO

    SET QUOTED_IDENTIFIER ON
    GO

    CREATE TABLE [DBO].[Country](
        [idCountry] [char](3) NOT NULL,
        [country] [varchar](30) NULL,
    CONSTRAINT [PK_Country] PRIMARY KEY CLUSTERED
    (
        [idCountry] ASC
    )WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO

- **The brackets** are used when we use keywords recognized by the engine, so it interprets them as text and not as a command.

- **DBO** is the default schema of the database.

- **SET ANSI_NULLS** turns on or off the comparison against NULL values.

- **GO** separates one statement from another.

- **SET QUOTED_IDENTIFIER** turns on or off the use of double quotes for reserved words.

- **CLUSTERED** genera una indexación que define cómo se organizan los datos en una tabla en función de la clave primaria.

- **ASC** defines the sorting order of indexing on the primary key.

**Attributes Description:**

1. **PAD_INDEX** is an option used during index creation or rebuilding. This option *determines whether SQL Server should fill index pages up to 100% of their capacity*.

When `PAD_INDEX` is set to `ON`, *SQL Server fills the index pages up to 100% of their capacity*. This can be beneficial to reduce internal index fragmentation. However, it can also increase the size of the index on disk.

    CREATE INDEX IX_Example
    ON MyTable (MyColumn)
    WITH (PAD_INDEX = ON);

In this example, `PAD_INDEX` is set to `ON` to allow for index page padding.

On the other hand, if you set `PAD_INDEX` to `OFF` or do not specify it, *SQL Server will not fill index pages up to 100% of their capacity*.

    CREATE INDEX IX_Example
    ON MyTable (MyColumn)
    WITH (PAD_INDEX = OFF);

<br>

2. **STATISTICS_NORECOMPUTE** option is used to specify whether automatic statistics updating should occur for an index or statistics object. When `STATISTICS_NORECOMPUTE` is set to `ON`, it means that the statistics for the specified index or statistics object won't be automatically recomputed by the SQL Server query optimizer.

        -- Create or update statistics with NORECOMPUTE option
        CREATE STATISTICS IX_Example
        ON YourTable (YourColumn)
        WITH NORECOMPUTE;

<br>

> [!TIP]
> 🧠
> By default, SQL Server automatically updates statistics when a certain threshold of changes in the underlying data occurs. However, in some cases, *you may choose to disable automatic statistics updates to have more control over when statistics are recomputed*.

<br>

3. **IGNORE_DUP_KEY** option is used in the context of creating or rebuilding indexes. When `IGNORE_DUP_KEY` is set to `ON`, *it specifies that duplicate key values should be ignored during the index creation process*, and the index creation continues with the next row.

        -- Create or rebuild an index with IGNORE_DUP_KEY option
        CREATE INDEX IX_Example
        ON YourTable (YourColumn)
        WITH (IGNORE_DUP_KEY = ON);

When `IGNORE_DUP_KEY` is set to `ON`,* any duplicate key values encountered during the creation of the index will be ignored*, and the creation process will proceed without raising an error. *This can be useful in scenarios where you want to create an index on a column that may have duplicate values, and you want to exclude those duplicates from the index without interrupting the entire process*.

<br>

4. **ALLOW_ROW_LOCKS** option is used in the context of index creation or modification to specify whether *row-level locks* can be used. When `ALLOW_ROW_LOCKS` is set to `ON`, it allows the *Database Engine* to use *row-level locks* when it is determining the appropriate *lock granularity*.

        -- Create or rebuild an index with ALLOW_ROW_LOCKS option
        CREATE INDEX IX_Example
        ON YourTable (YourColumn)
        WITH (ALLOW_ROW_LOCKS = ON);

<br>

> [!NOTE]
> 📝
> When you set `ALLOW_ROW_LOCKS` to `ON`, it doesn't mean that only *row-level locks* will be used; rather, it allows the *Database Engine to use **row-level locks** when it deems it appropriate*.

<br>

5. **ALLOW_PAGE_LOCKS** option is used in the context of index creation or modification to specify whether *page-level locks* can be used. When `ALLOW_PAGE_LOCKS` is set to `ON`, it allows the *Database Engine* to use *page-level locks* when it is determining the appropriate *lock granularity*.

        -- Create or rebuild an index with ALLOW_PAGE_LOCKS option
        CREATE INDEX IX_Example
        ON YourTable (YourColumn)
        WITH (ALLOW_PAGE_LOCKS = ON);

<br>

> [!NOTE]
> 📝
> When you set `ALLOW_PAGE_LOCKS` to `ON`, it doesn't mean that only page-level locks will be used; rather, it allows the *Database Engine to use **page-level locks** when it deems it appropriate*.

<br><br>

> [!IMPORTANT]
> 🚩
> By default, SQL Server uses a combination of **row-level locks** and **page-level locks** based on its internal algorithms. It's important to note that the SQL Server query optimizer might override the setting based on its own assessment of the workload and performance considerations.
