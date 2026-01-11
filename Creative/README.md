## Lets start with an nmap scan

![img](1.png)

We found two open ports , lets perform service version detection and default script scan on them

![img](2.png)

add the creative.thm in the /etc/hosts to access the site running on port 80 

lets use gobuster to enerumate the web directories

![img](3.png)

I inspected the page and also the url found by gobuster but no juciy information is found 

Lets enemurate for subdomains using wfuzz , since gobuster results are not accurate 

![img](4.png)

we found a sub domain beta , lets add that to /etc/hosts 

![img](5.png)

now lets vistis the site 

![img](6.png)

seems like it is used to test a url to see it is alive , lets try with local host 

![img](7.png)

![img](8.png)

seems like we can perform ssrf , lets analyse the request with burp

![img](9.png)

lets use wfuzz to see which port is active on localhost

![img](10.png)

seems like port 1337 is open lets check it 

![img](11.png)

![img](12.png)

lets naviagte to home directory 

![img](13.png)

![img](14.png)

We found a username saad , lets navigate into it 

![img](15.png)

we found a directory .ssh , lets naviagate into it 

![img](16.png)

we got the id_rsa key for user saad to login into ssh 

![img](17.png)

right click and click on view page source to see the key in structured format

![img](18.png)

seems like the key is passphase protected , lets crack it 

convert the key into a hash format that john can understand 

![img](19.png)

lets crack it using john 

![img](20.png)

![img](21.png)

![img](22.png)

![img](23.png)

we successfully got the user flag 

as we dont know the password we cant able to run sudo -l 

while running command ls -la , noticed a file named .bash_history lets view it 

![img](24.png)

![img](25.png)

We got the saad password , now lets run sudo -l to see the what command user saad can run with root privilages 


![img](26.png)

lets perform a LD_PRELOAD privilage esclation 

LD_PRELOAD is an environment variable in Linux

It tells the program:

Before you use your normal system libraries, load my library first.

lets write a c program in a file named exploit.c

![img](27.png)

_init() --> runs automatically when a shared library is loaded

Removes LD_PRELOAD after loading

setgid(0)--> Changes group ID → root (0)

setuid(0)-->Changes user ID → root (0)

system("/bin/sh"); --> Spawns a  shell

lets complie the file 

![img](28.png)

-fPIC --> Position Independent Code required for shared libs

-nostartfiles --> No default startup code so _init() runs cleanly

![img](29.png)

LD_PRELOAD=/tmp/exploit tells Linux: Load this library before anything else

and we successfully got the root flag

-----------------------------------------------------------------------THE END-------------------------------------------------------------------------

