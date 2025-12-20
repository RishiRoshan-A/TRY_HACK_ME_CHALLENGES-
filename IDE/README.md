## Lets start with a nmap scan 
![img](1.png)

We found there are four open ports lets perform service detection scan and default script scan on these specific ports

![img](2.png)
![img](3.png)

Lets use gobuster to enemurate the directories

![img](4.png)

we found no directories , there is a apache service http running on port  62337 lets check that 

it contains a login page and we dont have any credentials so lets try to enerumate directories using gobuster

![img](5.png)

i gone through every urls that gobuster found but i didnt found any useful information , in namp scan i saw anonymous ftp login is allowed , lets try that

![img](6.png)

we succesfully loged in and we found a hidden file 

lets copy that to our system

![img](7.png)

Lets see whats inside the file

![img](8.png)

we found the username  : john 
lets use hydra to crack the password 

we successfully found the password : password

now lets login into the website with the found credentials

![img](9.png)

in nmap scan we found a ide framework codiad 2.8.4 

lets search for the exploit in searchsploit 

![img](10.png)

we found a exploit lets naviagte to that directory and type : python 49705.py -h to see the syntax

lets use the exploit also set up a netcat listener as shown in the python script 

![img](11.png)

we successfully got a reverse_shell 

![img](12.png)

lets naviagte to home directory where there is a user drac 

![img](13.png)

we cant file user.txt as an drac user without knowing his password 

try ls -la --> to list the hidden files

and in .bash_history.txt we found his password

![img](14.png)

lets switch to tty terminal to upadte to drac user 

![img](15.png)


![img](16.png)

we succesfully found the user.txt

we know the username and password for drac lets try login with ssh 

![img](17.png)

type : sudo -l 

to see what user drac can execute with root permission 

![img](18.png)

we found vstfpd restart service 
so if we insert a reverse shell in the vstfpd.service file and execute we gain a reverse shell with root privilage

use command : locate vstfpd.ervice to see the file location 

i used reverse shell generator to generator a reverse_shell

![img](19.png)  

change sh to bash since we are working on a bash shell

use nano vstfpd.service to edit the file 

in EXEC_START = /bin/bash -c <payload> 

save and exit

set up a netcat listener and execute the vsftpd restart service

![img](20.png)

we got an connection in out netcat listener

![img](21.png)

navigate to root directory and cat the root flag

![img](23.png)

we succesfully found the root flag

-----------------------------------------------THE END--------------------------------------------------------------



