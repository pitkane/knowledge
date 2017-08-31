# Server Setup

## Sooooo old

```shell
sudo chown -R hiekkaasilmissa:www-data /home/hiekkaasilmissa/www

sudo chown -R www-data:www-data /home/hiekkaasilmissa/www/

sudo find /home/hiekkaasilmissa/www/ -type d -exec chmod 775 {} \;
sudo find /home/hiekkaasilmissa/www/ -type f -exec chmod 644 {} \;
sudo chmod g+s -R /home/hiekkaasilmissa/www/

https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-14-04

Näillä toimii kun www-data on myös mik-groupissa

oikat: mik:mik
sudo find . -type d -exec chmod 755 {} \;
sudo find . -type f -exec chmod 644 {} \;
sudo chown -vR mik .
sudo chmod -vR g+w .

easiest way to do it would be to set the directory's group to the group you want, and then set the sticky group bit on the directory with chmod g+s.

10.9.2015 TOIMIVAT

sudo chown -R mik:www-data .
sudo find . -type d -exec chmod 755 {} \;
sudo find . -type f -exec chmod 644 {} \;
sudo chmod -vR g+w .
sudo chmod g+s .

sudo find /var/www/asdfa.mbit.fi/ -type d -exec chmod 755 {} \;
sudo find /var/www/asdf.mbit.fi/ -type f -exec chmod 644 {} \;

sudo addgroup site1
sudo adduser mik site1
sudo chown -vR mik /var/www/asdf.mbit.fi/
sudo chmod -vR g+w /var/www/asdf.mbit.fi/
```
