# 3 :80 apex hospital

```
http://192.168.137.145/
APEX Hospital Landing Page

# doctors (or users)
Walter White | wwalter@apex.offsec
Sarah Jhonson| jsarah@apex.offsec
William Anderson |awilliam@apex.offsec
Amanda Jepson | jamanda@apex.offsec

# using smb-enum
S-1-22-1-1000 Unix User\white (Local User)

# scheduler link on homepage
http://192.168.137.145/openemr/interface/login/login.php?site=default
OpenEMR Login

# from http-enum
http://192.168.137.145/filemanager/
Responsive File Manager
# 2 folders - images and documents
# documents is hosted via smb
# file upload is possible

http://192.168.137.145/source/
# shows directory listining of filemanager/

$ gobuster dir -u http://192.168.137.145 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
/index.html           (Status: 200) [Size: 28957]
/assets               (Status: 301) [Size: 319] [--> http://192.168.137.145/assets/]
/thumbs               (Status: 301) [Size: 319] [--> http://192.168.137.145/thumbs/]
/source               (Status: 301) [Size: 319] [--> http://192.168.137.145/source/]
```
