# $${\color{orange}Triggers}$$

## Trigger

`Trigger` is a *special type of `stored procedure` that automatically executes in response to certain events occurring in a `database`*. Triggers are associated with specific tables and are triggered when specific data manipulation language (DML) operations, such as ***`INSERT`, `UPDATE`, `DELETE`***, are performed on those `tables`.

There are *two main types* of `triggers` in `T-SQL`:

1. **After Triggers** (`AFTER INSERT, UPDATE, DELETE`): these `triggers` execute after the triggering event (`insert, update, delete`) occurs on the `table`. They are commonly used to perform actions after data changes have been made.

2. **Instead Of Triggers** (`INSTEAD OF INSERT, UPDATE, DELETE`): these triggers execute instead of the triggering event. *They can be used to modify the action that would have occurred* (`insert, update, delete`) on the table.

<br><br>

Creating an **`AFTER INSERT trigger`** in `T-SQL`:

    CREATE TRIGGER trgAfterInsert
    ON YourTableName
    AFTER INSERT
    AS
    BEGIN
        -- Actions to perform after an INSERT operation on YourTableName
        -- You can access the inserted data using the "inserted" table
        -- Example: 
        -- INSERT INTO AnotherTable (Column1, Column2)
        -- SELECT ColumnA, ColumnB FROM inserted;
    END;

- **`trgAfterInsert`** is the name of the trigger.
- **`YourTableName`** is the name of the table associated with the trigger.
- **`AFTER INSERT`** specifies that the trigger will be fired after an INSERT operation on the table.

Within the `trigger body` (`BEGIN and END block`), *you can define the actions you want to perform after the triggering event occurs*. *Triggers have access to special tables like inserted and deleted*, which hold the affected data during `INSERT`, `UPDATE`, or `DELETE` operations. These tables can be used within the trigger to access the affected data.

<br><br>

Creating an **`INSTEAD OF INSERT trigger`** in `T-SQL`:

    CREATE TRIGGER trgInsteadOfInsert
    ON YourTableName
    INSTEAD OF INSERT
    AS
    BEGIN
        -- Actions to perform instead of the INSERT operation on YourTableName
        -- You can access the inserted data using the "inserted" table
        -- Example:
        -- INSERT INTO YourTableName (Column1, Column2)
        -- SELECT ColumnA, ColumnB FROM inserted;
    END;

- **`trgInsteadOfInsert`** is the name of the trigger.
- **`YourTableName`** is the name of the table associated with the trigger.
- **`INSTEAD OF INSERT`** specifies that the trigger will replace the default INSERT operation on the table.

Within the `trigger body` (`BEGIN and END block`), you can define the custom actions you want to perform instead of the regular `INSERT operation`. The `inserted table` contains the data that would have been inserted, allowing you to modify it or perform additional checks before inserting data into the table.

Similarly, you can create `INSTEAD OF triggers` for `UPDATE` or `DELETE operations` by replacing `INSTEAD OF INSERT` with `INSTEAD OF UPDATE` or `INSTEAD OF DELETE` respectively.

<br>

> [!NOTE]
> 📝
> To *modify or drop triggers, you can use the `ALTER TRIGGER` or `DROP TRIGGER statements`* respectively.

<br>

> [!WARNING]
> 👁️
> Always test triggers thoroughly to ensure they behave as expected and *don't adversely affect the system's performance or data integrity*.