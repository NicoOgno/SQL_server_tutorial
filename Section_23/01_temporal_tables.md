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

**Temporal attributes** (`ValidFrom`, `ValidTo`, and `PERIOD FOR SYSTEM_TIME`).

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

<br><br>

### In-memory Temporal Tables

- This tables are destroyed after running the script.

- When declaring an in-memory temporal table use `@`, example:

      DECLARE @MyTable TABLE (id int IDENTITY(1,1), columnName varchar(50))

      INSERT INTO @MyTable VALUES('Spaghetti')
      INSERT INTO @MyTable VALUES('Pizza')
      INSERT INTO @MyTable VALUES('Bananas')

      SELECT * FROM @MyTable


### Physical Temporal Tables

- This tables will be available as long as we don't restart the `Database Engine`.

- Is good practice to destroy the table after using it to liberate memory.

- When declaring physical temporal table use `#`, example:

      DECLARE #MyTable TABLE (id int IDENTITY(1,1), columnName varchar(50))

      INSERT INTO #MyTable VALUES('Spaghetti')
      INSERT INTO #MyTable VALUES('Pizza')
      INSERT INTO #MyTable VALUES('Bananas')

      SELECT * FROM #MyTable
      DROP TABLE #MyTable

<br><br>

### Why use Temporal Tables ?

There are several reasons why using `temporal tables` can be beneficial:

1. **Historical Data Tracking:** Temporal tables maintain historical information about changes made to data, allowing you to track the state of data at different points in time. This feature is particularly useful for compliance, auditing, and historical analysis purposes.

2. **Simplified Auditing:** With temporal tables, auditing becomes more straightforward as the history of changes is automatically managed. You can easily identify who made changes, when they were made, and what the previous values were without additional complex auditing mechanisms.

3. **Reconstructing Data History:** Temporal tables facilitate data reconstruction by providing a clear historical timeline. You can reconstruct the state of the data at any specific point in time or track the sequence of changes made to a particular record.

4. **Point-in-Time Analysis:** You can query temporal tables to retrieve data as it existed at a specific point in time, which is beneficial for generating reports or conducting analyses based on historical data.

5. **Efficient Data Comparison:** Temporal tables simplify the comparison of data changes between different points in time. You can easily identify what data changed and when, improving data analysis and troubleshooting.

6. **Easier Data Recovery:** In case of accidental data modifications or deletions, temporal tables allow for easier recovery by providing historical snapshots of data.

7. **Integration with Existing Applications:** Temporal tables integrate well with existing applications, allowing for seamless adoption of historical data management without significant changes to application logic.

<br>

Here is an example of *querying data from a `temporal table` to retrieve historical information*:

    -- Querying data from a temporal table for a specific point in time
    SELECT *
    FROM YourTemporalTable
    FOR SYSTEM_TIME AS OF '2023-06-01' -- Specify the timestamp to retrieve data as it was at that time
    WHERE YourCondition; -- Add any specific conditions if needed

<br>

> [!NOTE]
> 📝
> Temporal tables simplify the management of historical data and provide a convenient way to handle data changes over time, making them a valuable tool in database design and data management strategies.