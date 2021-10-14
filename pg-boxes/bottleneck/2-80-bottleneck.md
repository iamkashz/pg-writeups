# 2 :80 bottleneck

```
http://192.168.65.22/
Bottleneck website landing page

$ gobuster dir -u http://192.168.65.22 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
/img                  (Status: 301) [Size: 162] [--> http://192.168.65.22/img/]
/index.php            (Status: 200) [Size: 10175]
/css                  (Status: 301) [Size: 162] [--> http://192.168.65.22/css/]
/js                   (Status: 301) [Size: 162] [--> http://192.168.65.22/js/]
/vendor               (Status: 301) [Size: 162] [--> http://192.168.65.22/vendor/]
/image_gallery.php    (Status: 200) [Size: 6381]

http://192.168.65.22/image_gallery.php
random images on page

# cant find anything, using burp to intercept.
# when looking at request for /image_gallery.php; there's a subsequent request to
GET /image_gallery.php?t=1629343132&f=Ym90dGxlbmVja19kb250YmUucG5n

$ echo "Ym90dGxlbmVja19kb250YmUucG5n" | base64 -d
bottleneck_dontbe.png

# even source code shows images being loaded as 
<img class="img-fluid" src="image_gallery.php?t=1629343196&f=Ym90dGxlbmVja19kb250YmUucG5n" alt="">

# value of t= keeps changing everytime the page is reloaded; possibly a timestamp
```
