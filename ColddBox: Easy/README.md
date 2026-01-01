## Lets Start with an nmap scan

![img](1.png)

We found that there are two open ports , lets perform service version detection and default script scan on them 

![img](2.png)

lets vistis the site running on port 80

![img](3.png)

Lets use gobuster to enemurate the web directories 

![img](4.png)

We found some directories lets view /hidden 

![img](5.png)

we found a username c0ldd , and in /wp-admin path we have found a login page 

we know that the site is made up of wordpress , use wappalyer extension to check that 

Lets use wpscan to crack the password of c0ldd

![img](6.png)

![img](7.png)

We successfully found the username and password , lets login into the site 

![img](8.png)

while visting all urls and functionality of the site , i found that in apperence tab and in editor there is a file 404.php , lets vistis it 

![img](9.png)

lets replace the php code with our php reverse shell code , i got it from github

![img](10.png)

set up a nc listener 

![img](11.png)

click on update and the url http://machine_ip/?p=440.php

![img](12.png)

we successfully got the reverse shell

![img](13.png)

but we cant able to read the user.txt file , since our permission is denied

![img](14.png)

i visted /etc/crontab and checked for suid permission but no juicy information is found 

since this site is made up of wordpress , always check for default wp-config.php file which contains database information

and usually located in /var/www/html

![img](15.png)

lets view the file 

![img](16.php)

We successfully got the password for user c0ldd , lets esclate to c0ldd user and read the user flag 

![img](17.png)

We successfully found our user flag 

lets see what commands c0lld user can run with root privilages , for that type command : sudo -l

![img](18.png)

There is a payload available for ftp in gtfo bins to spawn a bash shell with root privilages lets try that

![img](19.png)


![img](20.png)

We successfully found the root flag 

--------------------------------------------------------------------------------------THE END----------------------------------------------------------------------------------


