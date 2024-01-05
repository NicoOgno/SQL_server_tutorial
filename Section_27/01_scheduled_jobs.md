# $${\color{orange}Database\space Backup\space and\space Restore}$$

## Scheduled Jobs

 You can create scheduled jobs using *SQL Server Agent* to automate various tasks such as running queries, executing stored procedures, performing backups, sending notifications, and more.

 ### Creating a Scheduled Job

 <br>

 1. **Create a New Job:**

        USE msdb;
        GO

        EXEC dbo.sp_add_job
          @job_name = N'YourJobName',
          @enabled = 1,
          @description = N'Your job description';

2. **Add a Job Step:**

        EXEC dbo.sp_add_jobstep
          @job_name = N'YourJobName',
          @step_name = N'YourStepName',
          @subsystem = N'TSQL',
          @command = N'YourTSQLCommandHere';

3. **Schedule the Job:**

        EXEC dbo.sp_add_schedule
          @schedule_name = N'YourScheduleName',
          @freq_type = 4, -- 4 indicates daily; change as needed for other frequencies
          @freq_interval = 1, -- Daily frequency interval
          @active_start_time = 100000, -- Specify the time (HHMMSS format)
          @schedule_id = 1; -- Assign a schedule ID

This example schedules a daily job that starts at 10:00 AM.

4. **Attach the Schedule to the Job:**

        EXEC dbo.sp_attach_schedule
          @job_name = N'YourJobName',
          @schedule_name = N'YourScheduleName';

Associate the previously *created schedule* (`YourScheduleName`) with your *job* (`YourJobName`).

5. **Start the Job:**

        EXEC dbo.sp_start_job N'YourJobName';

Initiate the job manually if you want it to run immediately.

<br>

> [!NOTE]
> 📝
> *SQL Server Agent* permissions are needed to perform these operations.

<br>

> [!WARNING]
> 👁️
> Remember to carefully plan and test your `scheduled jobs` to ensure they function as intended and don't interfere with other processes in your environment.

<br><br>

### Creating a Scheduled Job throigh the Object Explorer

1. In *Object Explorer* ➡️ *`SQL Server Agent`* right click on *`Jobs`* ➡️ *`New Job`*

2. Give a *name* to the *job*, then click on ***`Steps`*** at the sidebar and click *New..* at the bottom.

3. Give a *name* to the *step* keep the type: *`Transact-SQL script(T-SQL)`*

4. Choose the DB you want to make the *steps* on.

5. In the `text area` *Command:* write the code you want to be executed, and give *OK*.

6. Go to ***`Schedules`*** in the sidebar, and in this new window click *New...* at the bottom.

7. Give a *name* to the *schedule*.

8. Choose your *Schedule type:*.

9. Set *frequency* and *duration*.

10. You may set an *alert*, to do that go to *`Alert`* in the sidebar and set it.

11. Finally givo *OK* to save 💾 your *job* 