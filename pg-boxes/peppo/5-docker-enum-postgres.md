# 5 docker enum postgres

```
postgres@326cfee15738:/$ psql -U postgres -c 'SHOW config_file'
config_file
------------------------------------------
 /var/lib/postgresql/data/postgresql.conf
(1 row)
```

## PEAS

```
Linux version 4.9.0-12-amd64

╣ Possible Entrypoints

/docker-entrypoint-initdb.d:
lrwxrwxrwx 1 root root   34 May 16  2020 /docker-entrypoint.sh -> usr/local/bin/docker-entrypoint.sh
total 8.0K

╣ My user
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#users
uid=999(postgres) gid=999(postgres) groups=999(postgres),101(ssl-cert)

╣ Users with console
postgres:x:999:999::/var/lib/postgresql:/bin/bash
root:x:0:0:root:/root:/bin/bash

╣ Unexpected in root
/.dockerenv
/docker-entrypoint.sh
/docker-entrypoint-initdb.d

╣ Backup files (limited 100)
-rwxr-xr-x 1 root root 117824 May 13  2020 /usr/lib/postgresql/12/bin/pg_basebackup

╣ Interesting GROUP writable files (not in Home) (max 500)
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#writable-files
Group postgres:
	/run/postgresql
	/var/log/postgresql
```

Nothing here, trying passwords for eleanor
