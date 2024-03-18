# Creating A Cataloging Module

## Create an HTML page

create a basic html page that contains a form for entering bibliographic data that includes:
- author
- title
- publisher
- copyright

### index.html

    <!DOCTYPE html>
    <html>
    <head>
        <title>Enter Records</title>
    </head>
    <body>
        <h1>OPAC Library Administration</h1>
    
        <p>This is the library administration page for entering records into the OPAC.</p>
        <p>Please do not use this page unless you are an authorized cataloger.</p>
    
        <form action="insert.php" method="post">
            <label for="author">Author:</label>
            <input type="text" name="author" id="author" required><br><br>
    
            <label for="title">Book Title:</label>
            <input type="text" name="title" id="title" required><br><br>
    
            <label for="publisher">Publisher:</label>
            <input type="text" name="publisher" id="publisher" required><br><br>
    
            <label for="copyright">Copyright:</label>
            <input type="date" id="copyright" name="copyright">
    
            <input type="submit" value="Submit">
        </form>
    </body>
    </html>

## Create a PHP insert script

- this script adds data to the MySQL table "books"

### insert.php

    <?php
    
    // Load MySQL credentials
    require_once '../login.php';
    
    // Establish connection
    $conn = mysqli_connect($db_hostname, $db_username, $db_password) or
      die("Unable to connect");
    
    // Open database
    mysqli_select_db($conn, $db_database) or
      die("Could not open database '$db_database'");
    
    // Prepare and bind SQL statement
    $stmt = $conn->prepare("INSERT INTO books (author, title, publisher, copyright) VALUES (?, ?, ?, ?)");
    $stmt->bind_param("ssss", $author, $title, $publisher, $copyright);
    
    // Set parameters and execute statement
    $author = $_POST["author"];
    $title = $_POST["title"];
    $publisher = $_POST["publisher"];
    $copyright = $_POST["copyright"];
    
    if ($stmt->execute() === TRUE) {
        echo "New record created successfully";
    } else {
        echo "Error: " . $stmt->error;
    }
    
    // Close statement and connection
    $stmt->close();
    $conn->close();
    
    echo "<p>Return to the cataloging page: <a href='http://11.111.111.111/cataloging/'>http://11.111.111.111/cataloging/</a></p>";
    ?>


## Add security

- use htpasswd command to create an authentication file in /etc/apache2 directory
  
      sudo htpasswd -c /etc/apache2/.htpasswd libcat
  
- tell Apache2 web server that htpasswd will control access to the cataloging module
  
      sudo nano /etc/apache2/apache2.conf

- change AllowOverride None to AllowOverride All on <Directory /var/www/> section of code

- create .htaccess file in cataloging directory

      AuthType Basic
      AuthName "Authorization Required"
      AuthUserFile /etc/apache2/.htpasswd
      Require valid-user

- check the config file

      apachectl configtest

- restart Apache2

      sudo systemctl restart apache2
      systemctl status apache2

## Ownership and Permission

- change group ownership of /var/www/html to www-data

      sudo chown :www-data /var/www/html

- set setgid bit on /var/www/html

      sudo chmod -R g+s /var/wwww/html

## Add books to catalog using cataloging module

- go to http://34.16.152.2/cataloging and enter book records into catalog



