## Lets start with an Nmap Scan 

![img](1.png)

we found four open ports , lets perform service version detection and default script scan on it 

![img](2.png)

![img](3.png)

seems like a Apache site has been running on port 31331 , lets use gobuster to enemurate some web directories 

![img](4.png)

lets visit the contents of robots.txt

![img](5.png)

we found a sitemap : /utech_sitemap.txt , lets see the contents of it 

![img](6.png)

no juicy information is found on /index.html and /what.html 

lets visit /partners.html

![img](7.png)

we found a login page , lets check for any information disclosure 

right click and click on view-page source 

![img](8.png)

in bottom found two paths 

where js/api.js seems to be intresting , lets see the contents of it 

![img](9.png)

Lets try command line injection on the particular url 

![img](10.png)

single quotes does not work , so try backslash it worked 

'ls' is just text

Shell treats it literally

No command execution

Shell sees backslash

Executes the command inside them → ls

and we found a database lets see the contents of it 

![img](11.png)

We found a username r00t and the password in a hash format , lets use hashes.com to crack it 

![img](12.png)

We successfully found the username and password , since ssh port is open , lets try login over ssh with our found credentials

![img](13.png)

![img](14.png)

for the final answer we want to visit the first 9 characters of the ssh priviate key of root 

tried : sudo -l , visited crontabs , checked for files with suid permission but no juicy information is found 

so lets try id command 

![img](15.png)

semms like docker has been running on this machine , lets use gtfo bins for privilage esclation with docker

![img](16.png)

![img](17.png)

since there is no image like alpine , lets check for images using command : docker ps -a

found a image bash , lets try that in place of alpine 

![img](18.png)

we successfully got the root shell , now lets visit the ssh private key 

![img](19.png)

![img](20.png)

------------------------------------------------THE END-------------------------------------------------


