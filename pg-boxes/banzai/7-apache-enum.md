# 7 apache enum

```
# using web shell
CMD: cat /etc/apache2/apache2.conf
# Include generic snippets of statements
IncludeOptional conf-enabled/*.conf

# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

# virtual hosts are enabled
# exploring config file of virtual host
CMD: ls -la /etc/apache2/sites-available/
total 20
drwxr-xr-x 2 root root 4096 Jun  4  2020 .
drwxr-xr-x 8 root root 4096 Jun  4  2020 ..
-rw-r--r-- 1 root root 1428 Jun  5  2020 000-default.conf
-rw-r--r-- 1 root root 6338 Jun 16  2019 default-ssl.conf

CMD: cat /etc/apache2/sites-available/000-default.conf

<VirtualHost *:8295>
	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html
</VirtualHost>

<VirtualHost *:8080>
	ServerAdmin webmaster@localhost
	DocumentRoot /home/banzai
</VirtualHost>


# nothing in here.
```
