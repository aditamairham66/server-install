The error message "Failed to restart php-fpm.service: Unit not found." suggests that the PHP-FPM service unit does not exist on your system. This typically occurs when PHP-FPM is not installed or when it's installed but the service unit is named differently.

To resolve this issue, you should check whether PHP-FPM is installed and determine the correct service unit name. Here are the steps to follow:

1. Check if PHP-FPM is Installed:

   Run the following command to check if PHP-FPM is installed on your system:

   ```bash
   php-fpm -v
   ```

   If PHP-FPM is not installed, you need to install it. You can use the package manager (e.g., `yum`) to install PHP-FPM. For example:

   ```bash
   sudo yum install php-fpm
   ```

2. Determine the Correct Service Unit Name:

   After installing PHP-FPM, you may need to determine the correct name of the service unit. The name may vary depending on the Linux distribution and version you are using. Common names include `php-fpm`, `php7.4-fpm`, or similar.

   You can list the available service units with a command like this:

   ```bash
   systemctl list-units --type=service | grep php
   ```

   Look for the PHP-FPM service in the list and note its name.

3. Restart PHP-FPM:

   Once you have determined the correct service unit name, use that name to restart PHP-FPM. For example, if the service unit is named `php-fpm`, you would run:

   ```bash
   sudo systemctl restart php-fpm
   ```

   If you find that the service unit is named differently, replace `php-fpm` with the correct name in the `systemctl restart` command.

By following these steps, you should be able to restart PHP-FPM without encountering the "Unit not found" error.