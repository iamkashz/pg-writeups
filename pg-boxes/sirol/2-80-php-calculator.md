# 2 :80 php calculator

```
http://192.168.197.54/
Landing Page | PHP calc

$ gobuster dir -u http://192.168.197.54/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
/index.php            (Status: 200) [Size: 595]

# tried looking at Burp; cant find anything
# cannot inject anything in fields.
```
