Setup Ubuntu Desktop (16.04)
============
Instructions for web-developer.

###Update
```
sudo apt-get update
sudo apt-get upgrade
```

###Fix 3D-acceleration
Source: http://linux.vsevteme.ru/2013/02/01/blog/3d-uskorenie-v-ubuntu-12-10-zapuschennom-v-virtualbox
```
sudo apt-get install linux-headers-$(uname -r) build-essential compizconfig-settings-manager
```
Run VirtualBox guest additions
```
cd /media/`whoami`/VBOXADDITIONS*
sudo ./VBoxLinuxAdditions.run
sudo bash -c 'echo vboxvideo >> /etc/modules'
```
Check:
```
/usr/lib/nux/unity_support_test -p
```

###Install Windows 7 font
Source: http://startubuntu.ru/?p=104240
```
cd /tmp && wget http://www.stchman.com/tools/MS_fonts/tahoma.zip
sudo unzip -d /usr/share/fonts/truetype/msttcorefonts /tmp/tahoma.zip
sudo add-apt-repository ppa:no1wantdthisname/ppa
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fontconfig-infinality
sudo bash /etc/fonts/infinality/infctl.sh setstyle
```
Enter "6".

###Change the Unity launcher orientation [optionally]
Source: http://ubuntuhandbook.org/index.php/2016/03/ubuntu-16-04-move-unity-launcher-to-bottom/
#####To bottom
```
gsettings set com.canonical.Unity.Launcher launcher-position Bottom
```
#####To left
```
gsettings set com.canonical.Unity.Launcher launcher-position Left
```

###Resize the Unity launcher [optionally]
Source: http://askubuntu.com/questions/18345/how-to-resize-the-unity-launcher

###Install Node + npm
```
sudo apt-get install nodejs
sudo apt-get install npm
sudo ln -s /usr/bin/nodejs /usr/bin/node
```

###Install Bower
```
sudo npm install -g bower
```

###Install LAMP
Source: http://tecadmin.net/install-php-7-0-apache-2-4-mysql-5-6-on-ubuntu/

#####PHP 7
```
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get install -y php7.0
```
#####Apache 2.4
```
sudo add-apt-repository ppa:ondrej/apache2
sudo apt-get update
sudo apt-get install apache2
```
#####MySQL 5.7
```
sudo add-apt-repository -y ppa:ondrej/mysql-5.7
sudo apt-get update
sudo apt-get install mysql-server-5.7
```
#####PHP-extensions
```
sudo apt-get install libapache2-mod-php7.0 php7.0-mysql php7.0-curl php7.0-json php7.0-mbstring
```
! libapache2-mod-php

###Install Git
```
sudo apt-get install git
```

###Install Curl
```
sudo apt-get install curl
```

###Install Composer
#####Globally
Source: http://askubuntu.com/questions/116960/global-installation-of-composer-manual
```
curl -s http://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/
alias composer='/usr/local/bin/composer.phar'
```
#####Locally
Source: https://getcomposer.org/download/
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('SHA384', 'composer-setup.php') === '92102166af5abdb03f49ce52a40591073a7b859a86e8ff13338cf7db58a19f7844fbc0bb79b2773bf30791e935dbd938') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```





###TODO:
```

apt-get install mc openssh-server curl nodejs nginx git git-gui

apt-get install apache2 a2enmod rewrite

apt-get install php5 php5-mysql php5-curl php5-cli php5-memcache php5-memcached php5-gd php5-imagick php5-mcrypt php5-pgsql php5-intl php5-xdebug

apt-get install mysql-server

wget http://pear.php.net/go-pear.phar
php go-pear.phar
curl -s https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
pear config-set auto_discover 1
pear install pear.phpunit.de/PHPUnit

apt-get install postgresql-9.1 pgadmin3
passwd postgres
sudo -u postgres psql template1
ALTER USER postgres with encrypted password '****';

gedit /etc/postgresql/9.1/main/pg_hba.conf
— Update:
local all postgres
— entry to:
local all postgres md5
gedit /etc/postgresql/9.1/main/postgresql.conf
uncomment: #listen_addresses = 'localhost'

su postgres
mkdir /var/lib/postgresql/data
gedit /etc/environment
add to PATH: :/usr/lib/postgresql/9.1/bin
append: PGDATA="/var/lib/postgresql/data"
env
su postgres
createdb test
# TODO: configure max_connections for postgresql

apt-get -f install
apt-get clean all
apt-get autoremove
update
upgrade
##############################
local all all trust
# IPv4 local connections:
host all all 127.0.0.1/32 md5
# IPv6 local connections:
host all all ::1/128 md5
host all all 0.0.0.0/0 md5
##############################
install console-cyrillic
dpkg-reconfigure console-setup


sudo apt-get install phpmyadmin
```
