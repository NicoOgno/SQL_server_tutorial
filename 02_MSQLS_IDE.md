# Microsoft SQL Server Management IDE

### Object explorer:

- Here is the structure and you projects.

- Click the pin in the top right corner to `Auto Hide`

### Create new project

1. Open new `SQLQuery window`

2. In Solution Explorer right click at the top in `Solution` "your solution".

3. Click Add ➡️ New Project.

4. Select `SQL Server Scripts`, give a name for your project and click OK. This will create a project with three files: `Connections`, `Queries` and `Miscellaneous`.

5. Close the inicial `SQLQuery window`, then go to the file `Queries` in your project and give right click and choose *New Query*, this will create a new `.sql` file.

### Create a Solution

- A Solution may have 1 or more projects

1. Go to File in the left top corner, click New ➡️ Project.

2. Select **SQL Server Management Studio Solution** (`Blanck Solution`)

3. Give a name for your solution and a path, and click OK.

4. In **Solution Explorer** right click on Solution Add ➡️ New Project.

5. Select `SQL Server Script`.

6. Give a name to your project and click OK. The new project will be reflected in the **Solution Explorer** sidebar.

7. Create a new connection in **Connections**, just enter your password.

8. In **Queries** right click `New Query`

### Skip authentication in IDE after opening a solution

1. Erase the default connection in folder **Connections**.

2. Then right click in folder **Connections** and select new connection. In Server Name write `.\`, enter your password in Password input and click ok.
