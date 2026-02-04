## Lets start with An Nmap Scan 

![img](1.png)

We found four open ports , lets perform service version detection and default script scan on it 

![img](2.png)

![img](3.png)

lets see the site running on port 80

![img](4.png)

lets use gobuter to enemurate some web directories

![img](5.png)

found a intresting directory named /joomla

![img](6.png)

lets use gobuster to enemurate some directories under /joomla

![img](7.png)
![img](8.png)

under /_test seems to be intresting 

![img](9.png)

Seems like the version is vulnerable and found an exploit 

lets copy that 

![img](10.png)

lets run that python exploit 

![img](11.png)

We successfully got the command shell 

lets see the contents of the log.txt

![img](12.png)

in log.txt we found the username and password 

we know that ssh port is open at 55007 , lets try to login into ssh with those credentials 

![img](13.png)

![img](14.png)

found a file name backup.sh , lets visit the contents of it 

![img](15.png)

We found the another username and password , lets upgrade to user stoner 

![img](16.png)

We successfully found the user.txt

Now lets escalte our privilage to find the root flag 

lets use sudo -l 

![img](17.png)

No juicy information is found 

now lets search for suid files 

![img](18.png)

we can exploit this suid permission for find command , lets use gtfo bins 

![img](19.png)

![img](20.png)

We successfully found the root flag 

---------------------------------------------------THE END-----------------------------------------------





