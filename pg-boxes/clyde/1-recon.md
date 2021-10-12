# 1 recon

```
PORT      STATE SERVICE VERSION
21/tcp    open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| drwxr-xr-x    2 ftp      ftp          4096 Apr 24  2020 PackageKit
| drwxr-xr-x    5 ftp      ftp          4096 Apr 24  2020 apache2
| drwxr-xr-x    5 ftp      ftp          4096 Sep 21  2020 apt
| drwxr-xr-x    2 ftp      ftp          4096 Apr 22  2020 dbus
| drwxr-xr-x    2 ftp      ftp          4096 Apr 24  2020 dhcp
| drwxr-xr-x    7 ftp      ftp          4096 Sep 21  2020 dpkg
| drwxr-xr-x    2 ftp      ftp          4096 Apr 20  2020 git
| drwxr-xr-x    2 ftp      ftp          4096 Apr 24  2020 initramfs-tools
| drwxr-xr-x    2 ftp      ftp          4096 May 07  2020 logrotate
| drwxr-xr-x    2 ftp      ftp          4096 Sep 08  2019 misc
| drwxr-xr-x    5 ftp      ftp          4096 Mar 10 20:43 mysql
| drwxr-xr-x    2 ftp      ftp          4096 Jul 13  2017 os-prober
| drwxr-xr-x    2 ftp      ftp          4096 Apr 24  2020 pam
| drwxr-xr-x    4 ftp      ftp          4096 Apr 24  2020 php
| drwx------    3 ftp      ftp          4096 Apr 24  2020 polkit-1
| drwxr-xr-x    2 ftp      ftp          4096 Apr 24  2020 python
| drwxr-xr-x    3 ftp      ftp          4096 May 08  2020 rabbitmq
| drwxr-xr-x    2 ftp      ftp          4096 Apr 24  2020 sgml-base
| drwxr-xr-x    6 ftp      ftp          4096 Apr 22  2020 systemd
| drwxr-xr-x    3 ftp      ftp          4096 Apr 30  2020 ucf
|_Only 20 shown. Use --script-args ftp-anon.maxlist=-1 to see all.
22/tcp    open  ssh     OpenSSH 7.4p1 Debian 10+deb9u7 (protocol 2.0)
| ssh-hostkey:
|   2048 df:63:99:a4:cf:79:00:c8:b1:d6:67:97:81:4d:4f:af (RSA)
|   256 bd:9b:35:41:34:a2:5a:4c:fa:1b:9f:f1:36:f3:6a:fd (ECDSA)
|_  256 db:96:ee:8d:29:2b:f4:a3:58:b2:fb:c1:ac:65:92:48 (ED25519)
80/tcp    open  http    Apache httpd 2.4.25 ((Debian))
|_http-server-header: Apache/2.4.25 (Debian)
|_http-title: Apache2 Debian Default Page: It works
65000/tcp open  unknown
4369/tcp  open  epmd    Erlang Port Mapper Daemon
| epmd-info:
|   epmd_port: 4369
|   nodes:
|_    rabbit: 65000
15672/tcp open  http    Cowboy httpd
|_http-server-header: Cowboy
|_http-title: RabbitMQ Management
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel
```
