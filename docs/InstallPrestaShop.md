# Download PrestaShop

1) At the time of writing this article, the latest version of PrestaShop is version `8.1.4`. Download the latest version from the [PrestaShop Downloads Page](https://github.com/PrestaShop/PrestaShop/releases) using the below `wget` command:
First, go to the PrestaShop Git Hub repository page and download the latest version of PrestaShop with the following command:
```bash
wget https://github.com/PrestaShop/PrestaShop/releases/download/8.1.4/prestashop_8.1.4.zip
```

2) After the download is complete, create a directory. It will hold your PrestaShop files:
Once the download is completed, unzip the downloaded file to the Apache root directory:

```bash
unzip prestashop_8.1.4.zip -d /var/www/html/prestashop
```

Next, set proper permissions to the PrestaShop directory:

```bash
chown -R www-data:www-data /var/www/html/prestashop/
chmod -R 755 /var/www/html/prestashop
```

## Configure Apache for PrestaShop
Next, you will need to create an Apache virtual host configuration file to host PrestaShop. You can create it with the following command:
```bash
vi /etc/apache2/sites-available/prestashop.conf
```
Add the following lines:

```bash
<VirtualHost *:80>
   ServerAdmin admin@test.com
   DocumentRoot /var/www/html/prestashop
   ServerName presta.test.com

   <Directory /var/www/html/prestashop>
        Options FollowSymlinks
        AllowOverride All
        Require all granted 
   </Directory>
ErrorLog ${APACHE_LOG_DIR}/example_error.log
CustomLog ${APACHE_LOG_DIR}/example_access.log combined
</VirtualHost>
```
Save and close the file, then enable the PrestaShop virtual host with the following command:

```bash
a2ensite prestashop
```

Next, enable the Apache rewrite module and restart the Apache service to apply the changes:

```bash
a2enmod rewrite
systemctl restart apache2
```

## Access PrestaShop Web UI

<img src="https://imgur.com/fiqzwIi">