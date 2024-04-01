# Installing Omeka

## Prerequisites

- install ImageMagick
  
- enable Apache mod_rewrite
  
- restart Apache

      sudo apt install imagemagick
      sudo a2enmod rewrite
      sudo systemctl restart apache2

## Next Steps

- create a new user and database in MySQL for Omeka

      mysql -u -root
      create user 'omekauser'@'localhost' identified by '59bZ!9bA2';
      create database omekadb;
  
- download Omeka Classic as a zip file

      cd /var/www/html
      sudo wget https://github.com/omeka/Omeka/releases/download/v3.1.2/omeka-3.1.2.zip
      sudo apt install unzip
  
- extract zip file with unzip and change directory name to omeka

      unzip omeka-3.1.2.zip
      sudo mv /var/www/html/omeka-3.1.2 /var/www/html/omeka
  
- find db.ini file and edit

      cd /var/www/html/omeka
      sudo nano db.ini
  
- use chown command on the files directory in the omeka directory

      sudo chown -R www-data:www-data /var/www/html/omeka/files
  
- restart Apache2 and MySQL

      sudo systemctl restart apache2
      sudo systemctl restart mysql
  
- go to web browser and enter http://"your-ip-address"/omeka to complete omeka setup


      
