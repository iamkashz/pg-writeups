# 1 recon

```
PORT     STATE SERVICE     VERSION
21/tcp   open  ftp         vsftpd 3.0.2
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst:
|   STAT:
| FTP server status:
|      Connected to ::ffff:192.168.49.174
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 3.0.2 - secure, fast, stable
|_End of status
22/tcp   open  ssh         OpenSSH 7.4 (protocol 2.0)
80/tcp   open  http        Apache httpd 2.4.6 ((CentOS) OpenSSL/1.0.2k-fips PHP/5.4.16)
| http-methods:
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.6 (CentOS) OpenSSL/1.0.2k-fips PHP/5.4.16
|_http-title: Apache HTTP Server Test Page powered by CentOS
111/tcp  open  rpcbind     2-4 (RPC #100000)
| rpcinfo:
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|_  100000  3,4          111/udp6  rpcbind
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: SAMBA)
445/tcp  open  netbios-ssn Samba smbd 4.10.4 (workgroup: SAMBA)
3306/tcp open  mysql       MariaDB (unauthorized)
8081/tcp open  ssl/http    Apache httpd 2.4.6 ((CentOS) OpenSSL/1.0.2k-fips PHP/5.4.16)
|_http-server-header: Apache/2.4.6 (CentOS) OpenSSL/1.0.2k-fips PHP/5.4.16
|_http-title: Site doesn't have a title (text/html; charset=UTF-8).
| http-enum:
|   /login.php: Possible admin folder
|   /README: Interesting, a readme.
|_  /icons/: Potentially interesting folder w/ directory listing
| ssl-cert: Subject: commonName=quackerjack/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--
| Not valid before: 2020-06-22T19:28:25
|_Not valid after:  2021-06-22T19:28:25
|_ssl-date: TLS randomness does not represent time
Service Info: Host: QUACKERJACK; OS: Unix

Host script results:
|_clock-skew: mean: 1h19m59s, deviation: 2h18m35s, median: -1s
| smb-os-discovery:
|   OS: Windows 6.1 (Samba 4.10.4)
|   Computer name: quackerjack
|   NetBIOS computer name: QUACKERJACK\x00
|   Domain name: \x00
|   FQDN: quackerjack
|_  System time: 2021-08-30T13:17:11-04:00
| smb-security-mode:
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode:
|   2.02:
|_    Message signing enabled but not required
| smb2-time:
|   date: 2021-08-30T17:17:12
|_  start_date: N/A
```
