## Lets start With an Namp Scan 

![img](1.png)
![img](2.png)

seems lime lot of ports are open , lets perform default nmap script scan and service detection scan 

![img](3.png)
![img](4.png)

seems like only port 80 (http) and 22 (ssh) are functional 

lets use gobuster to enemurate the web directoires on the site running on port 80

![img](5.png)

if we access the path /inferno it is asking for the login credentials to further proceed

i inspected the page and visited the souce code for any information disclosure but no juciy information is found 

tried defualt passwords but thats not worked well 

lets try deafult username as admin and use rockyou.txt as wordlist in hydra 

![img](6.png)

we successfully loged into the site 

![img](7.png)

there are many php files i tried pasteing the php reverse shell code , but we cant able to save or modify the php file 

There is a file called README.md , lets see the contents of it 

![img](8.png)

found that the site has been developed with Codiad 

lets search for the exploits available for Codiad 

![img](9.png)

found one exploit , lets copy it and lets see the usage of it 

![img](10.png)

![img](11.png)

lets run the two commands in separate shell and further proceed with y 

![img](12.png)

![img](13.png)

![img](14.png)

We successfully got the Reverse shell 

![img](15.png)

![img](16.png)

seems like we cant able to read the local.txt file 

while visiting others Directory , in Downloads Directory found a Intresting File 

![img](17.png)

lets see the contents of it 

![img](18.png)

seems like the value are in the hexa decimal format , lets use cyber chef to dcode it 

![img](19.png)

at last it seems like the it is shown the username and password , lets try that credentials over ssh 

![img](20.png)

![img](21.png)

We successfully got our first flag , lets esclate our privilage to find the second our 

use command : sudo -l 

![img](22.png)

found that user can run tee command without any root permission

lets use gtfo bins 

![img](23.png)

seems like we can modify any files with this , lets modify the sudoers file and give dante all permission 

![img](24.png)

![img](25.png)

We successfully found our second flag 

------------------------------------------THE END--------------------------------------------------------



