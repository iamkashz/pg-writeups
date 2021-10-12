# 5 box enum apache

```
bash-4.2$ cat db.php
<?php
define('DBHOST', '127.0.0.1');
define('DBUSER', 'root');From BaseFrom Base58From Base64
define('DBPASS', 'MalapropDoffUtilize1337');From Base32From Base62From Base85
define('DBNAME', 'SimplePHPGal');
?>

bash-4.2$ mysql -u root -p
Enter password:

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| SimplePHPGal       |
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.01 sec)

mysql> select * from users;
+----------+----------------------------------------------+
| username | password                                     |
+----------+----------------------------------------------+
| josh     | VFc5aWFXeHBlbVZJYVhOelUyVmxaSFJwYldVM05EYz0= |
| michael  | U0c5amExTjVaRzVsZVVObGNuUnBabmt4TWpNPQ==     |
| serena   | VDNabGNtRnNiRU55WlhOMFRHVmhiakF3TUE9PQ==     |
+----------+----------------------------------------------+

# using cyberchef 
# recipe is password > base64 > base64 > plain-text
josh: MobilizeHissSeedtime747
michael: HockSydneyCertify123
serena: OverallCrestLean000
```
