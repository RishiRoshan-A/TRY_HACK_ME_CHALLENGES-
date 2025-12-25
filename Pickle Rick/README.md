## Lets Start with an nmap scan 

![img](1.png)

We found are two open ports , lets service version detection and default script scan

![img](2.png)

Lets see the site running on port 80

Lets inspect the site 

![img](3.png)

We found a username 

Lets use gobuster to enemurate some web directories

![img](4.png)

Lets visit robots.txt 

![img](5.png)

Looks like we found the password

I assests folder i checked for any login in all files but no juicy information is found 

i also tried to login into ssh with username and password but it failed

There should be an login page , since we got username and password , lets try enerumate web directories with an php extension

![img](6.png)

We found an login.php form ,lets login with username and password

![img](7.png)

Seems like we can execute commands

Tried to obtain nc reverse shell but it didnt work

Lets use ls to list the files

![img](8.png)

We found the first incredient but we cant able to read it with cat command , so lets try strings 

command : strings Sup3rS3cretPickl3Ingred.txt

![img](9.png)

Lets view the home directory 

Command : ls /home

![img](10.png)

Lets see files inside rick folder

Command : ls /home/rick

![img](11.png)

We found the second ingredients 

Lets use Strings command to read the second ingredients

Command : strings /home/rick/second\ ingredients

![img](12.png)

The third ingredients should be in root directory lets see what privilage we has 

Command : sudo -l 

![img](13.png)

We can run any command with sudo

Command : sudo ls /root

![img](14.png)

Lets read the third ingredient

Command : sudo strings /root/3rd.txt

![img](15.png)




