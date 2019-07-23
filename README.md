#Linux configuration
Project IP: http://13.233.167.61/

##Start a new Ubuntu Linux server instance on Amazon Lightsail.

##Connect using SSH

##Update all currently installed packages
*sudo apt-get update
*sudo apt-get upgrade
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
SHA256:wPD1bTKCg6olcsXzxiAdpAbigYRnzBR0lS//GrDN7g0 ubuntu@ip-172-26-3-26
The key's randomart image is:
+---[RSA 2048]----+
|*B+o=....        |
|=.*= *.o . .     |
| ++ B *.. + o    |
| . + =.o.. +     |
|o +   =oS        |
|.=   . =.        |
|.     . E.       |
|       . +.      |
|       .+..      |
+----[SHA256]-----+

ubuntu@ip-172-26-3-26:~$ cat catalog_root.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC+z7bZCqhF+9cg7IZdMV72/WhvRgUiTVn3yMMrW9bmL63DKYDMtQ
YiyUEzixuN2ZMOL4Xl5NvwsZToZJMhLZGDa7JUIUS6I4apsqkMpqoB+QYk8ahfe8WW9jvV14L7sfwp7nQXlkGD/SO2
aAI6mcUICuMCJo3H/2i55W8H0dN6OcVlUFd2j4y2kteFOrnyqxxRn/j/dPcqBOUUG+H7x8FSrrJzw5kK/McfCrAmNP
bFCH52EeaPiKmpAUKdM9WAmQOdpU8hBlMtsaFA4FbUFKH8AL4C7TsaLHPNzba/onviwWxymvjfzpW03mdwPQILguek
rVYIHtqx9MsgdukXlmcf ubuntu@ip-172-26-3-26


##private key

-----BEGIN RSA PRIVATE KEY-----
Proc-Type: 4,ENCRYPTED
DEK-Info: AES-128-CBC,1F36931A89CF9C11D1CB475130A777BB

K3YmvqK48muBQrABGYMd9NiImARCrM4W3aZlqntebTyI75Rwk/Gto603NuoiUXD8
NPuDYpAK+4zpkxlIP96RX40nXWXwTkiReqXcY9jp8Met5koaJxRvQKM68QpvUF/P
hUrJ2aqXwIQwMioEaXrn8JCRqKE6FPxKrZNVewDN6ZRnFoqmNri3z2gn3H81eaUB
ttHht+/aTphP3euLmVb4A7yBEA+IRxATpFeu2ZJ/bYKImW9jxV5YsfbIbcfKVipW
QryjTtKG14WJQpS7PMb/9zGVejmvp9cZmep4qdADVx15dCYgoxniFnL83vl/IKon
1EToHKTkQ3bM4FaWsZ3eMXQNMfGz2jv9YObnXQT2vuft8Lh0rX6zE/vymUzl2TVe
ZaLJOCi6JYVIWSbNENjVlxvFPAGZaiEyR9xjzRfprQWmDfbJcqKPC2YmtN+tSO6S
tJ84Vo3u9NxfMcM47miJut33olX3v6MbFc2evrIv+kfF4L7FxrvGZqlTEJIqMOOM
fwS4Tzp9bsAUtnglPO02hZ5vFYsvBS8tJGhxkIm3Z7kVoEKur5AKUAHsdzD99IXj
kFC6YKpsHIK6mhlxtewe5kwncdEGnu0Xc6AmTecQELBCWo/2DT7asmOTuLdkCEcb
VZDuuoEGNSb24y5746hqTw+ph2YcTId3euViF931j9G7vZV4VzGGcStdIZ2yqM7W
fAJ2U8BjPXTE/mk4JjoPnG9062Wb5XRjnjFAz2Ni/Or5tVEfb0q5ZcdL1nUxxLLY
293gVKqarBzTYSqbmC+svk/cwMKQWmfzv03MH75rv3AUw7dMsRFlkAd0uel1Q7B6
ZEbgwURfmx4K7+iQfZnUh7W4HTvBe8Amf8ZrGC1ykZV/T1UCUWEwMHSU5WI3Pg//
bsKl3xMX/Q0GpiKb1UpTyQmaUxxYu2XFXs6fBTp4st8+4jzRjJMBcEmiFLDdla9o
KWf1e3y1jAqjBe3+wwJmn4UXrebdURu8SvtegGHm1KPwKcVTqmcLHWbIhHmmrRK/
u7zLUCHV4C9kNNgNBO5mJSE8X4qbXOuUuo+FQyECqOrR1ZQ8eRJACqnuhqbXgbBZ
X2I1GjPYJD4ElpDseRByRSEay1NSH3VW2LLtLeisz74kXnSXpSzjPqTt+pgrOpQ4
S2Nsz2+OwLqXl09E1JJO1SJ9CMtaZuVvJ6ve7PhmOXjhnLmksvx67cU2QPPatAi4
Vm52745N2gMF7/qtJ/1lZaAhBSOvEYQBJ6yzP5oU+MR5EFFQcFJldbaSa7a1qOtS
fXsuWSktDCeS1nnwYFkEeBSqFLEblQV/2PKmIo8YQmgxJw/sXIb19MskqMUvXgNK
HJT284lMX5tSjUK0FMwNTtWmp4mTs+ExSgaRkpIUdqQEvDMi4lvCZZ7ijUFVRZn5
87LXXATGgCBPiQEti2VK+lBhQLf1tc9q3gLCTYn50BhJPYmMwWzWIySJz18cy3jt
4WwfZeN6HxG8BKRdC9PmWzjXaQZTj9qaYuABXaxIiXiB25+rvn1AzRr9cdhgK7Wb
1hZGsVx4uIUeWoYC8WtWced7tCtEOIq10q0bnlwVsgucgeqKqR68tXX26PAHa9NF
-----END RSA PRIVATE KEY-----


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
    ServerName 13.233.167.61

    WSGIScriptAlias / /var/www/catalog/wsgi.py

    <Directory /var/www/catalog>
        Order allow,deny
        Allow from all
    </Directory>
</VirtualHost>

##Once this is done
*sudo a2ensite catalog
*sudo service apache2







