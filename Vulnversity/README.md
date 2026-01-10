## Lets start with an Nmap scan 

![img](1.png)

We found six open ports lets perform service version detection and default script scan on them

![img](2.png)

We found that a apache http service is running on port 3333 lets visits it 

![img](3.png)

Lets use gobuster to enemurate the web directories

![img](4.png)

in path /internal we can able to upload files , lets try file upload vulnerablity and obtain a reverse shell

![img](5.png)

![img](6.png)

Semms the php extension , so lets different extensions 

after trying many exxtensions .phtml worked 

![img](7.png)

![img](8.png)

Since we dont know the path where the php shell is uploaded so lets use gobuster to find it

![img](9.png)

Lets go navigate /uploads path

![img](10.png)

set up a nc listener and click on the reverse shell code we created 

![img](11.png)

![img](12.png)

We successfully got the reverse shell 

Lets go to home directory 

![img](13.png)

We successfully found the user file 

lets esclate our privilage to find the root flag 

seems like we cant run sudo as this current user 

so lets find the files with suid permissions

![img](14.png)

systemctl command is used to enable,start or stop a service like ssh,ftp etc..

so we can create a service named root.service where we can able to spawn a reverse shell

![img](15.png)

lets start a python server and get the root.service file on the target system

![img](16.png)

use wget command to get the file

![img](17.png)

seems like our permission is denied so lets naviagte to tmp directory and try there

![img](18.png)

set up a nc listener

enable and start the root.service

![img](19.png)

We successfully got the reverse shell

![img](20.png)

we successfully found the root flag 









