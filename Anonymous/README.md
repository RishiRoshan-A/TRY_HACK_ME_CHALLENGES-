# Lets start with an Nmap scan 

![img](1.png)

we found four open ports , Lets perform default script scan and service version detection scan on them

![img](2.png)

![img](3.png)

Since smb port is open on port 445 , lets use enum4linux tool to enemurate smb shares , usernames etc ..

![img](4.png)

We found one share named pics 

![img](5.png)

lets interact with it using the tool smbclient 

![img](6.png)

we found two pictures , but no juicy information is found in that . 

in nmap scan we found that ftp anonymous scan is allowed , lets login in ftp with username and password as Anonymous

![img](7.png)

we found that there are three files in the scripts folder 

![img](8.png)

Lets get that files to our kali machine 

![img](9.png)

lets view that files

![img](10.png)

seems like clean.sh is being executed in the ftp continusily , so lets modify the contents of clean.sh and upload a bash reverse shell in it 

![img](11.png)

![img](12.png)

now in ftp scripts directory lets upload our modified clean.sh , by using the command : put clean.sh

![img](13.png)

set up a nc lisener

![img](14.png)

after some seconds , we successfully got the reverse shell

![img](15.png)

we successfully found the user flag 

Lets escalate our privilage to get the root flag

since we dont the password of the current user , we cant use sudo -l command

so lets search for suid files 

![img](16.png)

![img](17.png)

found that we can able to execute env command with suid permission 

lets use gtfo bins for the escalation 

![img](18.png)

lets upgrade our shell to pty

![img](19.png)

![img](20.png)

We successfully found the root flag  


---------------------------------------------------------THE END------------------------------------------------------------------------------







