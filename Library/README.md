## Lets start with a nmap scan 

![img](1.png)

we found only two ports are open ssh and http lets perform service detection scan and default script scan 

![img](2.png)

There is a site hosted on port 80

![img](3.png)

Lets vists robots.txt in that there a hint rockyou  might have been refering to the wordlists rockyou.txt

![img](4.png)

lets use gobuster to find for directories and found one /images

![img](5.png)

i downloaded images in the images folder and checked using stegseek and exiftool but no juicy information found 

![img](6.png)

Then i looked up into the main site their i found a username meliodas

![img](7.png)

we already have a hint rockyou.txt lets try ssh brute force using hydra with username meliodas and password wordlists rockyou.txt

![img](8.png)

we succesffuly found the password lets login with ssh and cat the user.txt for the first flag

![img](9.png)

we want to esclate our privilage in order to get the second flag

so execute command : sudo -l  

to see what the current user can execute with root permission

![img](10.png)

we found a file bak.py which user can execute with sudo

so lets remove bak.py 

![img](11.png)

Now lets a new file bak.py 

and give the command inside the file : 'import pty;pty.spawn("/bin/bash")'

using nano or echo to spawn a pty shell with root privilage

lets run the file with python command and we got the root privilage , navigate to root directory and cat the root.txt to view the flag

![img](12.png)

we succesfully found the second flag

-----------------------------------THE END--------------------------------------



