## Lets Start With an Namp Scan 

![img](1.png)

There are three open ports, Lets perform service detection scan and default script scan on these three open ports 

![img](2.png)

![img](3.png)

From our nmap scan the cms named bolt is running on port 8000

![img](4.png)

Lets visit the site 

While seeing the site we found the username and password

![img](5.png)

![img](6.png)

![img](7.png)

I further used gobuster to enerumate for any login pages but i wouldnt able to find any directoires

So i searched for default login page path  for bolt cms

![img](8.png)

We found that default login page for bolt is at /bolt/login

Lets use gobuster to cross-check

![img](9.png)

We successfully found the login page , lets login into that with the username and password we found

![img](10.png)

We found the bolt version

![img](11.png)

Lets use Exploit db to check for check for any exploits is there, for version 3.7.1 no exploit is found , but for 3.7.0 we found one exlpoit 

![img](12.png)

Lets see its exployee id 

![img](13.png)

![img](14.png)

Lets search for the exploit in msfconsole

![img](15.png)

Lets use that exploit 

![img](16.png)

Set LHOST , RHOSTS , USERNAME , PASSWORD 

![img](17.png)

we got a reverse shell

use command : /bin/bash -i to spawn a tty shell

The flag is not in the root direcotory and we have no idea where the flag is located so lets use 
find commad

commnd : find / -name "flag.txt"

The flag is in home directory

![img](18.png)

We successfully found the flag 

-----------------------------------------------------THE END------------------------------------------------


