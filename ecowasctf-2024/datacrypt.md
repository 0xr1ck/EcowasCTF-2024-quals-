
brief `This scenario represents a typical case of a Windows machine hit by ransomware, a malware that encrypts all personal victim data in exchange for a ransom As an investigator, you must first locate and analyze the malware using reverse engineering techniques to be able to understand its infection mechanism. Once you deduce the encryption key used by the malware, you can decrypt and submit the encrypted flag located at C:\Users\Administrator\Desktop\proof.txt. The infected machine is accessible through RDP: Administrator:bJEhU7R7oNYv5weWf*yhig6SnM.-Yg4s Sysinternals Suite and Ghidra are in Downloads in the infected machine`

TARGET = 10.8.0.2
username = Aministrator 
password = bJEhU7R7oNYv5weWf*yhig6SnM.-Yg4s
## RECON 

got the decryptor and its dll 
reverse engineer it 
and decrypt the flag 

```powershell

Microsoft Windows [Version 10.0.14393]
(c) 2016 Microsoft Corporation. All rights reserved.

C:\Users\Administrator>cd Desktop

C:\Users\Administrator\Desktop>copy proof.txt.secdojo \\10.8.0.3\share
        1 file(s) copied.

C:\Users\Administrator\Desktop>getmac

Physical Address    Transport Name
=================== ==========================================================
0A-1C-B7-CC-4D-E1   \Device\Tcpip_{99013294-7D60-405C-9B8D-E7F3AA1F6467}
00-FF-A3-EC-A2-13   \Device\Tcpip_{A3ECA213-D4D9-4C7D-A435-8532A9843266}

C:\Users\Administrator\Desktop>hostname
EC2AMAZ-59S0107
```

```python
using cyberchef does the work 
md5 sum both hostname and mac-address 
give you this 
846a60b7c77fad8843b50c284c922108
┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/datacrypt]
└──╼ $wine decryptor101.exe 846a60b7c77fad8843b50c284c922108 proof.txt.secdojo 
Infected_group_16697-xqwx3mldu5yfnilj7q9iki8o8eulygr5

┌─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/datacrypt]
└──╼ $
```

and that gives us the flag `Infected_group_16697-xqwx3mldu5yfnilj7q9iki8o8eulygr5`

```sql
┌─[✗]─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/datacrypt]
└──╼ $wine decryptor101.exe 
Usage : decryptor101.exe <key> <encrypted_file>
┌─[✗]─[m1cr0@veric]─[~/Desktop/ctfs/ecowasCTF/datacrypt]
└──╼ $wine decryptor101.exe 846a60b7c77fad8843b50c284c922108 proof.txt.secdojo 
Infected_group_16697-xqwx3mldu5yfnilj7q9iki8o8eulygr5
```

when you decompile the r101.dll file it takes the computer mac address and hostname and md5 sum it 
and encrypts files 
to decrypt it should go the same way using cyberchef should do the work faster or you can write a script using hashlib 
here is a simple script i wrote

```python

import hashlib

# replace the hostname and macaddr
strings = "Hostname&Macaddress"
# encoding strings
pound = hashlib.md5(strings.encode())
# outPut
print("key: ", end="")
print(pound.hexdigest())
```

