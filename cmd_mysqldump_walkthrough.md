<h1>MySQL Command Line & Database Backups with mysqldump Demo Walk-through (Windows)</h1>

First locate the file mysqldump.exe in the MySQL Server ‘bin’ (binary files) directory:

<img src= "https://github.com/hanoconnor/cfg-data-sql/blob/main/walkthrough_media/mysqlserver_bin_directory.png" />

Open a Command Prompt window (zoom in using Ctrl + Scroll)
Note: the ‘cls’ command can be used to clear previous commands/outputs.

 

Change directory to the directory containing the mysqldump.exe file:
cd C:\Program Files\MySQL\MySQL Server 8.0\bin\

<img src= "https://github.com/hanoconnor/cfg-data-sql/blob/main/walkthrough_media/cd_bin.png" />

Use the ‘dir’ command to show files within the directory to verify mysqldump.exe is located within the directory

<h2>Create a backup using mysqldump</h2>
mysqldump -h 127.0.0.1 -u root -p bakery > C:\Users\username\OneDrive\Desktop\backups\bakery_backup.sql

Change directory and use dir to show backup sql file has been created:

cd C:\Users\username\OneDrive\Desktop\backups\

dir

<h2>Demo MySQL databases in CLI</h2>
Change directory to directory containing the mysql binary files:
cd C:\Program Files\MySQL\MySQL Server 8.0\bin\

First log into MySQL using root user account (enter password flag only – remember security first):
mysql -u root -p

Enter root password when prompted.

Once mysql> prompt appears you can use usual MySQL syntax to demo databases and queries:

Show databases present: show databases;
Select database to use: use bakery;

 <img src= "https://github.com/hanoconnor/cfg-data-sql/blob/main/walkthrough_media/show_dbs.png" />

Demonstrate tables within the database: show tables;
Demonstrate data is present using query: select * from sweet;

Drop database: drop database bakery;
Show databases to confirm table has been dropped and no longer appears in schema list.
Re-create database to restore backup to: create database bakery; 
Select db: use bakery;
Demonstrate empty set to show no tables present: show tables;
Exit (to quit mysql)


<h2>Restore from bakery backup file</h2>

If not authenticated:
mysql -h 127.0.0.1 -u root -p bakery < C:\Users\username\OneDrive\Desktop\backups\bakery_backup.sql

<img src= "https://github.com/hanoconnor/cfg-data-sql/blob/main/walkthrough_media/restore_db.png" />

<b>OR</b> from within mysql prompt (if already authenticated):
use bakery;
source C:\Users\username\Desktop\backups\bakery_backup.sql

Show tables and queries to confirm backup has successfully restored tables and data:

<img src = "https://github.com/hanoconnor/cfg-data-sql/blob/main/walkthrough_media/show_tables.png" />
 
 
You can also check in MySQL Workbench to confirm successful restore.
NOTE: Remember to ALWAYS test database backups!
