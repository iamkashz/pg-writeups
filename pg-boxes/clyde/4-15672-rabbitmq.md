# 4 :15672 rabbitmq

```
http://192.168.197.68:15672/
RabbitMQ Management
| login page

# default creds
guest:guest

# trying guest:guest
User can only log in via localhost 

$ gobuster dir -u http://192.168.197.68:15672 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
/index.html           (Status: 200) [Size: 1391]
/api                  (Status: 200) [Size: 29930]
/cli                  (Status: 200) [Size: 1603]
```
