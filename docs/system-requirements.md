# System Requirements

To ensure the Omeka S platform operates efficiently at 91.9 KCSB FM, it is essential to meet the following system requirements. These requirements cover both the server environment and required software dependencies.
### Server Requirements

**Operating System:**
- [Elementary OS](https://elementary.io/)

**Hardware:**

  - **Processor:** Ideally 1 GHz or faster
  - **Memory:** 2 GB RAM MINIMUM (4+ GB recommended)
  - **Storage:** 20GB+ Disk Space
  - **Network:** Reliable internet connection

### Software Dependencies

Omeka S is run with a LAMP stack backend architecture. The software requirements are detailed below:

#### Linux
- **Elementary OS (Ubuntu):** Ensure that your system is up-to-date to avoid security vulnerabilities and compatibility issues.

#### Apache
- **Apache HTTP Server 2.4 or higher**
  - Ensure `mod_rewrite` is enabled

#### MySQL
- **MySQL 5.7 or higher or MariaDB 10.1 or higher**
  - Recommended: InnoDB storage engine for tables to increase efficiency and provide foreign key support
  - Must be configured to handle UTF-8 encoding:
    ```sql
    ALTER DATABASE your_database_name CHARACTER SET = utf8mb4 COLLATE = utf8mb4_unicode_ci;
    ```
  - MySQL default collation/character set is generally `utf8mb4` and `utf8mb4_0900_ai_ci`, but double-check to ensure.

#### PHP
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

