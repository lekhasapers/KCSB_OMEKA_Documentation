# Maintenance and Troubleshooting


## Keeping the LAMP Stack Updated

To ensure the LAMP stack remains secure and compatible with Omeka S, follow these steps to keep your system and software updated:

### Update Package Lists

```sh
sudo apt update
```

### Upgrade Installed Packages

```sh
sudo apt upgrade
```

### Full Distribution Upgrade

```sh
sudo apt dist-upgrade
```

### Version Control Maintenance

Ensure appropriate versions for Apache, MySQL, PHP:

```sh
sudo apt install apache2 mysql-server php
```

Check for specific version updates:

- Apache:

  ```sh
  apache2 -v
  ```

- MySQL:

  ```sh
  mysql --version
  ```

- PHP:

  ```sh
  php -v
  ```

### Configure Automatic Security Updates

Install `unattended-upgrades` package:

```sh
sudo apt install unattended-upgrades
```

Enable automatic updates:

```sh
sudo dpkg-reconfigure --priority=low unattended-upgrades
```

By following these guidelines, KCSB’s Omeka LAMP stack will remain up to date and secure, minimizing the risk of deprecation and ensuring continued compatibility with Omeka S.

_____ 

# Backing Up Omeka S
____

## Overview

Backing up Omeka S involves two main components:
1. **Omeka S Files**: This includes the application files, configuration files, themes, plugins, and uploaded files.
2. **Database**: Omeka S uses a database (typically MySQL) to store all metadata, settings, and relationships.

Both components must be backed up regularly to ensure a complete and restorable backup.

## Prerequisites

- Access to the server where Omeka S is installed.
- Administrative privileges to access files and databases.
- Basic knowledge of command-line operations

### Step 1: Backing Up Omeka S Files

#### Manual Backup

 **Connect to Your Server**: Use SSH to connect to your server. I've been using 'archives@128.111.126.136', but I'm not sure if you're on the same computer, so you may have to set that up on your own. 

   ```sh
   ssh username@your-server-ip
   ```

 **Navigate to the Omeka S Directory**: Locate the directory where Omeka S is installed.

   ```sh
   cd /var/www/html/omeka-s
   ```

 **Create a Compressed Archive**: Use the `tar` command to create a compressed archive of the Omeka S directory.

   ```sh
   tar -czvf omeka-s-backup-$(date +%F).tar.gz .
   ```

   This command creates a tar.gz file named with the current date.

 **Move the Backup File**: Move the backup file to a safe location.

   ```sh
   mv omeka-s-backup-$(date +%F).tar.gz /path/to/backup/location
   ```

#### Automated Backup (Using a Cron Job)

 **Create a Backup Script**: Create a shell script to automate the backup process.

   ```sh
   nano backup-omeka-s.sh
   ```

   Add the following content to the script:

   ```sh
   #!/bin/bash
   BACKUP_DIR="/path/to/backup/location"
   OMEKA_DIR="/path/to/omeka-s"
   TIMESTAMP=$(date +%F)
   tar -czvf $BACKUP_DIR/omeka-s-backup-$TIMESTAMP.tar.gz -C $OMEKA_DIR .
   ```

   Save and close the file.

 **Make the Script Executable**:

   ```sh
   chmod +x backup-omeka-s.sh
   ```

**Create a Cron Job**: Open the crontab editor.

   ```sh
   crontab -e
   ```

   Add the following line to schedule the backup script to run daily at midnight:

   ```sh
   0 0 * * * /path/to/backup-omeka-s.sh
   ```

### Step 2: Backing Up the Database

#### Manual Backup

 **Dump the Database**: Use the `mysqldump` command to create a backup of the Omeka S database.

   ```sh
   mysqldump -u username -p omeka_database > omeka-db-backup-$(date +%F).sql
   ```

   Enter your MySQL password when prompted.

 **Move the Backup File**: Move the SQL file to a safe location.

   ```sh
   mv omeka-db-backup-$(date +%F).sql /path/to/backup/location
   ```

#### Automated Backup (Using a Cron Job)

 **Create a Database Backup Script**: Create a shell script to automate the database backup process.

   ```sh
   nano backup-omeka-db.sh
   ```

   Add the following content to the script:

   ```sh
   #!/bin/bash
   BACKUP_DIR="/path/to/backup/location"
   DB_USER="username"
   DB_PASS="password"
   DB_NAME="omeka_database"
   TIMESTAMP=$(date +%F)
   mysqldump -u $DB_USER -p$DB_PASS $DB_NAME > $BACKUP_DIR/omeka-db-backup-$TIMESTAMP.sql
   ```

   Save and close the file.

 **Make the Script Executable**:

   ```sh
   chmod +x backup-omeka-db.sh
   ```

 **Create a Cron Job**: Open the crontab editor.

   ```sh
   crontab -e
   ```

   Add the following line to schedule the database backup script to run daily at 1 AM:

   ```sh
   0 1 * * * /path/to/backup-omeka-db.sh
   ```

### Step 3: Verifying Backups

 **List Backup Files**: Check the backup location to ensure the files are created.

   ```sh
   ls /path/to/backup/location
   ```

 **Test Restoration**: Periodically test the restoration process to ensure backups are valid and complete.


Regularly backing up your Omeka S installation is critical for data integrity and disaster recovery. By following the steps outlined in this documentation, you can ensure that both your files and database are safely backed up and can be restored if needed.
