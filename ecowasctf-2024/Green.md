
brief  `A lab that challenges your skills in exploiting web application vulnerabilities and leveraging misconfigurations in a Linux environment. You will need to apply many techniques to gain unauthorized access and obtain sensitive information on the target system.`

so basically two machines

two machine 

upload = 10.8.0.2
login = 10.8.0.3 
# enum 

```sql 
#nmap 

login

ports open on 
22 80 

22/tcp open   ssh         OpenSSH 7.6p1 Ubuntu 4ubuntu0.5 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 eb194b5822ab02fe6bce4034aa0179d7 (RSA)
|   256 32382837d660426b1223dca769394d96 (ECDSA)
|_  256 3cc1a6a478c43e7c142cdc7ad6b230e6 (ED25519)
80/tcp open   http        Apache httpd 2.4.29
Service Info: Host: 172.16.1.237; OS: Linux; CPE: cpe:/o:linux:linux_kernel

# upload 

uploadgreen_group_14073-rr3imo0jeuw9ux277vejk9qu7fpllawl 
two ports 

22 ssh and 80 http 

22/tcp open   ssh         OpenSSH 7.9p1 Debian 10+deb10u4 (protocol 2.0)
| ssh-hostkey: 
|   2048 c94c1f79ce338a373ba1ba5bda209687 (RSA)
|   256 57135df0b737387b21a3e05d93acfc19 (ECDSA)
|_  256 70783a10cb37623219e4dedcea983aaf (ED25519)
80/tcp open   http        nginx 1.14.2
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```


green:xR297gSTr  

my sql 

mysql> select * from users;
+----------+-----------+
| username | password  |
+----------+-----------+
| ubuntu   | abcit2020 |
| green    | xR297gSTr 


+------------+----------------+---------+---------+---------------+--------------------+----------+-------+
| Login      | Pass           | prenom  | nom     | ville         | email              | phone    | power |
+------------+----------------+---------+---------+---------------+--------------------+----------+-------+
| Nicolas    | nicolas        | Nicolas | Beau    | Nice          | Nicolas@live.fr    |  7539879 |     0 |
| superadmin | NoobDeveloper# | Abcit   | Abcit   | Paris         | testing@yopmail.fr |  7530000 |     2 |
| admin      | mouad          | admin   | admin   | Saint-Quentin | admin@abcit.fr     | 86433554 |     1 |
| sophia     | sophia         | Sophia  | So      | AyaSophia     | Sophia@live.fr     |  7876479 |     0 |
| Cindy      | cindy123       | Cindy   | Larcher | Rennes        | Cindy@live.fr      |  7536479 |     0 |
| abcit      | abcit          | abcit   | abcit   | abcit         | m@abcit.fr         |  9976566 |     0 |
