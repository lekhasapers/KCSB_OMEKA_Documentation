# IV. Configuration

After installing Omeka S on your server, the next step is to configure it properly to ensure optimal performance and security. This segment covers the initial configuration steps, configuring plugins and themes, and customizing the appearance of your Omeka S site.

## Initial Configuration

### Database Configuration

During the web-based installation process, you will be prompted to enter the database connection details. Ensure you have the following information ready:

- **Database Name:** omeka_s
- **Database User:** omeka_user
- **Database Password:** password
- **Database Host:** localhost

Fill in these details in the appropriate fields and proceed with the installation.

### Admin User Setup

You will also be prompted to create an admin user during the installation process. This user will have full access to all administrative functions in Omeka S.

- **Username:** Choose a unique username.
- **Email:** Enter a valid email address.
- **Password:** Create a strong password.

### Site Configuration

Once the installation is complete, log in to the admin interface using the credentials created in the previous step.

Navigate to **Settings** to configure the basic settings of your Omeka S site, such as site title, site description, and administrative contact information.

## Configuring Plugins

Plugins extend the functionality of Omeka S. The following details the installation procedures for themes and modules.

### Installing Plugins

1. Download the desired plugin from the Omeka S plugin directory.
2. Extract the plugin archive and upload the plugin folder to the `modules` directory in your Omeka S installation path (`/var/www/html/omeka-s/modules`).
3. Ensure correct file permissions:
   ```sh
   sudo chown -R www-data:www-data /var/www/html/omeka-s/modules/PluginName
   sudo chmod -R 755 /var/www/html/omeka-s/modules/PluginName
   ```

### Activating Plugins

1. Log in to the Omeka S admin interface.
2. Navigate to **Modules**.
3. Find the newly installed plugin and click **Install**.
4. Once installed, click **Activate** to enable the plugin.

### Configuring Plugin Settings

After activation, many plugins will add their own configuration options to the admin interface.

Navigate to the plugin’s configuration page via **Modules > [Plugin Name]** and configure the settings as needed.

## Configuring Themes

Themes control the appearance of your Omeka S site. Here’s how to install and customize themes:

### Installing Themes

1. Download the desired theme from the Omeka S themes directory.
2. Extract the theme archive and upload the theme folder to the `themes` directory in your Omeka S installation path (`/var/www/html/omeka-s/themes`).
3. Ensure the correct file permissions:
   ```sh
   sudo chown -R www-data:www-data /var/www/html/omeka-s/themes/ThemeName
   sudo chmod -R 755 /var/www/html/omeka-s/themes/ThemeName
   ```

### Activating Themes

1. Log in to the Omeka S admin interface.
2. Navigate to **Appearance**.
3. Find the newly installed theme and click **Activate**.

### Customizing Themes

Each theme may have its own set of customization options, such as logo upload, color schemes, and layout settings.

Navigate to **Appearance > Themes > Configure** to access and modify these settings.

To make deeper customizations, you can directly edit the theme’s files in the `themes` directory.
