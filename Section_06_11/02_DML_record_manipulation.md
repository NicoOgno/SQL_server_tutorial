# $${\color{orange}DML\space Record\space Manipulation}$$

* **Create a Record:** right click on the table you want to insert a record then ➡️ *`Edit Top 200 Rows`*. After making a change in the table a red symbol will appear 🛑 that's because you have to commit your changes, to commit just press *Enter* or *Down Arrow/Up*.

* **Delete a Record:** in the window of *`Edit Top 200 Rows`* `right click` on the record you want to delete and click `Delete`.

<br>

> [!TIP]
> 🧠
> Right click on a table ➡️ `Select Top 1000 Rows`, it brings the first 1000 records from the table, and the script to make it in the `Query Window`.

<br><br>

🔹 **SELECT:** is the filter for the fields you want to see. Example:

    SELECT IdPaciente, nombre, apellido FROM Paciente

That will show the the values from the fields IdPaciente, nombre and apellido from the table Paciente.

INSERT INTO Paciente (DNI, Nombre, Apellido, FNacimiento, Domicilio, IdPais, Telefono, Email, Observacion)
VALUES ('123098', 'Leandro', 'Paredes', '1982-05-20', 'Piedras 150', 'ARG', NULL, 'leandro@gmail.com', '')
🔹 **INSERT:** creates records in the `Query window`. Exmple:

    SELECT * FROM Paciente

    INSERT INTO Paciente (DNI, Nombre, Apellido, FNacimiento, Domicilio, IdPais, Telefono, Email, Observacion)
   
    VALUES ('123098', 'Leandro', 'Paredes', '1982-05-20', 'Piedras 150', 'ARG', NULL, 'leandro@gmail.com', '')

<br>

> [!NOTE]
> 📝
> Always *specify the fields for the values you are entering*, that will help you *handle errors*. Don't put `IDENTITY` fields such as `IdPaciente` because **SSMS** increments it automatically.
> 
> To give an empty field use **''** and **NULL** for a null value.

<br><br>

### $${\color{green}INSERT\space Multiple\space Records}$$

    INSERT INTO Paciente (DNI, Nombre, Apellido, FNacimiento, Domicilio, IdPais, Telefono, Email, Observacion)
   
    VALUES ('323098', 'Gonzalo', 'Gonzalez', '1972-04-20', 'La Estancia 345', 'COL', NULL, 'gonza@gmail.com', 'Recuperación'),

    ('265981', 'Fernando', 'Fernandez', '1992-11-27', 'Málaga', 'MEX', NULL, 'donfer@gmail.com', 'Tratamiento')

* Just separete the records with a **comma**.

<br><br>

* Get the first 1000 records from a table Example (*IdEstado* and *Descripcion* are the fields displayed):

        SELECT TOP (1000) [IdEstado]
            ,[Descripcion]
        FROM [CentroMedico].[dbo].[TurnoEstado]