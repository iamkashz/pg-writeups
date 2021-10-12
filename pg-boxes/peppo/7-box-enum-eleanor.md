# 7 box enum eleanor

## PEAS

```
Linux version 4.9.0-12-amd64 (debian-kernel@lists.debian.org) (gcc version 6.3.0 20170516 (Debian 6.3.0-18+deb9u1) ) #1 SMP Debian 4.9.210-1 (2020-01-20)
Description:    Debian GNU/Linux 9.12 (stretch)

╣ PATH
/home/eleanor/bin

╣ Any running containers? ........ Yes docker(2)
Running Docker Containers
326cfee15738        postgres            "docker-entrypoint.s…"   15 months ago       Up 12 months        0.0.0.0:5432->5432/tcp   postgres
71aa857fe988        redmine             "/docker-entrypoint.…"   15 months ago       Up 12 months        0.0.0.0:8080->3000/tcp   redmine

╣ Analyzing .socket files
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#sockets
Docker socket /var/run/docker.sock is writable (https://book.hacktricks.xyz/linux-unix/privilege-escalation#writable-docker-socket)

╣ My user
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#users
999(docker)
```
