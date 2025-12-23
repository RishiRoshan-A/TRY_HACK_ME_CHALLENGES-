##Lets Start With an Nmap scan

![img](1.png)

lets perform default script scan and service dection scan on these three open ports

Mean while lets use gobuster to enerumate web directories

![img](4.png)

We found a directory files lets navigate to it 

![img](5.png)

We found one empty folder ftp , one image file and text file , lets view the text file 

![img](6.png)

We found a username Maya

Lets see our nmap script scan

![img](2.png)
![img](3.png)

We found that ftp allows Anonymous login

Lets login into ftp , 

![img](7.png)

in here also the same things are there that are in the path /files

So i used hydra with username maya over ssh but cant able to find password 

So i tried to upload a reverse shell in ftp directory
Lets use php-reverse_shell i downloaded it from github

![img](8.png)

Lets also set up a nc listener

![img](9.png)

![img](10.png)

file uploaded successfully lets naviagate to /files/ftp

![img](11.png)

Click on the file and Lets see we obtained a reverse_shell

![img](12.png)

We found a file called recipe.txt 

We successfully found our first answer

i see a one more folders called incidents lets navigate to that 

![img](13.png)

Where we a found a wireshark file  

--> .pcapng represents a file saved in wireshark 

Lets copy that file to ftp folder and download that in our system 

![img](14.png)

![img](15.png)

Lets open that file using wireshark 

![img](16.png)

In wireshark right click on any tcp packet and in follow choose tcp stream 

![img](17.png)

in stream 7 i found some juicy information 

![img](18.png)

We succesfuuly found the username and password 

Lets try to login into ssh with that credentials

![img](19.png)

We successfully loged into ssh

![img](20.png)

We successfully found the user flag

I tried sudo -l to see what user can execute under root privilage , but lennie user dont have any root permission

Lets naviagte to script file where i found a planner.sh 

![img](21.png)

we cant run planner.sh but i found that planner.sh runs a file print.sh and we have permission to modify print.sh

![img](22.png)

Lets write a reverse_shell to print.sh , therefore when root executes planner.sh , print.sh also executes and we get a root shell

![img](23.png)

set a nc listener

![img](24.png)

modify print.sh

![img](25.png)

Wait until the root executes planner.sh

![img](26.png)

We got an reverse_shell

We successfully found the root flag

----------------------------------------------THE END----------------------------------------------





