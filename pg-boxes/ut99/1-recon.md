# 1 recon

```
PORT     STATE SERVICE    VERSION
21/tcp   open  ftp        FileZilla ftpd
| ftp-syst:
|_  SYST: UNIX emulated by FileZilla
80/tcp   open  http       Apache httpd 2.4.16 (OpenSSL/1.0.1p PHP/5.6.12)
| http-methods:
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.16 (Win32) OpenSSL/1.0.1p PHP/5.6.12
|_http-title: Index of /
| http-enum:
|   /: Root directory w/ listing on 'apache/2.4.16 (win32) openssl/1.0.1p php/5.6.12'
|   /phpmyadmin/: phpMyAdmin
443/tcp  open  ssl/http   Apache httpd 2.4.16 (OpenSSL/1.0.1p PHP/5.6.12)
| http-methods:
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.16 (Win32) OpenSSL/1.0.1p PHP/5.6.12
|_http-title: Index of /
| ssl-cert: Subject: commonName=localhost
| Not valid before: 2009-11-10T23:48:47
|_Not valid after:  2019-11-08T23:48:47
|_ssl-date: TLS randomness does not represent time
3306/tcp open  mysql      MySQL (unauthorized)
6666/tcp open  irc        InspIRCd
6667/tcp open  irc        InspIRCd
| irc-info:
|   server: irc.madcowz.localdomain
|   users: 2
|   servers: 1
|   chans: 1
|   lusers: 3
|   lservers: 0
|   source ident: nmap
|   source host: 192.168.49.200
|_  error: Closing link: (nmap@192.168.49.200) [Client exited]
6668/tcp open  irc        InspIRCd
6669/tcp open  irc        InspIRCd
6689/tcp open  irc        InspIRCd
6692/tcp open  irc        InspIRCd
| irc-info:
|   server: irc.madcowz.localdomain
|   users: 3
|   servers: 1
|   chans: 1
|   lusers: 3
|   lservers: 0
|   source ident: nmap
|   source host: 192.168.49.200
|_  error: Closing link: (nmap@192.168.49.200) [Client exited]
6699/tcp open  irc        InspIRCd
6779/tcp open  irc        InspIRCd
6788/tcp open  irc        InspIRCd
6789/tcp open  irc        InspIRCd
6792/tcp open  irc        InspIRCd
6839/tcp open  irc        InspIRCd
6881/tcp open  irc        InspIRCd
6901/tcp open  irc        InspIRCd
6969/tcp open  irc        InspIRCd
7000/tcp open  irc        InspIRCd
| irc-info:
|   server: irc.madcowz.localdomain
|   users: 4
|   servers: 1
|   chans: 1
|   lusers: 4
|   lservers: 0
|   source ident: nmap
|   source host: 192.168.49.200
|_  error: Closing link: (nmap@192.168.49.200) [Client exited]
7001/tcp open  tcpwrapped
7007/tcp open  irc        InspIRCd
Service Info: Hosts: localhost, www.example.com, irc.madcowz.localdomain; OS: Windows; CPE: cpe:/o:microsoft:windows

# full scan
6660/tcp open  irc            InspIRCd
6661/tcp open  irc            InspIRCd
6662/tcp open  irc            InspIRCd
6663/tcp open  irc            InspIRCd
6664/tcp open  irc            InspIRCd
6665/tcp open  irc            InspIRCd
6670/tcp open  irc            InspIRCd
6671/tcp open  p4p-portal?
| fingerprint-strings:
|   LANDesk-RC, LDAPBindReq, NULL, afp:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6672/tcp open  vision_server?
| fingerprint-strings:
|   DNSVersionBindReqTCP, FourOhFourRequest, NULL, giop, oracle-tns:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6673/tcp open  vision_elmd?
| fingerprint-strings:
|   NULL, RTSPRequest, TerminalServer, X11Probe:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6674/tcp open  unknown
| fingerprint-strings:
|   FourOhFourRequest, NULL, ms-sql-s:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6675/tcp open  unknown
| fingerprint-strings:
|   LDAPBindReq, LPDString, NULL, SMBProgNeg:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6676/tcp open  unknown
| fingerprint-strings:
|   DNSVersionBindReqTCP, NULL, TLSSessionReq, ms-sql-s:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6677/tcp open  unknown
| fingerprint-strings:
|   DNSVersionBindReqTCP, GetRequest, NULL, NotesRPC:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6678/tcp open  vfbp?
| fingerprint-strings:
|   LANDesk-RC, LPDString, NULL, RTSPRequest:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6679/tcp open  osaut?
| fingerprint-strings:
|   HTTPOptions, LDAPBindReq, LDAPSearchReq, NCP, NULL, oracle-tns:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6680/tcp open  unknown
| fingerprint-strings:
|   DNSVersionBindReqTCP, FourOhFourRequest, HTTPOptions, Kerberos, LDAPBindReq, LPDString, NULL, NotesRPC, WMSRequest, oracle-tns:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6681/tcp open  unknown
| fingerprint-strings:
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, NULL, oracle-tns:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6682/tcp open  unknown
| fingerprint-strings:
|   DNSVersionBindReqTCP, JavaRMI, LPDString, NULL:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6683/tcp open  unknown
| fingerprint-strings:
|   DNSVersionBindReqTCP, LPDString, NULL:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6684/tcp open  irc            InspIRCd
6685/tcp open  unknown
| fingerprint-strings:
|   NULL, afp:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6686/tcp open  unknown
| fingerprint-strings:
|   NULL, RPCCheck, SIPOptions:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6687/tcp open  irc            InspIRCd
6688/tcp open  irc            InspIRCd
6690/tcp open  irc            InspIRCd
6691/tcp open  irc            InspIRCd
6693/tcp open  irc            InspIRCd
6694/tcp open  irc            InspIRCd
6695/tcp open  irc            InspIRCd
6696/tcp open  irc            InspIRCd
6697/tcp open  irc            InspIRCd
6698/tcp open  irc            InspIRCd
6700/tcp open  irc            InspIRCd
6701/tcp open  irc            InspIRCd
6702/tcp open  irc            InspIRCd
6704/tcp open  irc            InspIRCd
6705/tcp open  irc            InspIRCd
6706/tcp open  irc            InspIRCd
6707/tcp open  irc            InspIRCd
6708/tcp open  irc            InspIRCd
6709/tcp open  irc            InspIRCd
6710/tcp open  irc            InspIRCd
6711/tcp open  irc            InspIRCd
6712/tcp open  irc            InspIRCd
6713/tcp open  irc            InspIRCd
6714/tcp open  ibprotocol?
| fingerprint-strings:
|   DNSStatusRequestTCP, FourOhFourRequest, Kerberos, LDAPSearchReq, NCP, NULL, NotesRPC, SIPOptions, TerminalServer:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6715/tcp open  irc            InspIRCd
6716/tcp open  irc            InspIRCd
6717/tcp open  irc            InspIRCd
6718/tcp open  irc            InspIRCd
6719/tcp open  irc            InspIRCd
6720/tcp open  irc            InspIRCd
6721/tcp open  irc            InspIRCd
6722/tcp open  irc            InspIRCd
6723/tcp open  irc            InspIRCd
6724/tcp open  irc            InspIRCd
6725/tcp open  irc            InspIRCd
6726/tcp open  irc            InspIRCd
6727/tcp open  irc            InspIRCd
6728/tcp open  irc            InspIRCd
6729/tcp open  irc            InspIRCd
6730/tcp open  irc            InspIRCd
6731/tcp open  irc            InspIRCd
6732/tcp open  irc            InspIRCd
6733/tcp open  irc            InspIRCd
6734/tcp open  irc            InspIRCd
6735/tcp open  irc            InspIRCd
6736/tcp open  irc            InspIRCd
6737/tcp open  irc            InspIRCd
6738/tcp open  irc            InspIRCd
6739/tcp open  irc            InspIRCd
6740/tcp open  irc            InspIRCd
6741/tcp open  irc            InspIRCd
6742/tcp open  irc            InspIRCd
6743/tcp open  irc            InspIRCd
6744/tcp open  irc            InspIRCd
6745/tcp open  irc            InspIRCd
6746/tcp open  irc            InspIRCd
6747/tcp open  irc            InspIRCd
6748/tcp open  irc            InspIRCd
6749/tcp open  irc            InspIRCd
6750/tcp open  irc            InspIRCd
6751/tcp open  irc            InspIRCd
6752/tcp open  irc            InspIRCd
| irc-info:
|   server: irc.madcowz.localdomain
|   users: 3
|   servers: 1
|   chans: 1
|   lusers: 3
|   lservers: 0
|   source ident: nmap
|   source host: 192.168.49.200
|_  error: Closing link: (nmap@192.168.49.200) [Client exited]
6753/tcp open  irc            InspIRCd
6754/tcp open  irc            InspIRCd
6755/tcp open  irc            InspIRCd
6756/tcp open  irc            InspIRCd
6757/tcp open  irc            InspIRCd
6758/tcp open  irc            InspIRCd
6759/tcp open  irc            InspIRCd
6760/tcp open  irc            InspIRCd
6761/tcp open  irc            InspIRCd
6762/tcp open  irc            InspIRCd
6763/tcp open  irc            InspIRCd
6764/tcp open  irc            InspIRCd
6765/tcp open  irc            InspIRCd
6766/tcp open  irc            InspIRCd
6767/tcp open  irc            InspIRCd
6768/tcp open  irc            InspIRCd
6769/tcp open  irc            InspIRCd
6770/tcp open  irc            InspIRCd
6771/tcp open  irc            InspIRCd
6772/tcp open  irc            InspIRCd
6773/tcp open  irc            InspIRCd
6774/tcp open  irc            InspIRCd
6775/tcp open  irc            InspIRCd
6776/tcp open  irc            InspIRCd
6777/tcp open  irc            InspIRCd
6778/tcp open  irc            InspIRCd
6780/tcp open  irc            InspIRCd
6781/tcp open  unknown
| fingerprint-strings:
|   Kerberos, LDAPBindReq, NULL, RPCCheck:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6782/tcp open  unknown
| fingerprint-strings:
|   FourOhFourRequest, GetRequest, Kerberos, LDAPBindReq, NULL, TLSSessionReq:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6783/tcp open  unknown
| fingerprint-strings:
|   GetRequest, LPDString, NCP, NULL, RTSPRequest, TLSSessionReq, TerminalServer, WMSRequest, ms-sql-s:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6784/tcp open  irc            InspIRCd
6785/tcp open  dgpf-exchg?
| fingerprint-strings:
|   GenericLines, Help, JavaRMI, Kerberos, NCP, NULL, NotesRPC, SMBProgNeg, SSLSessionReq, TerminalServer, ms-sql-s:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6786/tcp open  irc            InspIRCd
6787/tcp open  irc            InspIRCd
6790/tcp open  irc            InspIRCd
6791/tcp open  hnm?
| fingerprint-strings:
|   LDAPSearchReq, LPDString, NULL, NotesRPC:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6793/tcp open  irc            InspIRCd
6794/tcp open  irc            InspIRCd
6795/tcp open  irc            InspIRCd
6796/tcp open  irc            InspIRCd
6797/tcp open  irc            InspIRCd
6798/tcp open  irc            InspIRCd
6799/tcp open  irc            InspIRCd
6800/tcp open  irc            InspIRCd
6801/tcp open  irc            InspIRCd
6802/tcp open  irc            InspIRCd
6803/tcp open  irc            InspIRCd
6804/tcp open  irc            InspIRCd
6805/tcp open  irc            InspIRCd
6806/tcp open  irc            InspIRCd
6807/tcp open  irc            InspIRCd
6808/tcp open  irc            InspIRCd
6809/tcp open  irc            InspIRCd
6810/tcp open  irc            InspIRCd
6811/tcp open  irc            InspIRCd
6812/tcp open  irc            InspIRCd
6813/tcp open  irc            InspIRCd
6814/tcp open  irc            InspIRCd
| irc-info:
|   server: irc.madcowz.localdomain
|   users: 3
|   servers: 1
|   chans: 1
|   lusers: 3
|   lservers: 0
|   source ident: nmap
|   source host: 192.168.49.200
|_  error: Closing link: (nmap@192.168.49.200) [Client exited]
6815/tcp open  irc            InspIRCd
6816/tcp open  irc            InspIRCd
6817/tcp open  irc            InspIRCd
6818/tcp open  irc            InspIRCd
6819/tcp open  irc            InspIRCd
6820/tcp open  irc            InspIRCd
6821/tcp open  irc            InspIRCd
6822/tcp open  irc            InspIRCd
6823/tcp open  irc            InspIRCd
6824/tcp open  irc            InspIRCd
6825/tcp open  irc            InspIRCd
6826/tcp open  irc            InspIRCd
6827/tcp open  irc            InspIRCd
6828/tcp open  unknown
| fingerprint-strings:
|   NULL, ms-sql-s:
|_    ERROR :Closing link: (unknown@192.168.49.200) [No more connections allowed from your host via this connect class (local)]
6829/tcp open  irc            InspIRCd
6830/tcp open  irc            InspIRCd
6831/tcp open  irc            InspIRCd
6832/tcp open  irc            InspIRCd
6833/tcp open  irc            InspIRCd
6834/tcp open  irc            InspIRCd
6835/tcp open  irc            InspIRCd
6836/tcp open  irc            InspIRCd
6837/tcp open  irc            InspIRCd
6838/tcp open  irc            InspIRCd
6840/tcp open  irc            InspIRCd
6841/tcp open  irc            InspIRCd
6842/tcp open  irc            InspIRCd
6843/tcp open  irc            InspIRCd
6844/tcp open  irc            InspIRCd
6845/tcp open  irc            InspIRCd
6846/tcp open  irc            InspIRCd
6847/tcp open  irc            InspIRCd
6848/tcp open  irc            InspIRCd
6849/tcp open  irc            InspIRCd
6850/tcp open  irc            InspIRCd
6851/tcp open  irc            InspIRCd
6852/tcp open  irc            InspIRCd
6853/tcp open  irc            InspIRCd
| irc-info:
|   server: irc.madcowz.localdomain
|   users: 2
|   servers: 1
|   chans: 1
|   lusers: 3
|   lservers: 0
|   source ident: nmap
|   source host: 192.168.49.200
|_  error: Closing link: (nmap@192.168.49.200) [Client exited]
6854/tcp open  irc            InspIRCd
6855/tcp open  irc            InspIRCd
6856/tcp open  irc            InspIRCd
6857/tcp open  irc            InspIRCd
6858/tcp open  irc            InspIRCd
6859/tcp open  irc            InspIRCd
6860/tcp open  irc            InspIRCd
6861/tcp open  irc            InspIRCd
6862/tcp open  irc            InspIRCd
6863/tcp open  irc            InspIRCd
6864/tcp open  irc            InspIRCd
6865/tcp open  irc            InspIRCd
6866/tcp open  irc            InspIRCd
6867/tcp open  irc            InspIRCd
6868/tcp open  irc            InspIRCd
6869/tcp open  irc            InspIRCd
6870/tcp open  irc            InspIRCd
6871/tcp open  irc            InspIRCd
6872/tcp open  irc            InspIRCd
6873/tcp open  irc            InspIRCd
6874/tcp open  irc            InspIRCd
6875/tcp open  irc            InspIRCd
6876/tcp open  irc            InspIRCd
6877/tcp open  irc            InspIRCd
6878/tcp open  irc            InspIRCd
6879/tcp open  irc            InspIRCd
6880/tcp open  irc            InspIRCd
6882/tcp open  irc            InspIRCd
6883/tcp open  irc            InspIRCd
6884/tcp open  irc            InspIRCd
6885/tcp open  irc            InspIRCd
6886/tcp open  irc            InspIRCd
6887/tcp open  irc            InspIRCd
6888/tcp open  irc            InspIRCd
6889/tcp open  irc            InspIRCd
6890/tcp open  irc            InspIRCd
6891/tcp open  irc            InspIRCd
6892/tcp open  irc            InspIRCd
6893/tcp open  irc            InspIRCd
6894/tcp open  irc            InspIRCd
6895/tcp open  irc            InspIRCd
6896/tcp open  irc            InspIRCd
6897/tcp open  irc            InspIRCd
6898/tcp open  irc            InspIRCd
6899/tcp open  irc            InspIRCd
| irc-info:
|   server: irc.madcowz.localdomain
|   users: 2
|   servers: 1
|   chans: 1
|   lusers: 3
|   lservers: 0
|   source ident: nmap
|   source host: 192.168.49.200
|_  error: Closing link: (nmap@192.168.49.200) [Client exited]
6900/tcp open  irc            InspIRCd
6902/tcp open  irc            InspIRCd
6903/tcp open  irc            InspIRCd
6904/tcp open  irc            InspIRCd
6905/tcp open  irc            InspIRCd
6906/tcp open  irc            InspIRCd
6907/tcp open  irc            InspIRCd
6908/tcp open  irc            InspIRCd
6909/tcp open  irc            InspIRCd
6910/tcp open  irc            InspIRCd
6911/tcp open  irc            InspIRCd
6912/tcp open  irc            InspIRCd
6913/tcp open  irc            InspIRCd
6914/tcp open  irc            InspIRCd
6915/tcp open  irc            InspIRCd
6916/tcp open  irc            InspIRCd
6917/tcp open  irc            InspIRCd
6918/tcp open  irc            InspIRCd
| irc-info:
|   server: irc.madcowz.localdomain
|   users: 4
|   servers: 1
|   chans: 1
|   lusers: 4
|   lservers: 0
|   source ident: nmap
|   source host: 192.168.49.200
|_  error: Closing link: (nmap@192.168.49.200) [Client exited]
6919/tcp open  irc            InspIRCd
6920/tcp open  irc            InspIRCd
6921/tcp open  irc            InspIRCd
6922/tcp open  irc            InspIRCd
6923/tcp open  irc            InspIRCd
6924/tcp open  irc            InspIRCd
6925/tcp open  irc            InspIRCd
6926/tcp open  irc            InspIRCd
6927/tcp open  irc            InspIRCd
6928/tcp open  irc            InspIRCd
6929/tcp open  irc            InspIRCd
6930/tcp open  irc            InspIRCd
6931/tcp open  irc            InspIRCd
6932/tcp open  irc            InspIRCd
6933/tcp open  irc            InspIRCd
6934/tcp open  irc            InspIRCd
6935/tcp open  irc            InspIRCd
6936/tcp open  irc            InspIRCd
6937/tcp open  irc            InspIRCd
6938/tcp open  irc            InspIRCd
6939/tcp open  irc            InspIRCd
6940/tcp open  irc            InspIRCd
6941/tcp open  irc            InspIRCd
6942/tcp open  irc            InspIRCd
6943/tcp open  irc            InspIRCd
6944/tcp open  irc            InspIRCd
| irc-info:
|   server: irc.madcowz.localdomain
|   users: 4
|   servers: 1
|   chans: 1
|   lusers: 4
|   lservers: 0
|   source ident: nmap
|   source host: 192.168.49.200
|_  error: Closing link: (nmap@192.168.49.200) [Client exited]
6945/tcp open  irc            InspIRCd
6946/tcp open  irc            InspIRCd
6947/tcp open  irc            InspIRCd
6948/tcp open  irc            InspIRCd
6949/tcp open  irc            InspIRCd
6950/tcp open  irc            InspIRCd
6951/tcp open  irc            InspIRCd
6952/tcp open  irc            InspIRCd
6953/tcp open  irc            InspIRCd
6954/tcp open  irc            InspIRCd
6955/tcp open  irc            InspIRCd
6956/tcp open  irc            InspIRCd
6957/tcp open  irc            InspIRCd
6958/tcp open  irc            InspIRCd
6959/tcp open  irc            InspIRCd
6960/tcp open  irc            InspIRCd
6961/tcp open  irc            InspIRCd
6962/tcp open  irc            InspIRCd
6963/tcp open  irc            InspIRCd
6964/tcp open  irc            InspIRCd
6965/tcp open  irc            InspIRCd
6966/tcp open  irc            InspIRCd
6967/tcp open  irc            InspIRCd
6968/tcp open  irc            InspIRCd
6970/tcp open  irc            InspIRCd
6971/tcp open  irc            InspIRCd
6972/tcp open  irc            InspIRCd
6973/tcp open  irc            InspIRCd
6974/tcp open  irc            InspIRCd
6975/tcp open  irc            InspIRCd
6976/tcp open  irc            InspIRCd
6977/tcp open  irc            InspIRCd
6978/tcp open  irc            InspIRCd
6979/tcp open  irc            InspIRCd
6980/tcp open  irc            InspIRCd
6981/tcp open  irc            InspIRCd
6982/tcp open  irc            InspIRCd
6983/tcp open  irc            InspIRCd
6984/tcp open  irc            InspIRCd
6985/tcp open  irc            InspIRCd
6986/tcp open  irc            InspIRCd
6987/tcp open  irc            InspIRCd
6988/tcp open  irc            InspIRCd
6989/tcp open  irc            InspIRCd
6990/tcp open  irc            InspIRCd
6991/tcp open  irc            InspIRCd
6992/tcp open  irc            InspIRCd
6993/tcp open  irc            InspIRCd
6994/tcp open  irc            InspIRCd
6995/tcp open  irc            InspIRCd
6996/tcp open  irc            InspIRCd
6997/tcp open  irc            InspIRCd
6998/tcp open  irc            InspIRCd
6999/tcp open  irc            InspIRCd
```
