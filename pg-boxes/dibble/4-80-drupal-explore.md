# 4 :80 drupal explore

```
http://192.168.213.110/user/register
# regsitering kashz:kashz
Thank you for applying for an account. Your account is currently pending approval by the site administrator.
In the meantime, a welcome message with further instructions has been sent to your email address. 
# trying to login
Error message: The username kashz has not been activated or is blocked.

# enumerating using register page
# Trying username: admin
The username admin is already taken.

# enumerating number of users using /user/<> until error
http://192.168.213.110/user/3 => ERROR
# so probably only admin, as kashz could be the second username; but account is not activated.

# trying to find hidden page by enumerating /node/<int> where int=1-100
# no hidden pages

# checking if php plugin is installed /modules/php (403 = good)
404 Not Found > not installed.

$ droopescan scan drupal -u http://192.168.213.110/
[+] Themes found:
    gin http://192.168.213.110/themes/gin/
        http://192.168.213.110/themes/gin/README.md
        http://192.168.213.110/themes/gin/LICENSE.txt

[+] Possible interesting urls found:
    Default admin - http://192.168.213.110/user/login

[+] Possible version(s):
    9.0.6
    9.0.7

[+] No plugins found.

[+] Scan finished (0:02:59.271309 elapsed)
```
