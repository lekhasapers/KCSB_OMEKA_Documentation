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