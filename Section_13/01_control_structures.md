# $${\color{orange}Control\space Structures}$$

### IF

**`IF statements in SQL`** are used for conditional logic.

    IF condition
      BEGIN
          -- Statements to execute if the condition is true
      END


For instance, if you want to check if a certain value is greater than 10:

    DECLARE @value INT
    SET @value = 15

    IF @value > 10
      BEGIN
          PRINT 'The value is greater than 10'
      END

Remember that the exact syntax can vary depending on the `SQL database system` you are using (e.g., `MySQL`, `PostgreSQL`, `SQL Server`). The example above is written in `Transact-SQL` (`T-SQL`), which is used in `Microsoft SQL Server`.

> [!TIP]
> 🧠
> Use `command T` to see text types as results, for example using print in `T-SQL`.

The `IF statement` only runs the next line of code if it's `TRUE`, you must specify wich part of the code you want to run for the `IF statement` using `BEGIN END`.

<br>

### BEGIN END

In SQL, `BEGIN` and `END` are used to *group multiple statements into a block*. This block can be part of a conditional statement (`IF`) or a loop (`WHILE`, `FOR`, etc.), or it can simply be an independent code block.

    BEGIN
        -- SQL statements go here
        SELECT column1, column2
        FROM table_name
        WHERE condition;

        UPDATE another_table
        SET column = value
        WHERE another_condition;

        -- You can have more statements here
    END;

The `BEGIN` indicates the start of the block, and `END` indicates its end. All `SQL statements` between `BEGIN` and `END` are executed as a unit. This is especially useful when you need to execute multiple statements together as part of more complex logic or a transaction.

> [!TIP]
> 🧠
> Always **indent** your code for better readibility.

<br>

> [!NOTE]
> 📝
>  In some cases, such as in a `BEGIN...END` block inside a `stored procedure`, it's not necessary to use `BEGIN` and `END` if there's only one statement inside the block. However, it's a good practice to include them always for clarity and code maintenance.

<br>

### ELSE

In SQL, the `ELSE` keyword is used in conjunction with the `IF statement` to specify a block of statements to be executed if the condition specified in the `IF statement` is not true.

    IF condition
    BEGIN
        -- Statements to execute if the condition is true
    END
    ELSE
    BEGIN
        -- Statements to execute if the condition is false
    END

For instance:

    DECLARE @value INT
    SET @value = 5

    IF @value > 10
    BEGIN
        PRINT 'The value is greater than 10'
    END
    ELSE
    BEGIN
        PRINT 'The value is not greater than 10'
    END

In this example, if `@value` is greater than 10, it will print the first message; otherwise, it will print the second message. The `ELSE block` is optional; *if it's not provided, nothing will be executed when the condition is false*.

<br>

### EXISTS

In SQL, the `EXISTS keyword` is used in a `SELECT statement` to check for the existence of rows that meet a specified condition. It is often used in conjunction with a correlated `subquery` or as part of a `conditional expression`.

    IF EXISTS (SELECT 1 FROM your_table WHERE your_condition)
    BEGIN
        -- Statements to execute if the condition is true
        PRINT 'Rows exist that meet the specified condition.'
    END
    ELSE
    BEGIN
        -- Statements to execute if the condition is false
        PRINT 'No rows found that meet the specified condition.'
    END

In this example, the `EXISTS clause` checks if there are any rows in the `your_table` table that satisfy the specified `condition (your_condition)`. If such rows exist, the statements inside the `IF block` will be executed; otherwise, the statements inside the `ELSE block` will be executed.

<br>

> [!NOTE]
> 📝
> The key point is that it returns either `TRUE` or `FALSE` based on whether any rows are returned by the `subquery`.

<br>

### WHILE

In SQL, the `WHILE statement` is used to create a *loop that repeatedly executes a block of `SQL statements` as long as a specified condition is true*.

    DECLARE @counter INT = 1;

    WHILE @counter <= 10
    BEGIN
        -- Statements to execute while the condition is true
        PRINT 'Counter: ' + CAST(@counter AS VARCHAR);

        -- Increment the counter
        SET @counter = @counter + 1;
    END;


In SQL, the WHILE statement is used to create a loop that repeatedly executes a block of SQL statements as long as a specified condition is true. The basic syntax is as follows:

sql
Copy code
DECLARE @counter INT = 1;

WHILE @counter <= 10
BEGIN
    -- Statements to execute while the condition is true
    PRINT 'Counter: ' + CAST(@counter AS VARCHAR);

    -- Increment the counter
    SET @counter = @counter + 1;
END;

In this example, the `WHILE loop` continues executing the statements inside the `BEGIN` and `END block` as long as the `@counter` is less than or equal to 10. The `PRINT statement` is used to display the current value of the counter.

<br>

> [!NOTE]
> 📝
> It's important to include logic to modify the condition inside the loop (such as incrementing a counter or updating a variable) to avoid an infinite loop.

> [!TIP]
> 🧠
> `WHILE` loops can be useful for scenarios where you need to repeatedly perform a set of actions until a certain condition is met. If you make an *infinite loop* you can break it by clicking the **stop button** in the top of the IDE where the `▶ Execute` was before.

<br>

### CASE

In SQL, the `CASE statement` is used for *conditional logic*, allowing you to perform different actions based on different conditions.

    CASE
        WHEN condition1 THEN result1
        WHEN condition2 THEN result2
        ...
        WHEN conditionN THEN resultN
        ELSE elseResult
    END

<br>

Here's an example to illustrate the usage of the `CASE statement`:

DECLARE @score INT = 85;
DECLARE @grade VARCHAR(2);

    SET @grade = 
        CASE
            WHEN @score >= 90 THEN 'A'
            WHEN @score >= 80 THEN 'B'
            WHEN @score >= 70 THEN 'C'
            WHEN @score >= 60 THEN 'D'
            ELSE 'F'
        END;

    PRINT 'The grade is: ' + @grade;

In this example, the `CASE statement` checks the value of `@score` and assigns a corresponding grade based on different score ranges.

<br>

> [!NOTE]
> 📝
> *The conditions are evaluated in order*, and the *first condition that is true will determine the result*. **If none of the conditions are true, the `ELSE clause` provides a default result**.

<br>

### RETURN

In SQL, the *`RETURN statement` is primarily used within `stored procedures` or `user-defined functions` to exit the procedure or function and return a value to the caller*. Its exact usage depends on the context.

    CREATE PROCEDURE ExampleProcedure
    AS
    BEGIN
        -- Your SQL statements here

        IF (/* Some condition */)
        BEGIN
            -- Additional logic

            -- Return a specific value and exit the procedure
            RETURN 1;
        END

        -- More statements can follow here

    END;

In this example, if a certain condition is met, the `stored procedure` will return the value `1` and terminate. The *`RETURN statement` is useful when you want to exit early from a `stored procedure` or `function` based on a condition*.

<br>

### BREAK

In SQL, the `BREAK statement` is not used as a standalone keyword like `RETURN`. Instead, it *is typically used in conjunction with looping constructs*, such as `WHILE` or `FOR`, to exit the loop prematurely based on a certain condition.

Here is an example using `BREAK` within a `WHILE` loop:

    DECLARE @counter INT = 1;

    WHILE @counter <= 10
    BEGIN
        -- Some statements

        IF @counter = 5
        BEGIN
            -- Exit the loop when counter is 5
            BREAK;
        END

        -- More statements

        SET @counter = @counter + 1;
    END;

In this example, the `BREAK statement` is used to exit the `WHILE loop` when the value of `@counter` becomes 5.

<br>

> [!NOTE]
> 📝
> Keep in mind that the use of `BREAK` may vary depending on the specific `SQL database system` you are working with.

<br>

### TRY CATCH

In SQL Server, the `TRY...CATCH block` is used for **error handling** within a `T-SQL` (`Transact-SQL`) `batch`, `stored procedure`, `trigger`, or `dynamic SQL`. *It allows you to catch and handle errors that occur during the execution of a group of statements*.

    BEGIN TRY
        -- Statements that might cause an error
        -- ...

    END TRY
    BEGIN CATCH
        -- Handling the error
        -- ...

    END CATCH;

<br>

Here's an example to illustrate the usage:

    BEGIN TRY
        -- Statements that might cause an error
        DECLARE @result INT = 10 / 0; -- Division by zero to trigger an error

    END TRY
    BEGIN CATCH
        -- Handling the error
        PRINT 'An error occurred: ' + ERROR_MESSAGE();

        -- Additional error handling logic can be added here

    END CATCH;

In this example, if the division by zero occurs, the error is caught by the `CATCH block`, and the error message is printed. You can replace the `PRINT statement` with other error-handling logic, such as logging the error, rolling back transactions, or raising a custom error.

<br>

> [!TIP]
> 🧠
> The `TRY...CATCH block` is a powerful tool for handling errors in a controlled manner, and it's especially useful in scenarios where you want to gracefully handle errors and avoid abrupt termination of the script or procedure.