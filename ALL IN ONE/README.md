## RECON 

Lets start with our nmap Scan full port scan  on the target ip 

![img](1.png)

Found three open ports , lets perform service version dection scan and default scan on them 

![img](2.png)

Found that ftp anonnymous login is allowed , lets login with anonymous as username and password 

![img](3.png)

here didnt find any juicy information 

in http site there is a apache default service is running , lets use gobuster to enemurate the web directories 

![img](4.png)

found a directory wordpress , lets access it 

![img](5.png)

seems like wordpress has been running , lets use wp-scan to enemurate information like username , plugins , wp version etc..

![img](6.png)

![img](7.png)

found a few wp plugins mail-masta and reflex-gallery 

![img](8.png)

also found a username elyana

## EXPLOITATION 

we found some plugins , lets see if the plugins are vulnerable to any exploits 

![img](9.png)

seems like mail-masta is vulnerable to local file intrusion , lets view that exploit 

![img](10.png)

found the extract path where we can perform lfi , lets try to access the wp-config.php file since it contains information like usernames and passwords

while normally accessing wp-config.php file like ../../../../../wp-config.php it is getting executed and returning us a blank page 

therefore in order to read it , lets apply a php filter and convert it to base64 

![img](11.png)

now lets we can able to see the contents of the file in base64 encoded format , lets decode it 

![img](12.png) 

We found the elyana password , there is a wp-login form , lets use our credentials to login 

# GAINING REVERSE SHELL

found a 404 php template , lets replace the code with php reverse shell code from github 

![img](13.png)

update the file and access the url to gain a reverse shell 

![img](14.png)

![img](15.png)

we cant able to read the user.txt file and found a hint that elyana password is somewhere in the system 

lets use find command to search for elyana owned files 

![img](16.png)

found a private.txt file , lets view it 

![img](17.png) 

since we got elyana password and ssh port is open , lets login through ssh 

![img](18.png)

## PRIVILEGE ESCLATION 

--> sudo -l --> shows which command user elyna can run with sudo or root privilege 

![img](19.png)

found that elyana can run socat command with sudo 

utilized gtfo bins to spawn a shell with root privilege

![img](20.png) 

![img](21.png)

Successfully found the user.txt flag and root.txt flag 




