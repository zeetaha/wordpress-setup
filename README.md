# wordpress-setup
Install Dependecies 

1. `sudo apt update
   sudo apt install apache2 \
                 ghostscript \
                 libapache2-mod-php \
                 mysql-server \
                 php \
                 php-bcmath \
                 php-curl \
                 php-imagick \
                 php-intl \
                 php-json \
                 php-mbstring \
                 php-mysql \
                 php-xml \
                 php-zip`

Install Wordpress

2. `sudo mkdir -p /srv/www`
3. `sudo chown www-data: /srv/www`
4. `curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www`

Configure

5. sudo nano /etc/apache2/sites-available/wordpress.conf
6. <VirtualHost *:80>
      ServerName 15.156.11.63
      DocumentRoot /srv/www/wordpress
      <Directory /srv/www/wordpress>
          Options FollowSymLinks
          AllowOverride Limit Options FileInfo
          DirectoryIndex index.php
          Require all granted
      </Directory>
      <Directory /srv/www/wordpress/wp-content>
          Options FollowSymLinks
          Require all granted
      </Directory>
  </VirtualHost>
  
7. sudo a2ensite wordpress
8. sudo a2enmod rewrite
9. sudo a2dissite 000-default
10. sudo service apache2 reload

