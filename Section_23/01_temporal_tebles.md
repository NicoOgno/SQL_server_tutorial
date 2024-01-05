# $${\color{orange}Temporal\space Tables}$$

## Temporal Tables

This feature *enables you to query and retrieve data as it existed at different points in time* without creating complex structures or managing history tables manually.

**`Temporal Tables`** consist of two separate tables:

1. **Current Table:** This table holds the current data. It *represents the current state of the data* without any historical information.

2. **History Table:** This table keeps track of the changes made to the data in the current table. It *maintains historical records of every change made to the current table*.

<br>

Example:

    -- Create a temporal table
    CREATE TABLE dbo.Employee
    (
        EmployeeID INT PRIMARY KEY CLUSTERED,
        Name NVARCHAR(100),
        Department NVARCHAR(100),
        ValidFrom datetime2 GENERATED ALWAYS AS ROW START,
        ValidTo datetime2 GENERATED ALWAYS AS ROW END,
        PERIOD FOR SYSTEM_TIME (ValidFrom, ValidTo)
    )
    WITH (SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.EmployeeHistory));

In this example, the `dbo.Employee table` is the **`current table`**, and the `dbo.EmployeeHistory table` is the associated **`history table`**. When you enable system versioning using `SYSTEM_VERSIONING = ON`, SQL Server generates and manages these `tables` to maintain `historical data`.

<br><br>

### Creating Temporal Tables

    -- Create a regular table (current table)
    CREATE TABLE dbo.MyTable
    (
        ID INT PRIMARY KEY CLUSTERED,
        Name NVARCHAR(50),
        ValidFrom datetime2 GENERATED ALWAYS AS ROW START,
        ValidTo datetime2 GENERATED ALWAYS AS ROW END,
        PERIOD FOR SYSTEM_TIME (ValidFrom, ValidTo)
    );

    -- Create history table linked to the current table
    CREATE TABLE dbo.MyTableHistory
    (
        ID INT,
        Name NVARCHAR(50),
        ValidFrom datetime2,
        ValidTo datetime2,
        PERIOD FOR SYSTEM_TIME (ValidFrom, ValidTo)
    ) 
    WITH (SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.MyTableHistory));

<br><br>

### Enabling Temporal Table

    -- Enable system versioning on the main table
    ALTER TABLE dbo.MyTable
        ADD PERIOD FOR SYSTEM_TIME (ValidFrom, ValidTo);

    -- Connect the history table to the main table for system versioning
    ALTER TABLE dbo.MyTable
        SET (SYSTEM_VERSIONING = ON (HISTORY_TABLE = dbo.MyTableHistory));

<br><br>

### Managing Data in Temporal Tables

Once the `temporal tables` *are created and enabled, data manipulation is similar to regular tables*:

    -- Insert data into the current table
    INSERT INTO dbo.MyTable (ID, Name, ValidFrom, ValidTo)
    VALUES (1, 'John Doe', '2023-01-01', '9999-12-31'); -- ValidTo with a future date signifies the current row

    -- Update data in the current table
    UPDATE dbo.MyTable
    SET Name = 'Jane Doe'
    WHERE ID = 1;

    -- Query data from the temporal table for a specific point in time
    SELECT *
    FROM dbo.MyTable
    FOR SYSTEM_TIME AS OF '2023-06-01'
    WHERE ID = 1;


<br><br>

> [!NOTE]
> 📝
> `Temporal Tables` *simplify the process of managing historical data by automatically tracking changes*. It's important to note that this feature is supported in SQL Server editions starting from *SQL Server 2016* (Enterprise, Standard, and Developer editions).