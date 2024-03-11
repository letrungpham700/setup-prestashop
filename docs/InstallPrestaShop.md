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
   ServerName presta.admin.com

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

1) Now, after the PrestaShop download is complete and the server configuration is done, you will finish installation via the web interface. Open your browser, and type your domain.
Back to your web browser and browse the domain name of your Prestashop installation (i.e: http://presta.admin.com/). You should see the web installer is starting the Prestashop installation.

2) You will now select the language you want to use and click on the “Next” button.:
Select the default language for your PrestaShop installation and click Next. The default installation language for PrestaShop is 'English'.

![Language](https://github.com/letrungpham700/setup-prestashop/assets/53925226/f51894ea-3076-4f04-ae9b-5618edde7c55)

On the next screen, you will get the PrestaShop license agreement. So, read the license carefully and continue to select I agree to the above terms and conditions to continue:
Click agree when showed the Prestashop License agreement page.

![License](https://github.com/letrungpham700/setup-prestashop/assets/53925226/451e9b29-d8cb-4708-a9c2-3637f1129055)

3) Next, you will see the below information page system compatibility:
Now create a new admin user for your Prestashop installation. Input details admin user, email, and password. Then, click Next to continue to the database configurations.

![Compatibility](https://github.com/letrungpham700/setup-prestashop/assets/53925226/f3fdfca4-2fcb-49b5-8119-3e1ada708507)

4) Make sure that all pre-installation requirements are met and also that your system is compatible with the PrestaShop.

5) On the next screen, you will need to enter your store details. The email address is the username that will allow you to access the PrestaShop administration backend.

![Store Info](https://github.com/letrungpham700/setup-prestashop/assets/53925226/b8837f7b-135d-462a-afbe-a1989ff27e45)

6) Now, select the content of your store:
For the store content and click 'Next'.
![Content of your store](https://github.com/letrungpham700/setup-prestashop/assets/53925226/c020cbe2-f813-4e0d-9824-ecf58dcdba97)

7) After that, you will be asked to enter the database user and connection details that were created by you earlier:
For the Prestashop database configuration. Input details database user, database name, and the password that you have created. Then, click Next and the Prestashop installation will be starting.

![Database Connection](https://github.com/letrungpham700/setup-prestashop/assets/53925226/babc2e61-aeca-4eb8-a163-94ded0cf8f43)

Once you click on the “Next” button, the installation will start:
Below you can see the installation is processed.

![Installation](https://github.com/letrungpham700/setup-prestashop/assets/53925226/9d91110a-fbc3-4e9a-ad9c-c490c08ec7ab)

8) The installation will take a few minutes, once it is completed you will get a screen confirming that the PrestaShop has been installed.
When the Prestashop installation is finished, you will see the page that informs you about your Prestashop installation. Also, there is an additional change that you should do, which is deleting the 'install' directory on your Prestashop document root.

![PrestaShop Installed](https://github.com/letrungpham700/setup-prestashop/assets/53925226/304e8a56-a624-4a1d-abb9-ebf0273aeb07)

9) For security reasons, you will need to delete the installation directory. For this, go back to the terminal and enter the below rm command:

```bash
rm -rf /var/www/html/prestashop/install
```
10) To access your PrestaShop administrative dashboard, click on the “Manage your store” button. Enter your email and password.
Click on the PrestaShop admin URL. You will be redirected to the PrestaShop admin login page:
![PrestaShop](https://github.com/letrungpham700/setup-prestashop/assets/53925226/e24bf975-00f5-4c15-9dcd-dcb8792349d4)

You will get redirected to the administration dashboard. From here, you will start customizing your PrestaShop installation. Further, you can add new products.
Provide your admin username and password and click on LOG IN. You will be redirected to the PrestaShop dashboard:
![Dashboard](https://github.com/letrungpham700/setup-prestashop/assets/53925226/eefd9d29-d83b-4189-a785-8f80280bddab)

At this point, you have finished the installation of the open-source eCommerce solution Prestashop on Ubuntu 22.04.