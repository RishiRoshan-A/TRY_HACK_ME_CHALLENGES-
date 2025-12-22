## Lets Start With an Namp Scan 

![img](1.png)

we found only two ports are open , lets perform default script scan and service detection on these two ports

![img](2.png)

Lets vists the website running on port 80 its a normal apache defualt page lets inspect that , 

![img](3.png)

We found a username Jessie 

lets enemurate more , lets find webdirectories using gobuster

![img](4.png)

We found a directory /sitemap

Lets vistis that page 

![img](5.png)

I explored this website like inspecting it and navigating to all sections but no juicy information found

so Lets furture use gobuster to find directories under /sitemap

![img](6.png)

We found a intresting folder .ssh

lets visit it 

![img](7.png)

We got the id_rsa file 

![img](8.png)

We got the rsa private key which is useful for login into ssh and we already have an username we found before 

create a file copy the rsa key into the file change its permission
command : sudo chmod 600 <file_name>

now lets use the rsa key and username to login into ssh

![img](9.png)

we successfully login into ssh 

i naviagte to few folders to find user flag but cannot manually find it so lets use find command

command : find / -name "user*"

![img](10.png)
![img](11.png)

we successfully found the directory contains user flag lets navigate to it 

![img](12.png)

We succesfully found our user flag

Lets escalte our privilage to see the root flag

command : sudo -l --> show what the user can run with the root permission

![img](13.png)

wget which is used to download a file using url in linux , since we have root permission for wget we try to pass the root_flag.txt to our system using wget

so start a netcat listener

![img](14.png)

wget -h to see info about the command

![img](15.png)

--post-file argument is used the send a file to the target system

![img](16.png)

check our nc listener 

![img](17.png)

we successfully got our root flag

-----------------------------------------------------THE END---------------------------------------------------------








