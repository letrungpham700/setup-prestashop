# Install and Configuring PHP

1) PHP 8.1 is the default PHP version in Ubuntu 22.04. It is fully supported as well as a recommendation for PrestaShop. So, run the below command to install PHP and all other necessary PHP modules:

```bash
sudo apt install software-properties-common apt-transport-https -y
sudo add-apt-repository ppa:ondrej/php -y
sudo apt install php php-common php-cli php-fpm php-opcache php-gd php-mysql php-curl php-intl php-xsl php-mbstring php-zip php-bcmath php-soap -y
#sudo apt install php8.1 php8.1-common php8.1-cli php8.1-fpm php8.1-opcache php8.1-gd php8.1-mysql php8.1-curl php8.1-intl php8.1-xsl php8.1-mbstring php8.1-zip php8.1-bcmath php8.1-soap -y
```

After installing all the packages, edit the php.ini file:
```bash
vi /etc/php/8.1/apache2/php.ini
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

2) After this installation process is complete, the PHP-FPM service will automatically start. You can verify it by typing:
```bash
sudo systemctl status php8.1-fpm
```

3) After that, run the below sed commands. It will set the recommended PHP options:

```bash
sudo sed -i "s/memory_limit = .*/memory_limit = 1024M/" /etc/php/8.1/fpm/php.ini
sudo sed -i "s/upload_max_filesize = .*/upload_max_filesize = 256M/" /etc/php/8.1/fpm/php.ini
sudo sed -i "s/zlib.output_compression = .*/zlib.output_compression = on/" /etc/php/8.1/fpm/php.ini
sudo sed -i "s/max_execution_time = .*/max_execution_time = 18000/" /etc/php/8.1/fpm/php.ini
sudo sed -i "s/;date.timezone.*/date.timezone = Asia\/Ho_Chi_Minh/" /etc/php/8.1/fpm/php.ini
sudo sed -i "s/;opcache.save_comments.*/opcache.save_comments = 1/" /etc/php/8.1/fpm/php.ini
```

```bash
sudo systemctl restart php8.1-fpm
```
