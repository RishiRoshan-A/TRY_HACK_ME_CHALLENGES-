## Lets Start With an Nmap Scan

![img](1.png)

We found only two open ports , lets perform service version detection and default script scan

![img](2.png)

Here ssh runs on port 80 and http runs on port 22

in order to visits the webiste runnig on port 22 , update the firefox file network.security.ports.banned.override  to 22 in about:config

Lets visit the website

![img](3.png)

While inspecting the page we got an base 64 encoded strings and also a url /recovery.php

![img](4.png)

Lets decrypt it

![img](5.png)

we found the password 

Lets use gobuster to find hidden web directoires

![img](6.png)

We found only /assests which contains only the images on the site 

Lets go to recovery.php , it contains a login page while inspecting it , we can see a encoded string , 

![img](7.png)

Lets decode it using cyberchef 

![img](8.png)

When i click on magic icon in cyber chef it automatically decode the string with base32 and hex and i got an unreadable string so i tried rot13 and we got an hint , lets see that url

![img](9.png)

This reminds me the dino image in the webiste 

![img](10.png)

Lets go to assests folder and download the file 

![img](11.png)

![img](12.png)

i used stegseek to find a valid passphase , but it cant able to find 

![img](13.png)

Then i remebered we got a password lets use that 

![img](14.png)

We are in the wrong image lets try another two image , i tried jackinthebox but it is also a wrong image , so lets try header.jpg

![img](15.png)

![img](16.png)

We found the username and password , lets login 

![img](17.png)

Seems like with ?cmd=  we can execute commands

![img](18.png)

Lets create  a nc reverse shell i used reverse shell generator ,so set up a nc listener

![img](19.png)

![img](20.png)

execute the command

![img](21.png)

We got the reverse shell

![img](22.png)

i naviagte to home folder where i see a file jack_password_list

![img](23.png)

Lets copy the passwords in the file and try to brute force over ssh running on port 80 with hydra

![img](24.png)

we successfully found the password , lets login into ssh

![img](25.png)

i saw a file called user.jpg , lets copy it to our system

run a python server

![img](26.png)

using wget lets get the file user.jgp

![img](27.png)

![img](28.png)

Lets view the image

![img](29.png)

We successfully got the user flag

Lets esclate our privilage to get the root flag

![img](30.png)

seems user jack cannot run sudo on this machine 

i tried visting crontab but no juicy information is found 

![img](31.png)

Lets check for files with suid permission 

suid --> if the file has suid permission normal user can execute it with root privilage

4000 --> represents file with suid permission

![img](32.png)

We found that strings command has suid permission , lets use to read the root.txt file in the root directory

![img](33.png)

We successfully found the root flag

---------------------------------------------------------THE END------------------------------------------------------



