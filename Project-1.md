## PROJECT 1 DOCUMENTATION



### STEP 1


 - update a list of packages in package manager

    Command - `sudo apt update`

    ![update packages](.\Images\UpdatePackages.PNG)



  - run apache2 package installation
    
    Command - `sudo apt install apache2`

     ![update packages](.\Images\InstallApache2.PNG)

  - verify that apache2 is running as a Service in our OS

    Command - `sudo systemctl status apache2`

      ![update packages](.\Images\VerifyApacheRunning.PNG)





### STEP 2 — INSTALLING MYSQL

   - use ‘apt’ to acquire and install mysql server

     Command - `sudo apt install mysql-server`

     ![update packages](.\Images\installmysql.PNG)


-  log in to the MySQL console by typing

    Command - `sudo mysql`

    ![update packages](.\Images\logintomysql.PNG)

 -  set a password for the root user

     Command - `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`

 -  Exit the MySQL shell with

    Command - `exit`

 -  This script will remove some insecure default settings and lock down access to your database system

      Command - `sudo mysql_secure_installation`

       ![update packages](.\Images\securitycheck.PNG)

 -  test if you’re able to log in to the MySQL console by typing

    Command - `sudo mysql -p`

     ![update packages](.\Images\trytologin.PNG)

 -  Exit the MySQL shell with

    Command - `exit`




### STEP 3 — INSTALLING PHP

 -  In addition to the php package, you’ll need php-mysql, a PHP module that allows PHP to communicate with MySQL-based databases. You’ll also need libapache2-mod-php to enable Apache to handle PHP files. Core PHP packages will automatically be installed as dependencies.

    To install these 3 packages at once, run:

Command - `sudo apt install php libapache2-mod-php php-mysql`

  ![update packages](.\Images\installphp.PNG)


 -  Once the installation is finished, you can run the following command to confirm your PHP version:

 Command - `php -v`

 ![update packages](.\Images\phpversion.PNG)


 ### STEP 4 — CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE

 - Create the directory for projectlamp using ‘mkdir’ command as follows:

   Command - `sudo mkdir /var/www/projectlamp`

  - assign ownership of the directory with your current system user

     Command - `sudo chown -R $USER:$USER /var/www/projectlamp`

 - create and open a new configuration file in Apache’s sites-available directory using your preferred command-line editor. Here, we’ll be using vi or vim (They are the same by the way)

 Command - `sudo vi /etc/apache2/sites-available/projectlamp.conf`

   ![update packages](.\Images\conffile.PNG)


 - You can now use a2ensite command to enable the new virtual host
    Command - `sudo a2ensite projectlamp`

    -  disable the default website that comes installed with Apache
    Command - `sudo a2dissite 000-default`

    -To make sure your configuration file doesn’t contain syntax errors, run:
    Command - `sudo apache2ctl configtest`


    - reload Apache so these changes take effect:
    Command - `sudo systemctl reload apache2`

    - Create an index.html file in that location so that we can test that the virtual host works as expected:
    Command - `sudo echo 'Hello LAMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectlamp/index.html`

    - Now go to your browser and try to open your website URL using IP address:

    ![update packages](.\Images\testurl.PNG)


 ### STEP 5 — ENABLE PHP ON THE WEBSITE

 - edit the /etc/apache2/mods-enabled/dir.conf file and change the order in which the index.php file is listed within the DirectoryIndex directive:
    Command - `sudo vim /etc/apache2/mods-enabled/dir.conf`

     ![update packages](.\Images\index.PNG)

 - After saving and closing the file, you will need to reload Apache so the changes take effect:

  Command - `sudo systemctl reload apache2`

   - we will create a PHP script to test that PHP is correctly installed and configured on your server.Create a new file named index.php inside your custom web root folder:
   
  Command - `vim /var/www/projectlamp/index.php`



    




