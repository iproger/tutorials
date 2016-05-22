Help for deployments surroundings in Ubuntu.
============
```
sudo apt-get update

sudo apt-get upgrade

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
