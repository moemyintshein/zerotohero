#!/bin/bash

##LAMP installation on Debian and Red Hat

DEBIAN=deb
REDHAT=rpm 

read -p "Enter your linux distro[deb/rpm]: " distro
if [ $distro == $DEBIAN ]; then
    #installation apache web server
    sudo apt-get update     
    sudo apt-get install apache2 -y
    sudo systemctl restart apache2
    
    #installation mysql-server
    sudo apt-get install mysql-server -y
    #configure root password for mysql-server 'sudo mysql_secure_installation'
    
    #installation php
    sudo apt-get install php libapache2-mod-php php-mysql php-curl php-gd php-mbstring php-mcrypt php-xml php-xmlrpc -y
    #installation php-mcrypt
    bash "./php-mcrypt.sh"
    sudo systemctl restart apache2
    
elif [ $distro == $REDHAT ]; then
    #installation apache webserver
    sudo yum update
    sudo yum install httpd -y
    sudo systemctl restart httpd
    sudo systemctl enable httpd      #for boot startup 
    #uncomment following 3 lines if you enable firewalld service
      #sudo firewall-cmd --permanent --zone=public --add-service=http 
      #sudo firewall-cmd --permanent --zone=public --add-service=https
      #sudo firewall-cmd --reload
    
    #installation mariadb
    sudo yum install mariadb mariadb-server -y
    sudo systemctl restart mariadb
    sudo systemctl enable mariadb
    #configure root password for mysql-server 'sudo mysql_secure_installation'
    
    #installation php
    sudo yum install php php-mysql -y
    sudo systemctl restart httpd
    
else
    echo "Wrong input! Please try with deb or rpm."
    
fi
    

