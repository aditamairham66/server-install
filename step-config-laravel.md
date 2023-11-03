Laravel 10 is not a released version at the time of my last knowledge update (January 2022). Laravel 8 was the latest LTS (Long Term Support) version available. However, the steps for configuring Laravel with Apache on CentOS 7 are similar for different versions of Laravel.

To configure a Laravel application with Apache 2.4 on CentOS 7, you can follow these general steps. Please ensure that you have your Laravel project ready and your server environment set up.

1. **Install Apache and PHP**:

   Make sure Apache and PHP are installed on your CentOS 7 server. You can use the following commands to install them:

   ```bash
   sudo yum install httpd
   sudo yum install php
   ```

2. **Install Required PHP Extensions**:

   Laravel typically requires some PHP extensions. You can install them using the following command:

   ```bash
   sudo yum install php-mysql php-xml php-mbstring
   ```

3. **Create a Virtual Host Configuration**:

   Create a virtual host configuration for your Laravel application. You can create a new configuration file in `/etc/httpd/conf.d/` for your site. For example:

   ```bash
   sudo nano /etc/httpd/conf.d/mylaravelapp.conf
   ```

   Inside the configuration file, you can use a configuration similar to this (adjust the paths as needed):

   ```apache
   <VirtualHost *:80>
       ServerAdmin webmaster@mylaravelapp.com
       DocumentRoot /var/www/mylaravelapp/public
       ServerName mylaravelapp.com

       <Directory "/var/www/mylaravelapp/public">
           AllowOverride All
           Order allow,deny
           Allow from all
       </Directory>
   </VirtualHost>
   ```

   Don't forget to replace `mylaravelapp.com` and the paths with your actual values.

4. **Enable the Virtual Host**:

   Enable the virtual host you've just created:

   ```bash
   sudo systemctl enable httpd
   ```

5. **Restart Apache**:

   Restart the Apache web server to apply the changes:

   ```bash
   sudo systemctl restart httpd
   ```

6. **Set Permissions for Laravel**:

   Make sure the web server can write to the storage and bootstrap/cache directories in your Laravel application:

   ```bash
   sudo chown -R apache:apache /var/www/mylaravelapp/storage
   sudo chown -R apache:apache /var/www/mylaravelapp/bootstrap/cache
   ```

7. **Configure the `.env` File**:

   Update the `.env` file of your Laravel application with your database configuration and other settings.

8. **Run Laravel Commands**:

   In your Laravel project directory, run the following commands to generate the application key and perform other setup tasks:

   ```bash
   php artisan key:generate
   php artisan config:cache
   ```

9. **Restart Apache Again**:

   After making these changes, restart Apache to ensure the configuration is updated:

   ```bash
   sudo systemctl restart httpd
   ```

Your Laravel application should now be accessible via your domain name, and you've configured it to run on Apache 2.4 with CentOS 7.