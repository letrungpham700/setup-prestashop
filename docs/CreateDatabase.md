# Create a MySQL Database

Để cài đặt PrestaShop 9.0 mới nhất, cần một máy chủ web chạy PHP 8.1+ và bất kỳ phiên bản nào của MySQL 5.6+ (MySQL, MariaDB, Percona Server, v.v.).

```bash
sudo apt install unzip -y
```

1) PrestaShop stores its data in a MySQL database. If MySQL or MariaDB installation is there on your server then skip this step. Otherwise, install the MySQL 5.7 server package. Do it from Ubuntu’s default repositories by using the following command:

```bash
sudo apt install mysql-server mysql-client -y
```

2) Now, to create a database, log in to the MySQL shell:

```bash
sudo mysql
```

3) Next, from within the MySQL shell, run the below SQL statement. It will create a new database as `prestashop`:

```bash
CREATE DATABASE prestashop;
```

4) Now, you need to create a MySQL user account named `prestashop` and grant the necessary permissions to the user. Do it by running the below command:

```bash
CREATE USER 'prestashop_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL ON prestashop.* TO 'prestashop_user'@'localhost';
```

5) After this, exit the MySQL console by typing:

```bash
EXIT;
```

