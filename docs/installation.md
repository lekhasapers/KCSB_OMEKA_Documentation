# Installation

Running Omeka S on a LAMP backend architecture involves several steps, including installing and configuring each component of the stack and then installing Omeka S itself.

### 1. Install Elementary OS
- Install Elementary OS from the official website and follow the installation instructions.

### 2. Install Apache
- Install Apache HTTP Server:
  ```sh
  sudo apt update
  sudo apt install apache2
  ```

- Enable `mod_rewrite`:
  ```sh
  sudo a2enmod rewrite
  sudo systemctl restart apache2
  ```

- **Verification:** Open a web browser and navigate to `http://localhost`. This will prompt the Apache2 default welcome page.

### 3. Configure Firewall
- Allow HTTP and HTTPS traffic through the firewall:
  ```sh
  sudo ufw allow in "Apache Full"
  ```

### 4. Install MySQL
- Install MySQL Server:
  ```sh
  sudo apt install mysql-server
  sudo mysql_secure_installation
  ```

- Secure MySQL Installation:
  ```sh
  sudo mysql -u root -p
  ```

- Create a database and a user for Omeka-S:
  ```sql
  CREATE DATABASE omeka_s;
  CREATE USER 'omeka_user'@'localhost' IDENTIFIED BY 'password';
  GRANT ALL PRIVILEGES ON omeka_s.* TO 'omeka_user'@'localhost';
  FLUSH PRIVILEGES;
  EXIT;
  ```

- **Verification:** Log into MySQL and check the databases:
  ```sh
  sudo mysql -u root -p
  SHOW DATABASES;
  ```
  Ensure the Omeka-S database is listed.

### 5. Install PHP and Required Extensions
- Install PHP and required extensions:
  ```sh
  sudo apt install php libapache2-mod-php php-mysql php-json php-mbstring php-xml php-dom php-simplexml php-fileinfo php-curl php-gd
  ```

- **Verification:** Create a PHP File to verify installation:
  ```sh
  echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php
  ```
  Navigate to `http://localhost/info.php`, where the PHP information page will be visible.

### 6. Advanced PHP Configuration
- Adjust PHP settings for better performance:
  ```sh
  sudo nano /etc/php/7.4/apache2/php.ini
  ```
  - This subsequent part is very important and something that I had trouble with. Don't forget to do this.
  - Suggested adjustments:
    - `memory_limit = 256M`
    - `upload_max_filesize = 64M`
    - `post_max_size = 64M`
    - `max_execution_time = 300`

### 7. Install Composer and Git
- Install Composer and Git:
  ```sh
  sudo apt install composer
  sudo apt install git
  ```

- **Version Control Verification:**
  ```sh
  composer --version
  git --version
  ```

### 8. Install Omeka S
- Navigate to the web root and clone the Omeka S repository:
  ```sh
  cd /var/www/html
  sudo git clone https://github.com/omeka/omeka-s.git
  ```

### 9. Set File Permissions
- Set the correct file permissions:
  ```sh
  sudo chown -R www-data:www-data /var/www/html/omeka-s
  sudo chmod -R 755 /var/www/html/omeka-s
  ```

### 10. Install Omeka S Dependencies with Composer
- Install dependencies:
  ```sh
  cd omeka-s
  sudo composer install
  ```

### 11. Create a Host Config for Apache
- Create a new virtual host configuration:

```sh
  sudo nano /etc/apache2/sites-available/omeka-s.conf
```

- Add the following content to the config file:

```apache
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/html/omeka-s

    <Directory /var/www/html/omeka-s>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

### 12. Enable the Virtual Host and Restart Apache
- Enable the virtual host and restart Apache:
  ```sh
  sudo a2ensite omeka-s.conf
  sudo systemctl restart apache2
  ```

### 13. Finalize Omeka S Installation
- Open a web browser and navigate to `http://your-server-ip/omeka-s`
- Follow the on-screen instructions to complete the Omeka S setup, entering the database information created earlier.

### 14. Enable HTTPS (Optional)
- Install Certbot for SSL/TLS configuration:
  ```sh
  sudo apt install certbot python3-certbot-apache
  sudo certbot --apache
  ```

- Follow Certbot's instructions to obtain and install a free SSL certificate from Let's Encrypt.

### 15. Optimize MySQL Configuration
- Consider optimizing MySQL for better performance:
  ```sh
  sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
  ```

- Add or modify configurations like:
  ```ini
  innodb_buffer_pool_size = 1G
  query_cache_size = 64M
  query_cache_type = 1
  ```

### 16. Enable Error Logging for Debugging
- Ensure error logging is enabled to assist with troubleshooting:
  ```apache
  php_flag display_errors Off
  php_flag log_errors On
  php_value error_log /var/www/html/omeka-s/php_errors.log
  ```

### 17. Set Up Cron Jobs for Maintenance (Optional)
- I didn't do this, but in retrospect would be better to complete
- Set up cron jobs for regular maintenance tasks:
  ```sh
  crontab -e
  ```

- Add tasks such as:
  ```cron
  0 3 * * * php /var/www/html/omeka-s/application/data/scripts/backup.php
  ```

### 18. Security Considerations

Ensuring the security of the MySQL root account is crucial for protecting your database. Below are several recommended security practices:

#### 1. Set a Strong Password
Always use a strong password for the MySQL root account. A strong password should include a combination of uppercase and lowercase letters, numbers, and special characters. Avoid using default or weak passwords.

**Example Command:**
```
ALTER USER 'root'@'localhost' IDENTIFIED BY 'New_Strong_Password';
```

#### 2. Disable Remote Root Access
To prevent unauthorized access, restrict the root account to local connections only. This prevents external hosts from connecting directly to the MySQL root account.

**Example Command:**
```
UPDATE mysql.user SET Host='localhost' WHERE User='root';
FLUSH PRIVILEGES;
```

#### 3. Use the `mysql_secure_installation` Script
MySQL provides a built-in script that walks you through securing your installation. This includes removing anonymous users, enforcing strong passwords, and more.

**Example Command:**
```
sudo mysql_secure_installation
```

#### 4. Remove Anonymous Users
Anonymous user accounts can pose a security risk. Ensure they are removed to limit unauthorized access.

**Example Command:**
```
DELETE FROM mysql.user WHERE User='';
FLUSH PRIVILEGES;
```

#### 5. Remove Remote Root Access (if enabled)
Root access should be limited to local connections. If remote access is necessary, consider creating a separate user with specific permissions. To ensure root cannot access remotely, use the following command:

**Example Command:**
```
DELETE FROM mysql.user WHERE User='root' AND Host != 'localhost';
FLUSH PRIVILEGES;
```

#### 6. Grant Minimal Privileges
For day-to-day operations, avoid using the root account. Instead, create separate users with the minimal privileges required for their tasks.

#### 7. Enable Logging and Monitoring
Enable MySQL logs to monitor suspicious activities and access attempts. Regularly review logs to identify potential security risks.

#### 8. Use SSL/TLS Encryption
If remote connections are necessary, configure MySQL to use SSL/TLS to encrypt traffic between clients and the server. This ensures secure communication over the network.

By following these security practices, you can help safeguard your MySQL database and reduce the risk of unauthorized access.


### 19. Backup Procedures
- Document a simple backup procedure for Omeka S data:
  ```sh
  mysqldump -u omeka_user -p omeka_s > /path/to/backup/omeka_s_backup.sql
  ```

By following these steps and meeting the system requirements, Omeka S will be effectively installed and configured on a LAMP stack, providing a robust platform for managing and sharing digital collections at 91.9 KCSB FM.
