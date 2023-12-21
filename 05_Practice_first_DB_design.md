# $${\color{orange}First \space Database \space \ Design}$$

1.  Open **Microsoft SQL Server Manager**, in Object Explorer click on `Connect` 🔌 ➡️ `Database Engine`, and enter the password in the prompt. It will open some folders in the Object Explorer.

2. In **Object Explorer** right click on Databases ➡️ New Database.

3. In the prompt give a name in the input `Database name` *without any special characters, punctuation or blank spaces.* (**PascalCase**)

4. Create a new folder in your machine (*Example: in `C:\` create folder SQLDATA and subfolder with the name of your DB.* Then change the path before creating the DB in SQL Server IDE for the DB and the DB_log, and give click on 🆗), make sure you know the location of the folder, `it will help you make backups when needed`.

5. A DB folder with the name of your DB will appear in the Object Explorer within the `Databases` folder.

<br><br>

### $${\color{green}.MDF \space and \space \ .LDF \space files}$$

**Master Data File**
- **DB.mdf:** is the primary data file of a SQL Server database. It contains the `tables`, `indexes`, `stored procedures`, and other objects of the database.
**Log Data File**
- **DB_log.ldf:** is the transaction log file of a SQL Server database. It `records all transactions and changes made to the database`, `enabling recovery and restoration` in case of failures or data loss.

<br><br>

### $${\color{green}Opening\space a\space Script\space Window\space and\space Setting\space a\space Database\space as\space the\space Default}$$

🔹  In the buttons panel at the top click `🗒️New Query` or use the shortcut `Ctrl + N`

> [!TIP]
> 🧠
> When the Script window is open it handles by default the `Database *master*`, that's why is useful to have another Database as default.

> [!NOTE]
> 📝
> To handle a specific DB select it from the `List Box` on top of the *Object Explorer* component.

**Set as default:** in *Object Explorer* component go to Security ➡️ Logins, then click on your user (Example: sa) there will be a window with the user info, at the bottom of the window in *Default database* choose your DB. Then close any Query window you have open, disconnect MSQLServer and connect 🔌 again.

<br><br>

### $${\color{green}Defining\space a\space Table\space using\space the\space Table\space Designer}$$

- In *Object Explorer* right click on Table ➡️ New.

- In the table we give the `Column Name`, `Data Type` and set if `Nulls` are Allowed.

> [!NOTE]
> 📝
> In the tables the check box `Allow Nulls` is checked by default.

- To save the Table click the diskette 💾 in the buttons panel at the top and give a descriptive name. To see the table right click on Tables ➡️ Refresh.

- **dbo.DatabaseName:** `dbo.` is a schema established by default in every Table we create. In this folder is all the information about the Table.

<br><br>

### $${\color{green}Modify\space Existing\space Table}$$

🔹 Go to the table (example: dbo.DBName) right click on it and click *`Design`*, after changes are made save the new Table clicking the diskette 💾 in the buttons panel at the top.

> [!WARNING]
> 👁️
> When a Table is modified for the first time a Warning pop-up will appear. You need to allow permission to delete the old Table and generate the new one.

> [!IMPORTANT]
> 🚩
> To allow permission to modify Tables go to the *`Tools`* menu ➡️ ⚙️ options ➡️ *`Designers`* ➡️ *`Table and Database Designers`*, uncheck 🔲 `Prevent saving changes that require table re-creation`. Then give 🆗 and save the Table 💾.

<br><br>

### $${\color{green}Stablishing\space a\space Primary\space Key\space PK}$$

🔹 Go to the table (example: dbo.DBName) right click on it and click *`Design`*. Then select a field to be the `PK`, and click the button at the top right `Set Primary Key` 🗝️. The `PK` will be stored in the *keys* folder in the specific Table (dbo.DBName).

> [!NOTE]
> 📝
> `PK` fields don't allow nulls 🚫.

<br><br>

### $${\color{green}Stablishing\space Identity\space Property}$$

🔹 Go to the table (example: dbo.DBName) right click on it and click *`Design`*, select the field to be set as `Identity` (example: idSomething 👁️ **Must be of *Number type***). Then in the *Column Properties* component at the bottom in `Identity Specification` set `(Is Identity)` to Yes. This will make that each time a new registry is inserted in the Table this field will increment by one.

> [!TIP]
> 🧠
> We usually set the Identity to a field that is the Primary Key. This ensures that its value is not duplicated, generating unique records.

<br>

**Identity Arguments**

1.  **Seed:** Define from which value it starts incrementing its value.
> [!NOTE]
> 📝
> If the Seed value is 1, it will start incrementing from 1.
> If the Seed value is 5, it will start incrementing from 5.

<br>

2. **Increment:** is an increment.
> [!NOTE]
> 📝
> If the Increment value is 1, the field value will be saved with consecutive values e.g., 1, 2, 3, 4.
>If the Increment value is 2, the field value will be saved with alternate consecutive values e.g., 1, 3, 5, 7.

> [!TIP]
> 🧠
> To define a field with the Identity property (*Seed=1, Increment=2*) in **T-SQL**, we use:
> Example: `[fieldName] [int] IDENTITY(1,2)`.

<br><br>

**Example of a table with the Column IdPaciente *IDENTITY(1,2)* property.**

| IdPaciente | Nombre | IdPais | FechaNacimiento |
|--------|:----:|:--------:|-------:|
| 1 | Juan Carlos Ruber | ESP | 01-12-1990 |
| 3 | Carlos Andrés Montoya | MEX | 15-05-1978 |
| 5 | Juan Sanchez | MEX | 20-03-1992 |
| 7 | Juan Sanchez | MEX | 16-07-1992 |