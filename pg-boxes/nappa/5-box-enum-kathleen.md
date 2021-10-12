# 5 box enum kathleen

```
[kathleen@nappa forum]$ cat db.sql
INSERT INTO `users` VALUES
(1,'westley.dakari@easysetting.org','$2a$11$lk4vdhhO58ieqg1HQo7u.OqjU7vReJGkUfyAZmWgIKlLi.neyt2ru',NULL,NULL,NULL,0,NULL,NULL,NULL,NULL,'2020-11-04 13:12:49.988166','2020-11-04 13:12:49.988166','westley.dakari'),
(2,'willam.iran@easysetting.org','$2a$11$JoqTUzLiY1Cm6Qd2iisaaeSXjq9F2hwgKkc18p2QkN17bDIm1eP.O',NULL,NULL,NULL,0,NULL,NULL,NULL,NULL,'2020-11-04 14:08:01.012468','2020-11-04 14:08:01.012468','willam.iran'),
(3,'logun.vergil@easysetting.org','$2a$11$sX.aM5iwIRVgotPwSdUILOmzzQOtJkc43mCQARs7Ynas6UWXDiuAW',NULL,NULL,NULL,0,NULL,NULL,NULL,NULL,'2020-11-04 14:10:10.447159','2020-11-04 14:10:10.447159','logun.vergil'),
(4,'admin.forum@easysetting.com','$2a$11$ICtG8hqXv39lW2NGTLdnUe9lTCmMgvUD3aXXx3UoopVdA2Lv9eNRu',NULL,NULL,NULL,0,NULL,NULL,NULL,NULL,'2020-11-04 14:14:03.775925','2020-11-04 14:14:03.775925','admin.forum'),
(5,'romaan.juanluis@easysetting.com','$2a$11$YgxzLmjR2NwkHrzS8uMtieALKcMil6yHXgihjlmUoCBXUNHXoOqBi',NULL,NULL,NULL,0,NULL,NULL,NULL,NULL,'2020-11-04 14:22:12.153737','2020-11-04 14:22:12.153737','romaan.juanluis');

# master key is not in config but ftp shows it
[kathleen@nappa forum]$ find / -name master.key -type f 2>/dev/null
/srv/ftp/forum/config/master.key
[kathleen@nappa forum]$ ls -la /srv/ftp/forum/config/master.key
-rw------- 1 root root 32 Nov  6  2020 /srv/ftp/forum/config/master.key
```

## PEAS

```
# no python; cant run suidenum
╣ PATH
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#writable-path-abuses
/home/kathleen/.gem/ruby/2.7.0/bin:/home/kathleen/.gem/ruby/2.7.0/bin

╣ Users with console
kathleen:x:1000:1000::/home/kathleen:/bin/bash
root:x:0:0::/root:/bin/bash

╣ MySQL version
mysql  Ver 15.1 Distrib 10.5.6-MariaDB, for Linux (x86_64) using readline 5.1

╣ Active Ports
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      295/puma 4.3.6 (tcp
```
