It seems that the `mysql-server` package is not available in the default CentOS 7 repositories. In CentOS 7, MySQL has been replaced by MariaDB, which is a fork of MySQL and is compatible with it.

You can install MariaDB as a replacement for MySQL using the following command:

```bash
sudo yum install mariadb-server
```

After installing MariaDB, you can proceed with the same steps I provided earlier for securing and configuring the MariaDB server.

Here's a quick summary of the steps:

### Install and Secure MariaDB:

1. Install MariaDB:

   ```bash
   sudo yum install mariadb-server
   ```

2. Start and enable MariaDB:

   ```bash
   sudo systemctl start mariadb
   sudo systemctl enable mariadb
   ```

3. Run the post-installation security script:

   ```bash
   sudo mysql_secure_installation
   ```

### Install phpMyAdmin:

1. Install phpMyAdmin:

   ```bash
   sudo yum install epel-release
   sudo yum install phpmyadmin
   ```

2. Edit the Apache configuration for phpMyAdmin:

   ```bash
   sudo nano /etc/httpd/conf.d/phpMyAdmin.conf
   ```

   Change the line with `Require ip 127.0.0.1` to `Require all granted`.

3. Start and enable Apache:

   ```bash
   sudo systemctl start httpd
   sudo systemctl enable httpd
   ```

After completing these steps, you should have MariaDB and phpMyAdmin installed and ready to use on your CentOS 7 system. You can access phpMyAdmin through your web browser at `http://localhost/phpmyadmin`.