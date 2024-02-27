# How to make a LAMP stack

## Installing Apache

    sudo apt update
    sudo apt -y upgrade

    apt search apache2 | head
    apt show apache2

    sudo apt install apache2

### Basic Checks

    systemctl status apache2

### Creating a web page

    sudo apt install w3m
    w3m 127.0.0.1 
or

    w3m localhost

    w3m 10.182.0.2

-should display web page stating Apache2 Ubuntu Default Page

    cd /var/www/html/
    sudo mv index.html index.html.original
    sudo nano index.html

-create html page
-access page

    http://34.16.156.130/index.html.original

## Installing PHP

### Install
    sudo apt install php libapache2-mod-php
    sudo systemctl restart apache2

      systemctl status apache2

    cd /var/www/html/
    sudo nano info.php

- create file and save

    http://34.16.156.130/info.php

### Configuration

    cd /etc/apache3/mods-enabled/
    sudo cp dir.conf dir.conf.bak
    sudo nano dir.conf

- change heading to: "DirectoryIndex **index.php** index.html index.cgi index.pl index.xhtml index.htm

    apachectl configtest
- want a Syntax OK message
- reload Apache2 configuration

    sudo systemctl reload apache2
    sudo systemctl restart apache2

### Create index.php file

    cd /var/www/html/
    sudo nano index.php

- add code
  
    <html>
      <head>
      <title>Broswer Detector</title>
      </head>
      <body>
      <p>You are using the following browser to view this site:</p>
      
      <?php
      $user_agent = $_SERVER['HTTP_USER_AGENT'];
      
      if(strpos($user_agent, 'Edge') !== FALSE) {
          $browser = 'Microsoft Edge';
      } elseif(strpos($user_agent, 'Firefox') !== FALSE) {
          $browser = 'Mozilla Firefox';
      } elseif(strpos($user_agent, 'Chrome') !== FALSE) {
          $browser = 'Google Chrome';
      } elseif(strpos($user_agent, 'Opera Mini') !== FALSE) {
          $browser = "Opera Mini";
      } elseif(strpos($user_agent, 'Opera') !== FALSE) {
          $browser = 'Opera';
      } elseif(strpos($user_agent, 'Safari') !== FALSE) {
          $browser = 'Safari';
      } else {
          $browser = 'Unknown';
      }
      
      if(strpos($user_agent, 'Windows') !== FALSE) {
          $os = 'Windows';
      } elseif(strpos($user_agent, 'Linux') !== FALSE) {
          $os = 'Linux';
      } elseif(strpos($user_agent, 'Mac') !== FALSE) {
          $os = 'Mac';
      } elseif(strpos($user_agent, 'iOS') !== FALSE) {
          $os = 'iOS';
      } elseif(strpos($user_agent, 'Android') !== FALSE) {
          $os = 'Android';
      } else {
          $os = 'Unknown';
      }
      
      if($browser === 'Unknown' || $os === 'Unknown') {
          echo 'No browser detected.';
      } else {
          echo 'Your browser is ' . $browser . ' and your operating system is ' . $os . '.';
      }
      ?>
      
      </body>
      </html>
- save file, exit nano

    http://34.16.156.130/

## Installing mysql

    sudo apt install mysql-server

    systemctl status mysql

    sudo mysql_secure_installation

- answer "y" to all questions
- set password, exit mysql

      sudo su
      mysql -u root
      show databases;

### Set up user account

    create user '*username*'@'localhost' indentified by '*password*';

- Query OK means continue

### Create Practice Database

    create database opacdb;
    grant all privileges on opacdb.* to '*user*'@'localhost';
    show databases;

### Login as regular user

    mysql -u *username* -p

    show databases;
    use opacdb;

    create table *tablename*
    
- create table

    insert into *tablename*
  
- insert records into table

    select * from *table*
  
- select all records

### Install PHP and MySQL Support

    sudo apt install php-mysql php-mysqli

    sudo systemctl restart apache2
    sudo systemctl restart mysql

    cd /var/www/html/
    sudo touch login.php
    sudo chmod 640 login.php
    sudo chown :www-data login.php
    ls -l login.php
    sudo nano login.php

    <?php // login.php
    $db_hostname = "localhost";
    $db_database = "opacdb";
    $db_username = "opacuser";
    $db_password = "XXXXXXXXX";
    ?>

    sudo nano opac.php

- create file
- test syntax




    

    

    
