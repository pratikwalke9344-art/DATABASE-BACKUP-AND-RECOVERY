# DATABASE-BACKUP-AND-RECOVERY
*COMPANY :* CODETECH IT SOLUTION

*NAME :* WALKE PRATIK BABU

*INTERN ID :* CTIS4099

*DOMAIN :* SQL

*DURATION :* 4 WEEEKS

*MENTOR :* NEELA SANTHOSH KUMAR

This task demonstrates how to back up and restore the prtkintern database in MySQL. Backup and recovery are essential operations in database management, ensuring that data can be preserved against accidental loss, corruption, or system failure. The process involves exporting the database contents into a backup file and later restoring it to recreate the database in its original state. This task highlights both manual and automated approaches to backup and recovery.

1. Exiting MySQL Shell
Before running backup commands, exit the MySQL shell to return to the Windows command prompt:

       exit;
   
1. Creating a Backup
Use the mysqldump utility to export the database into a .sql file:
bash

       "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqldump.exe" -u root -p prtkintern >
       
       "C:\Users\prati\prtkintern_backup.sql"
       
Prompts for the root password.
Creates **prtkintern_backup.sql** containing schema and data.
This file can be stored securely or versioned in GitHub.

3. Verifying Backup File
Open the backup file to confirm it contains CREATE TABLE and INSERT INTO statements:

bash

      notepad "C:\Users\prati\prtkintern_backup.sql"

4. Simulating Failure (Optional)
To test recovery, drop the database:
bash

      "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p -e "DROP DATABASE prtkintern;"
      
5. Recreating Database
Create a fresh empty database:
bash

      "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p -e "CREATE DATABASE prtkintern;"

6. Restoring Database
Import the backup file into the new database:
bash

      "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p prtkintern <                        
      "C:\Users\prati\prtkintern_backup.sql"
      
7. Verifying Recovery
Log back into MySQL and check tables:
bash

      "C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p
      
Inside MySQL shell:
sql

      USE prtkintern;
      SHOW TABLES;
      SELECT * FROM job_seekers;
      
8. Automating Backup and Recovery
Create batch scripts for convenience:
backup.bat

bat
"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqldump.exe" -u root -p prtkintern > "C:\Users\prati\prtkintern_backup.sql"
restore.bat

bat
"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" -u root -p prtkintern < "C:\Users\prati\prtkintern_backup.sql"
Double‑clicking these files will run backup or restore automatically.
