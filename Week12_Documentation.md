# Installing WordPress

## Installation

- check the versions of PHP and MySQL

      php --version
      mysql --version

- get additional PHP modules installed

      sudo apt install php-curl php-xml php-imagick php-mbstring php-zip php-intl

- restart Apache2 and MySQL

      sudo systemctl restart apache2
      sudo systemctl restart mysql

## Download and Extract

- change to /var/www/html directory
- download latest version of WordPress with wget
- extract the package using tar

      cd /var/wwww/html
      sudo wget https://wordpress.org/latest.tar.gz
      sudo tar -xzvf latest.tar.gz

  ## Create Database and User

  - switch to the root Linux user
  - login as the MySQL root user
 
        sudo su
        mysql -u root

        create user 'wordpress'@'localhost' identified by 'XXXXXXXXX';
        create database wordpress;
        grant all privileges on wordpress.* to 'wordpress'@'localhost';
        show databases;
        \q

## Set up wp-config.php page

- change to wordpress directory
- copy and rename wp-config-sample.php to wp-config.php
- edit file and add database name, user name, and password

      cd /var/www/html/wordpress
      sudo cp wp-config-sample.php wp-config.php
      sudo nano wp-config.php

- DB_NAME, DB_USER, DB_PASSWORD replace
- add this to disable FTP uploads to the site

      define('FS_METHOD','direct' );

## Change File Ownership

      sudo chown -R www-data:www-data /var/www/html/wordpress

## Run and install script

- go to website http://your_external_ip/wordpress/wp-admin/install.php
- follow prompts on screen

