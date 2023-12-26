# $${\color{orange}Database\space and\space Table\space with\space TransactSQL 📋}$$

### $${\color{green}Create\space Database\space with\space TransactSQL}$$

1. Open `🗒️New Query` window

2. Type in window:

       CREATE DATABASE DatabaseName
and `▶ Execute`

3. In *Object Explorer* right click Databases ➡️ *Refresh*, and you'll see the new DB added ✨.

<br><br>

### $${\color{green}Create\space Table\space with\space TransactSQL}$$

1.  in `Query` window type:

        CREATE TABLE Paciente(
          IdPaciente int NOT NULL,
          Nombre varchar(50) NOT NULL,
          Apellido varchar(50) NOT NULL,
          FNacimiento date NULL,
          Domicilio varchar(50) NULL,
          IdPais char(3) NULL,
          Telefono varchar(20) NULL,
          Email varchar(30) NULL,
          Observacion varchar(1000) NULL,
          FechaAlta datetime NOT NULL
          
          CONSTRAINT PK_IdPaciente PRIMARY KEY (IdPaciente)
        )
    and `▶ Execute`

<br>

> [!NOTE]
> 📝
> The reserved word *CONSTRAINT* is a condition, by convention PK_ is prefixed (PK_IdPaciente), and the reserved word *Primary Key* sets IdPaciente as the `PK` 🗝️.

2. Then Refresh `Databases` in *Object Explorer* go to the table and check it out with ➡️ *`Design`*

<br><br>

**Assign `Identity Specification` Example:**

    CREATE TABLE Pago (
      IdPago int IDENTITY (1,1) NOT NULL PRIMARY KEY,
      Concepto tinyint NOT NULL,
      Fecha datetime NOT NULL,
      Monto money NOT NULL,
      Estado tinyint,
      Obs varchar(1000)
    )

<br><br>

**Composed `PK` Table Example:**

    CREATE TABLE PagoPaciente (
      IdPago int NOT NULL,
      IdPaciente int NOT NULL,
      IdTurno int NOT NULL

      PRIMARY KEY (IdPago, IdPaciente, IdTurno)
    )

<br><br>

**Composed `PK` Table with `CONSTRAINT` Example:**

    CREATE TABLE MedicoEspecialidad (
      IdMedico int NOT NULL,
      IdEspecialidad int NOT NULL,
      Descripcion varchar(50) NOT NULL

      CONSTRAINT PK_MedicoEspecialidad PRIMARY KEY (IdMedico, IdEspecialidad)
    )