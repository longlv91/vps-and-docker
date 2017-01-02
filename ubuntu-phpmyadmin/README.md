- sudo phpenmod mcrypt<br/>
- sudo phpenmod mbstring<br/>
- sudo systemctl restart apache2<br/>
- vim /etc/apache2/sites-available/000-default.conf<br/>
Change directory in DocumentRoot<br/>
- vim /etc/apache2/apache2.conf<br/>
Change directory in /var/www/<br/>
- sudo service apache2 restart<br/>
