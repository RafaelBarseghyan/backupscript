## Script provides a comprehensive backup solution for MySQL databases with options for local and AWS S3 storage.


+ MySQL Authentication:
The script prompts the user to enter MySQL host, username, and password.
It attempts to connect to MySQL using the provided credentials to verify authentication.


+ Database Identification:
The user is prompted to enter the name of the database.
The script checks if the specified database exists.


+ Choice of Backup Folder in Local Server:
The user is prompted to enter the local backup folder path.
The script attempts to create the specified directory.

+ Choice of Compression Method:
The user is prompted to choose a compression type for the backup (gzip, bzip2, xz, lzma).

+ Database Backup in Local Server:
The script performs a MySQL dump of the specified database.
The backup file is compressed using the chosen compression method.

+ Remove Backups Older Than Specified Days:
Older backup files in the local server are removed based on a specified retention period.

+ Database Backup in AWS S3:
The user is prompted if they want to synchronize the database backup to an AWS S3 bucket.
If the user agrees, they provide the S3 bucket name and AWS profile username.
The script uses AWS CLI to sync the local backup folder with the specified S3 bucket.

+ Deleting Old Objects from AWS S3:
The user is prompted if they want to remove older backup files and objects from the AWS S3 bucket.
If the user agrees, they provide the number of days to keep objects in the S3 bucket.
The script uses AWS CLI to list and delete objects older than the specified days.

+ Script Completion:
The script prints a success message at the end.


### To start compressing and backup the database you must specify a few information shown below after running script

+ MYSQL_HOST - (Example - "localhost") 
+ MYSQL_USER (Example - "james" ) 
+ MYSQL_PASSWORD (Example - "mysqlpass" ) 
+ DB_BACKUP_PATH - database backup folder where you want to save compressed files (Example - "/home/james/databasebackups/" )
+ DATABASE_NAME - the name of the database you want to backup (Example database name - "Users" )
+ COMPRESSION_TYPE - (Example - "gzip" )

### To synchronize data between backup folder in local server and AWS S3 you must specify a few information shown below 

+ AWS_S3_BUCKET_NAME - (Example - "database.backups.aws.s3" )
+ AWS_USERNAME - (Example - "admin999" )
+ AWS Access Key ID
+ AWS Secret Access Key  
+ AWS Region - (Example - "eu-central-1")
+ BACKUP_DELDATE_FROM_AWS - (Example - "7" )

> Keep in mind that you must have the necessary acceses in
> + mysql server.
> + local server folder where you want to create your database backup files.
> + already created AWS user and S3 bucket (also you need AWS CLI v2).
