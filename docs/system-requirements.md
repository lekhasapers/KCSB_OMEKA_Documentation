# System Requirements

To ensure the Omeka S platform operates efficiently at 91.9 KCSB FM, it is essential to meet the following system requirements. These requirements cover both the server environment and required software dependencies.

## Server Requirements

**Operating System:**
- Elementary OS (documentation)

**Hardware:**

  - **Processor:** Ideally 1 GHz or faster
  - **Memory:** 2 GB RAM MINIMUM (4+ GB recommended)
  - **Storage:** 20GB+ Disk Space
  - **Network:** Reliable internet connection

## Software Dependencies

Omeka S is run with a LAMP stack backend architecture. The software requirements are detailed below:

### Linux
- **Elementary OS (Ubuntu):** Ensure that your system is up-to-date to avoid security vulnerabilities and compatibility issues.

### Apache
- **Apache HTTP Server 2.4 or higher**
  - Ensure `mod_rewrite` is enabled

### MySQL
- **MySQL 5.7 or higher or MariaDB 10.1 or higher**
  - Recommended: InnoDB storage engine for tables to increase efficiency and provide foreign key support
  - Must be configured to handle UTF-8 encoding:
    ```sql
    ALTER DATABASE your_database_name CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci;
    ```
  - MySQL default collation/character set is generally `utf8mb4` and `utf8mb4_0900_ai_ci`, but double-check to ensure.

### PHP
- **PHP 7.4 or higher**
  - Required PHP extensions: `PDO`, `pdo_mysql`, `mysqli`, `json`, `mbstring`, `xml`, `dom`, `simplexml`, `fileinfo`, `curl`, `gd`
  - Install required PHP extensions:
    ```sh
    sudo apt install php libapache2-mod-php php-mysql php-json php-mbstring php-xml php-dom php-simplexml php-fileinfo php-curl php-gd
    ```

### Additional Software
- **Composer** (for PHP dependencies)
- **Git** (for version control)
- **SSL Certificate**

## Omeka S and LAMP Stack Dependencies

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

### 3. Install MySQL
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

### 4. Install PHP and Required Extensions
- Install PHP and required extensions:
  ```sh
  sudo apt install php libapache2-mod-php php-mysql php-json php-mbstring php-xml php-dom php-simplexml php-fileinfo php-curl php-gd
  ```

- **Verification:** Create a PHP File to verify installation:
  ```sh
  echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php
  ```
  Navigate to `http://localhost/info.php`, where the PHP information page will be visible.

### 5. Install Composer and Git
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

### 6. Install Omeka S
- Navigate to the web root and clone the Omeka S repository:
  ```sh
  cd /var/www/html
  sudo git clone https://github.com/omeka/omeka-s.git
  ```

### 7. Set File Permissions
- Set the correct file permissions:
  ```sh
  sudo chown -R www-data:www-data /var/www/html/omeka-s
  sudo chmod -R 755 /var/www/html/omeka-s
  ```

### 8. Install Omeka S Dependencies with Composer
- Install dependencies:
  ```sh
  cd omeka-s
  sudo composer install
  ```

### 9. Create a Host Config for Apache
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

### 10. Enable the Virtual Host and Restart Apache
- Enable the virtual host and restart Apache:
  ```sh
  sudo a2ensite omeka-s.conf
  sudo systemctl restart apache2
  ```

### 11. Finalize Omeka S Installation
- Open a web browser and navigate to `http://your-server-ip/omeka-s`
- Follow the on-screen instructions to complete the Omeka S setup, entering the database information created earlier.

By following these steps and meeting the system requirements, Omeka S will be effectively installed and configured on a LAMP stack, providing a robust platform for managing and sharing digital collections at 91.9 KCSB FM.