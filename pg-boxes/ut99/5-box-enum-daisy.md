# 5 box enum daisy

## PowerUp.ps1

```
$ powershell.exe -exec bypass -Command "& {Import-Module .\PowerUp.ps1; Invoke-AllChecks}"
[*] Checking for unquoted service paths...
ServiceName   : FoxitCloudUpdateService
Path          : C:\Program Files (x86)\Foxit Software\Foxit Reader\Foxit Cloud\
                FCUpdateService.exe
StartName     : LocalSystem
AbuseFunction : Write-ServiceBinary -ServiceName 'FoxitCloudUpdateService' -Pat
                h <HijackPath>

ServiceName   : InspIRCd
Path          : C:\Program Files (x86)\InspIRCd\inspircd.exe
StartName     : NT AUTHORITY\NetworkService
AbuseFunction : Write-ServiceBinary -ServiceName 'InspIRCd' -Path <HijackPath>

[*] Checking %PATH% for potentially hijackable .dll locations...
HijackablePath : C:\Python\Scripts\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Python\Scripts\\wlbsctrl.dll'
                 -Command '...'

HijackablePath : C:\Python\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Python\\wlbsctrl.dll' -Command
                  '...'
				  

# there is a sqlite file in C:\Users\daisy
c:\Users\daisy>dir
Directory of c:\Users\daisy
[truncated]
08/12/2020  01:04 PM            79,872 murmur.sqlite

# using sqlitebrowser on kali to open it
# table: config
certificate
-----BEGIN CERTIFICATE-----
MIIDSzCCAjOgAwIBAgIBATANBgkqhkiG9w0BAQUFADAuMSwwKgYDVQQDDCNNdXJt
dXIgQXV0b2dlbmVyYXRlZCBDZXJ0aWZpY2F0ZSB2MjAeFw0xNTEwMDEwNjIwMDla
Fw0zNTA5MjYwNjIwMDlaMC4xLDAqBgNVBAMMI011cm11ciBBdXRvZ2VuZXJhdGVk
IENlcnRpZmljYXRlIHYyMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA
rbPDJ6ilKF4Uhrc0mJJQCkC6q3y3wZ65XUbTZwt5c1CbOUvWpJ8c6eOvwJxMrvfY
QnoQYKQpsrMj/pO/SxMCDrbnSX2nZsETligsQNImGUCGLbfl7Ij/V53AkcwFDbqt
XlPNjRdK1nAEJM+kgf2fM4copTQWCxvHXVdPO7V7hbi5KMFW0yX3XIOte2z0ouD9
AYDm7UBNvyCqMli/c31FVPHJKkfQ2Zozeg3W3wuXJpz1ap3E7JuK3lp/Rl4200EF
SEx9EHsI4dTWZPjTuaXQl+BkpDxKLr0aD0Oyu5Y8FeUMsPUNeMPbiFikfMQycdE7
DohiZF/O5rz+wEWAmOybHQIDAQABo3QwcjAMBgNVHRMBAf8EAjAAMB0GA1UdJQQW
MBQGCCsGAQUFBwMBBggrBgEFBQcDAjAdBgNVHQ4EFgQUCcyqPXe1TKG7CdRN8Nph
soxZzXowJAYJYIZIAYb4QgENBBcWFUdlbmVyYXRlZCBmcm9tIG11cm11cjANBgkq
hkiG9w0BAQUFAAOCAQEAUDCAnQU8nCsNw0KtblKeURGskqoxacCr66UKroTCFzDT
BIFaTGfAMZL7zRFUpxRiiw8zjcHZYEI0aZBVi0swtU8G/UcfO+txj5olHeU+jeKv
+X2/gR3yK1mFsmJAoAWq8w503hu9e76LZjrQgTj/JWsy6De/KyJRonDMODyFguSS
E/URm2XiS8VXjbQ/K6lu8UEGbFgRwiL3McEAznG9my4KI41Ihop0onMnhU+hk75Q
bO+0KayksuKApEeX8DN8NzHxK5YRwUtRRq0AoNw3FiSyAA5wJFHgs2BouBKMtUwl
boviAJtPquPlUoAaYZG+pnzeF7Kgitoa0z+71fBsXA==
-----END CERTIFICATE-----

key
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEArbPDJ6ilKF4Uhrc0mJJQCkC6q3y3wZ65XUbTZwt5c1CbOUvW
pJ8c6eOvwJxMrvfYQnoQYKQpsrMj/pO/SxMCDrbnSX2nZsETligsQNImGUCGLbfl
7Ij/V53AkcwFDbqtXlPNjRdK1nAEJM+kgf2fM4copTQWCxvHXVdPO7V7hbi5KMFW
0yX3XIOte2z0ouD9AYDm7UBNvyCqMli/c31FVPHJKkfQ2Zozeg3W3wuXJpz1ap3E
7JuK3lp/Rl4200EFSEx9EHsI4dTWZPjTuaXQl+BkpDxKLr0aD0Oyu5Y8FeUMsPUN
eMPbiFikfMQycdE7DohiZF/O5rz+wEWAmOybHQIDAQABAoIBAQCeTOsXo3wQk9zF
AQWv3fePwHneeuTEUbDAryFOEYj3bIhp6RGOKWuiQ9wR/t9rvXea7b8rM7DEqLmu
8lstQf9oBYw2z4rV/DOrbqUV1e7eqI0f8S5bKGb8JEoxFOuuHWiORHVZldagIqnE
Gm/j/40s2opSNGu6Z/CCwmT1F2mg7Lz7xKItyX5R18cSj0saJuiOz5NotRqKmkBv
HE6YtZ6aXaqZd1zz5T/rXTXNfCVCvCW1/SdTW+Jw25z6Q3HMqmx6TXBzogCyMjug
hpjoS2J87qtSVdmYZWc4r9HT9Z8u3WMVmn0qvLbQSRzwNt1zTWslpvo8+P4RZ4r2
DSDuoaDBAoGBAN5a3gL7fJh4sHINoTpOKX3FfKIEOEzoVW1C0dYYfTWfIuO/0d8d
v0VdQLf/NogJS6P/swUr3shhbyb9S0uuvtwjcD2xtcvLBZcUI76CESdNKuJTbEn8
2C81EXh6CbZA01nhCCxymezQ5t67//V84WT9Cv7XXUQhgkW+vxt3FjPJAoGBAMf8
SK4gQTkfV+vxgqqCLTYWL4z6WHEskRYhecVsgRsaY1DiWwiQxN+5qgurRBqQRvO2
Fdq6cKDdDzit4mx5pAr3Ori8Gw5rbuBSImi59VRudbqL/eyAuyU0byrInomIlUCC
1bZ9oWIkCEhouC2V6m8BX30QD4z2mZe/GLBUvQ61AoGAWxjbUFl8SHNZxsByx5Jy
SUb5st8LueaN6T+w/If39FoIT0qtTz2+uUplU3zJ+J3mUYBW9c1tbqcMhOrNSGqF
Y2dZes0t8BpzZdwocMqVAIcLBMKs4PsoDt8tEzDcfcC9Vlttn9gr2+wSSjq3uPm6
1kcdlB7j5R/dYXmujjAR9pECgYBx78AQxHukacETwaLqNgRAHl+0+CRPRk7axvOz
kN/1axFOUcf/l0szE3pX75l7cNubmg/VcAce/xLe/eJUXvEg9j3UZgccLgUbdG/6
LoghNFWKlJt0lNsKlVcIjwgT32b5PBE6SVUaruCxMEhOYG0SFTwr6myRqSVUmSEd
xQl5SQKBgFxIglRfwMQl1otJ/b4zOCcScq2HEMrOLpawTYO3z8OZrIx9Ylh/+76r
rm6HGeSBdSpjDXtV51eKvAz+vBgXKP+GYRccQBWU9LpVyAXRo24LWGv2drN3/bWg
y16dsbF5QWKd+efEXmnXzlGAbN+aH2Wc3b8VAdh70UsbMBQwIeV0
-----END RSA PRIVATE KEY-----

# table: user_info
user_id | value
2 | d5d9bba5a4a6bd45c28e825a2954b97bfc56969e
1 | ef120c98664439173d6a4545d264d506183775de

# table: users
name | pw
SuperUser | c01ddbea603260933ca25bda4a67079216947ed6

# cracked hash
c01ddbea603260933ca25bda4a67079216947ed6:sha1:cooows
# tried PsExec - bad password for all users
```
