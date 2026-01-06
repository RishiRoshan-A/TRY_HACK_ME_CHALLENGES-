## Lets start with an nmap scan

![img](1.png)

We found two open ports , lets perform service version detection and default script scan on them

![img](2.png)

Lets see the site running on port 80

![img](3.png)

Lets use gobuster to enemurate the web directories 

![img](4.png)

I visted all these paths and also inspected every page but no juicy information is found 

Lets futher use gobuster to enemurate the web directories under the path we found

![img](5.png)

![img](6.png)

![img](7.png)

on /static when i open the first image it started with 1 and ended with 18, but here 00 makes suspicious so lets visit it 

![img](8.png)

we found a lead to a path , lets naviagte to it 

![img](9.png)

it consist of a login page but we dont know any credentials , lets view the source code of the page 

![img](10.png)

in style.css and button.js no information is found but in dev.js we got the username and password 

![img](11.png)

Lets login into the site 

![img](12.png)

seems like ftp is running on another port instead of default 21

Lets do a full port scan using nmap

![img](13.png)

we found  a port open on 37370 , but the service is unknown , so lets perform default script scan and service detection scan on it

![img](14.png)

we can now conform that it is running ftp , lets try to login with our username and password

![img](15.png)

there are three files , with extension .pcapng that represents wireshark 

lets get all that file and analysis it with wireshark

![img](16.png)

In ftp and Http1 file no juicy information 

In Http2 file we found the username and password 

![img](17.png)

Right click on any tcp packet and in follow click on follow tcp stream 

![img](18.png)

In stream 31 we found the username and password

lets login into ssh with the username valleyDev and password

![img](19.png)

Lets view the user.txt file 

![img](20.png)

We successfully found the user.txt 

Lets escalate our privilage to read the root file 

We cant able to run sudo on this machine as the current user we have loged in 

![img](21.png)

Lets visit the crontab 

![img](22.png)

There is a python script run by root every minute , but we cant able to override or write or create or modify the file 

Lets read that python file 

![img](23.png)

It is importing base64 if we insert a reverse shell in base64.py , we may get a reverse root shell when root excutes the photosEncrypt.py

but we cant able to modify the file as our permission is denied 

![img](24.png)

while exploring file system in home folder found an user valley and a file named valleyAuthenticator

we cant able to read that file it looks like  a raw data

![img](25.png)

Lets get that file to our system 

use command : python -m http.server <port_no>  --> to start a python server 

![img](26.png)

while using strings command found a word UPX seems suspicious 

![img](27.png)

![img](28.png)

Lets research about it 

![img](29.png)

upx compresses the executable file that why we saw that raw packets , lets unpack it 

![img](30.png)

now lets use string command 

![img](31.png)
![img](32.png)

We found the two hash values , lets crack it using 

![img](33.png)

![img](34.png)

We found two password for username valley 

Lets try that to login into ssh as user valley

![img](35.png)

we cant able to edit or modify the photosEncrypt.py file but we have permission to modify the base64.py file

lets generate a python reverse shell i used reverse shell generator to generate a python reverse shell 
payload

![img](36.png)

start the nc listener

![img](37.png)

paste  our reverse shell code in the base64.py and save it 

![img](38.png)

after a minute the root executes the photosEncrypt.py file in which it imports base64 that calls base64.py file which will activates the reverse shell with root privilage 

![img](39.png) 

We successfully found the root flag 

-----------------------------------------------------------------THE END----------------------------------------------------------------------------------







