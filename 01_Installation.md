# SQL Installation

### SQL Server Installation

<a href="https://www.microsoft.com/es-mx/sql-server/sql-server-downloads">SQL Server Developer</a>

**Steps:**

1. Select an installation type: select `Custom`. Then click `install`.

2. Go to `Installation` select `New SQL Server standalone installation or add features to an existing installation`.

3. Specify a free edition: *Developer*. Then click next.

4. Accept license terms and privacy statement. Then click next.

5. Microsoft Update: do ***not*** check the box. Then click next.

6. Screen with features and a warning, just click next.

7. Unselect `Azure Extension for SQL Server`. Then click next.

8. Select `SQL Server Replication`, `Full-text and Semantic Extractions for Search` and `Integration Services`. Then click next.

9. Let the Default instance. Then click next.

10. In Service `SQL Server Agent` change `Startup Type` to *automatic*. Then click next.

11. Select `Mixed Mode (SQL Server authentication and Window authentication)`, create a password and click `Add Current User`. Then click next.

12. Finally click install, after installation restart your machine.

**Check Installation:**

1. Search for `services` in your machine and check if you default SQL Server has the status Running example:

   "Name": SQL Server (MSSQLSERVER)
   "Status": Running

   "Name": SQL Server Agent (MSSQLSERVER)
   "Status": Running

2. If SQL Server or SQL Server Agent were not running, select them and click the green play button on the top left corner.

### SQL Server Management Studio Installation

<a href="https://learn.microsoft.com/es-es/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16">SQL Server Management Studio</a>

- Click Install and then restart your machine.

### Connecting with SQL Engine

1. Search for `ssms` in your machine, then right click on `Microsoft SQL Server Management Studio` and click Pin to taskbar.

2. Open `Microsoft SQL Server Management Studio`. In Connect to Server write in the *Server name* input `.\`, in Authentication select `SQL Server Authentication`, in Login write `sa` and then enter you password.