# $${\color{orange}First \space Database \space \ Design}$$

1.  Open **Microsoft SQL Server Manager**, in Object Explorer click on `Connect` ➡️ `Database Engine`, and enter the password in the prompt. It will open some folders in the Object Explorer.

2. In **Object Explorer** right click on Databases ➡️ New Database.

3. In the prompt give a name in the input `Database name` *without any special characters, punctuation or blank spaces.* (**PascalCase**)

4. Create a new folder in your machine (*Example: in `C:\` create folder SQLDATA and subfolder with the name of your DB.* Then change the path before creating the DB in SQL Server IDE for the DB and the DB_log, and give click on OK), make sure you know the location of the folder, `it will help you make backups when needed`.

5. A DB folder with the name of your DB will appear in the Object Explorer within the `Databases` folder.

<br><br>

### $${\color{green}.MDF \space and \space \ .LDF \space files}$$

**Master Data File**
- **DB.mdf:** here are saved the DB `objects`, `tables`, and `procedures`.

**Log Data File**
- **DB_log.ldf:** contains the transactions carried out in the database..