# RECON 

Lets start with the Nmap full port scan on our target ip

![img](1.png)

We found that only port 80 is open on our target machine , lets perform service version detection and default scan on it 

![img](2.png)

seems like apache has been hosted on port 80 , lets visit the site 

![img](3.png)

Lets enemurate web directories using gobuster 

![img](4.png) 

we found a path /webdav 

while accessing /webdav in the apache site it asked for username and password 

so lets search for default username and password for webdav 

![img](5.png)

the default credentials wampp/xampp has worked 

## EXPLOITATION 

Lets use davtest tool to check which file extension we can upload and execute in the webdav 

![img](6.png)

![img](7.png)

seems like we can successfully upload and execute the php files 

therefore lets upload the php-reverse-shell.php from pentest monkey , change the ip and port 

lets use cadaver to upload our php-reverse-shell.php in webdav 

![img](8.png)

use nc to listen on the port we specified and access the php file we uploaded

![img](9.png)

our php code got executed and we successfully got the reverse shell

in the home directory we found a user named merlin and inside the merlin directory found the user.txt file 

![img](10.png)

## PRIVILEGE ESCALATION

sudo -l --> command shows that what the current user can execute with root privileges 

![img](11.png)

we can execute cat command with root privileges 

so lets view the root.txt file under root directory with cat command 

![img](12.png)

Successfully found the user flag and the root flag 


--------------------------------------------------THE END---------------------------------------






