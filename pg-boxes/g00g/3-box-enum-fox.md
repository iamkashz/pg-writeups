# 3 box enum fox

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/arj
------------------------------

$ /usr/bin/arj
ARJ32 v 3.10, Copyright (c) 1998-2004, ARJ Software Russia.

Processing archive: /usr/bin/arj
Archive created: 2019-02-10 14:50:08, modified: 2019-02-10 14:50:08

List of frequently used commands and switches.  Type ARJ -? for more help.

Usage:     ARJ <command> [-<sw> [-<sw>...]] <archive_name> [<file_names>...]
Examples:  ARJ a -e archive, ARJ e archive, ARJ l archive *.doc
<Commands>
 ac: Add Chapter to chapter archive     l: List contents of archive
  a: Add files to archive               m: Move files to archive
  c: Comment archive files              t: Test integrity of archive
  d: Delete files from archive          u: Update files to archive
  e: Extract files from archive         v: Verbosely list contents of archive
  f: Freshen files in archive           x: eXtract files with full pathname
<Switches>
  c: skip time-stamp Check              r: Recurse subdirectories
  e: Exclude paths from names           u: Update files (new and newer)
  f: Freshen existing files             v: enable multiple Volumes
  g: Garble with password               w: assign Work directory
  i: with no progress Indicator         x: eXclude selected files
  m: with Method 0, 1, 2, 3, 4          y: assume Yes on all queries
  n: only New files (not exist)        hk: enable ARJ-PROTECT damage protection
```

## PEAS

```
╣ Environment
MAIL=/var/mail/fox

# no port listening on localhost

╣ Analyzing Mongo Files (limit 70)
-rw-r--r-- 1 root root 2279 Jan 18  2018 /etc/fail2ban/filter.d/mongodb-auth.conf

╣ Analyzing Htpasswd Files (limit 70)
-rw-r--r-- 1 root root 47 Jan 18  2018 /usr/lib/python3/dist-packages/fail2ban/tests/files/config/apache-auth/basic/authz_owner/.htpasswd
username:$apr1$1f5oQUl4$21lLXSN7xQOPtNsj5s4Nk/
-rw-r--r-- 1 root root 47 Jan 18  2018 /usr/lib/python3/dist-packages/fail2ban/tests/files/config/apache-auth/basic/file/.htpasswd
username:$apr1$uUMsOjCQ$.BzXClI/B/vZKddgIAJCR.
-rw-r--r-- 1 root root 117 Jan 18  2018 /usr/lib/python3/dist-packages/fail2ban/tests/files/config/apache-auth/digest_anon/.htpasswd
username:digest anon:25e4077a9344ceb1a88f2a62c9fb60d8
05bbb04
anonymous:digest anon:faa4e5870970cf935bb9674776e6b26a
-rw-r--r-- 1 root root 62 Jan 18  2018 /usr/lib/python3/dist-packages/fail2ban/tests/files/config/apache-auth/digest/.htpasswd
username:digest private area:fad48d3a7c63f61b5b3567a4105bbb04
-rw-r--r-- 1 root root 62 Jan 18  2018 /usr/lib/python3/dist-packages/fail2ban/tests/files/config/apache-auth/digest_time/.htpasswd
username:digest private area:fad48d3a7c63f61b5b3567a4105bbb04
-rw-r--r-- 1 root root 62 Jan 18  2018 /usr/lib/python3/dist-packages/fail2ban/tests/files/config/apache-auth/digest_wrongrelm/.htpasswd
username:wrongrelm:99cd340e1283c6d0ab34734bd47bdc30
4105bbb04

# this is what asked the verification code on ssh login
╣ Searching unexpected auth lines in /etc/pam.d/sshd
auth required pam_google_authenticator.so

╣ Searching uncommon passwd files (splunk)
passwd file: /usr/share/lintian/overrides/passwd

╣ Mails (limit 50)
   664235      4 -rw-rw----   1 fox      mail         3494 Sep  5 00:31 /var/mail/fox
   664235      4 -rw-rw----   1 fox      mail         3494 Sep  5 00:31 /var/spool/mail/fox
   
# enumerated /var/mail/fox
# contains information that wrong password attempt was made on user fox (because I failed login multiple times)
```
