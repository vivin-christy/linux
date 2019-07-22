#Linux configuration
Project IP: http://52.66.211.46/

##Start a new Ubuntu Linux server instance on Amazon Lightsail.

##Connect using SSH

##Update all currently installed packages
*sudo apt-get update
*sudo apt-get upgrade
*install them manually
*sudo apt-get -u upgrade

##Change the SSH port from 22 to 2200. Make sure to configure the Lightsail firewall to allow it.
*sudo vi /etc/ssh/sshd_config
*Restart ssh service
*sudo ufw allow 2200
*sudo ufw allow 80
*sudo ufw allow 123
*sudo ufw enable

##To create a user called `grader`
*sudo adduser grader
*password= grader

##Create a new ssh-key called `catalog_root`.
Enter file in which to save the key (/home/ubuntu/.ssh/id_rsa): catalog_root
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in catalog_root.
Your public key has been saved in catalog_root.pub.
The key fingerprint is:
SHA256:C4kSQ+JkIjFqcAAE4wSXIW+unMJxXIXjmaO489tEDVA ubuntu@ip-172-26-13-59
The key's randomart image is:
+---[RSA 2048]----+
|^B=+.E..         |
|@X. .o.          |
|.+= .o+          |
|.o.o.*o.         |
| .+oo.+.S        |
|oo+o.  . .       |
|o+.  .  .        |
|.o  o            |
|  oo..           |
+----[SHA256]-----+

ubuntu@ip-172-26-13-59:~$ sudo cat catalog_root.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQClHpR0+43jOHk/086/w4jx9PYTHeYJtBH2VWuGgK5LcmQQch
IUHaU7XI8OZ1ahG9lFQqp+Pvv0iUi/bapCugch8oGQcK/dblfkkNSe808hH2a+XgrxffYgd4uayzekWrhMW0tb
UlkOfLVMUvwlLWz+rwG/eUyjSAnAWlaUqBg5ZMKvpKyTpCYPDdtIJ41ObQSUjNvMa/69RySu6MKNFRLOvQPB0d
6hgr41g7rq7K7FIHdbGifq4ArMl+5Q8CvzNg8i2M4eA8oKdg+Qmow7uzgUDNe4t7EBPDoKMlYzNhC/9BG7Y1qE
AhK7Sj5KtUkTxqxaR62jv3rWFPsQ/blNeKWz ubuntu@ip-172-26-13-59


##sudo vi /etc/sudoers.d/grader
*grader ALL=(ALL) NOPASSWD:ALL

##To configure timezone
*sudo dpkg-reconfigure tzdata

##To serve Python using Apache and mod_wsgi,need to install
*sudo apt-get install python3
*sudo apt-get install python3-setuptools
*sudo apt-get install apache2 libapache2-mod-wsgi-py3
*sudo service apache2 restart

##Install postgresql
*sudo apt-get install postgresql

*sudo -u postgres psql
*create user catalog with password 'password';
*create database catalog with owner catalog;

##To install git
*sudo apt-get install git
*cd /var/www
*sudo git clone https://github.com/vivin-christy/ud-catalog.git catalog

##Then we need to setup the project
*sudo easy_install3 pip
*cd catalog
*sudo pip3 install -r requirements.txt
*export DB_URI=postgresql://catalog:password@localhost/catalog
*python3 manage.py db upgrade
*python3 create_category.py
*sudo vi config.py
also change redirect_uri to http://catalog.aavi.me/gCallback

##OAuth authentication
*Client ID	
544406063127-k38vd06fg22m0802h9vo69i63ce0m3pf.apps.googleusercontent.com
Client secret	
9NEB4PQ5-UTtm5yW0yOIsiiq
*Authorized JavaScript origins-  	http://localhost:5000
*Authorized redirect URIs-  	http://catalog.aavi.me/gCallback

##sudo vi /etc/apache2/sites-available/catalog.conf
<VirtualHost *:80>
    ServerName 52.66.211.46

    WSGIScriptAlias / /var/www/catalog/wsgi.py

    <Directory /var/www/catalog>
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>

##Once this is done
*sudo a2ensite catalog
*sudo service apache2







