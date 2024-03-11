
# Installing Apache Web Server

```bash
sudo apt update
```

Install the Apache web server using the following apt command. When prompted to confirm the installation, input Y to accept and press ENTER.

```bash
sudo apt install apache2 -y
```

```bash
sudo systemctl is-enabled apache2
sudo systemctl status apache2
```

Change the following settings per your requirements:

```bash
memory_limit = 512M
post_max_size = 32M
upload_max_filesize = 32M
date.timezone = Asia/Ho_Chi_Minh
```
Save and close the file, then restart the Apache service to apply the changes:
```bash
systemctl restart apache2
```

Now the Apache web server and PHP should be running. You can verify that by creating the phpinfo file and testing it via the web browser.
Run the following command to create a new phpinfo file '/var/www/html/info.php'. This file should now be accessible via the URL path '/info.php'.

```bash
cat <<EOF | sudo tee /var/www/html/info.php
<?php
phpinfo();
?>
EOF
```
