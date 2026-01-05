## Lets start with an Nmap scan

![img](1.png)

We found four open ports lets perform default script scan and service version detection scan on them

![img](2.png)
![img](3.png)

Lets visit the site running on port 80

![img](4.png)

It is showing us a login page , but dont know any credentials 

Lets use gobuster to enemurate the web directories 

![img](5.png)

![img](6.png)

Lets visit /cloud path 

![img](7.png)

seems like we can upload images , lets try uploading a php reverse shell , we cant able to upload file with .php extension , so lets try to bypass it 

after trying many extensions this one worked : .php#.png

![img](8.png)

![img](9.png)

set up a nc listener and click on upload and we got a reverse shell

![img](10.png)

In home directory found a user named sysadmin but we cant able to read the local.txt file as our permission is denied 

While searching for files owned by sysadmin

command : find / -type f -user sysadmin 2>/dev/null 

found a file dataset.kdbx in opt directory 

![img](11.png)

while researching about the file , found that it is a highly encrypted password database and needs a KeePass to decrypt it 

![img](12.png)
![img](13.png)

Lets start a python server and get the file using wget 

![img](14.png)

![img](15.png)

Lets crack the keepass using john , lets convert the file into an haah format that john can crack

![img](16.png)

we successfully found the keepass

Since i cant able to install keepassxc tool i am using an alternative tool kpcli for it to open or read dataset.kdbx

![img](17.png)

![img](18.png)

Lets see the entries 0 

![img](19.png)

We can able to copy the password , even it is coted with red box

Since we found the username and password , lets login into ssh 

![img](20.png)

![img](21.png)

We successfully found the local.txt

Lets escalate our privilage to view the root flag 

we cant able to run sudo as user sysadmin

![img](22.png)

I noticed a folder named script inside it there is a file called script.php

![img](23.png)

while visitng the folder backups where backup.zip has been run by root every minute , means this script has been executed 

Since we cant able to remove or modify backup.inc.php

We create a file named backup.inc.php in our sysadmin folder and insert a php reverse shell into it and override it 

![img](24.png)

![img](25.png)

set up a nc listener 

![img](26.png)

command : mv backup.inc.php ./script/lib/backup.inc.php --> to override the exisiting file with our php reverse shell

![img](27.png)

after a minute we get a reverse shell with root privilage

![img](28.png)

We sucessfully found the proof.txt file  


----------------------------------------------------------THE END---------------------------------------------------------------------



