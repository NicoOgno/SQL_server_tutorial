# $${\color{orange}Transactions}$$

### BEGIN TRANSACTION

`BEGIN TRANSACTION statement` is used to start a new transaction. Transactions in SQL are used to group one or more `SQL statements` into a single unit of work that is executed as a whole. If any part of the transaction fails, the entire transaction can be *rolled back to its starting point*.

    -- Start a new transaction
    BEGIN TRAN;

    -- Your SQL statements go here
    UPDATE your_table_name
    SET column1 = 'new_value'
    WHERE column2 = 'condition';

    -- If everything is successful, commit the transaction
    COMMIT TRAN;

- **BEGIN TRANSACTION** initiates the start of a new transaction.
- Your `SQL statements` follow the `BEGIN TRANSACTION statement`.
- If all statements within the transaction are successful, you can commit the transaction using `COMMIT TRANSACTION`. This makes all changes permanent.
- *If there is an issue or an error occurs*, you can roll back the transaction using `ROLLBACK TRANSACTION`. This undoes all changes made within the transaction.

Here's an example with a rollback:

    -- Start a new transaction
    BEGIN TRAN;

    -- Your SQL statements go here
    UPDATE your_table_name
    SET column1 = 'new_value'
    WHERE column2 = 'condition';

    -- If there is an error, roll back the transaction
    ROLLBACK TRAN;

> [!NOTE]
> 📝
> `Transactions` are essential for maintaining the consistency and integrity of your database when multiple operations need to be executed together as a single unit of work.