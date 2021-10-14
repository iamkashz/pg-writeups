# 3 :25 smtp

```
# nmapAutomator | smtp-user-enum -U /usr/share/wordlists/metasploit/unix_users.txt -t "192.168.125.97"

192.168.125.97: avahi exists
192.168.125.97: postfix exists
192.168.125.97: postmaster exists
192.168.125.97: root exists
192.168.125.97: saned exists
192.168.125.97: www-data exists

$ smtp-user-enum -U /usr/share/seclists/Usernames/Names/names.txt -t "192.168.125.97"

######## Scan started at Wed Sep  1 12:44:18 2021 #########
192.168.125.97: janis exists
192.168.125.97: paige exists
192.168.125.97: root exists
192.168.125.97: terry exists
192.168.125.97: walter exists
```
