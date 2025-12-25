## Lets Start with an Nmap scan

![img](1.png)
![img](2.png)

Lets perform service version detection and default script scan

In meanwhile lets visit site running on port 80 http

Its a login page but dont know the credentials

I used gobuster to enemurate for web directories but no directories found

Lets see the namp scan output

![img](3.png)
![img](4.png)
![img](5.png)

We found that ftp anonymous login is allowed , and also we found the key located at /key_rev_key

Now lets login into ftp

![img](6.png)

We found a jpg file called gum_room.jpg 

Lets use stegseek tool to check for there is any hidden details inside the image

![img](7.png)

We found a secret message stored in gum_room.jpg

![img](8.png)

looks like a base64 encoded text lets decrypt it

![img](9.png)

we found a username charlie and password is in hash format , lets use hashes.com to crack it 

![img](10.png)

we cracked the hash value

Now we have username and password lets login into the password

![img](11.png)

It seems like we can execute commands , lets set a nc listener and execute a nc reverse shell

![img](12.png)

We successfully got a reverse_shell

![img](13.png)

Lets upgate the shell and move to user directory

![img](14.png)

we found the user.txt but we cant able to read it

![img](15.png)

There is a file called teleport , lets see the contents inside it

![img](16.png)

We got a rsa key , we can use it to login into ssh , create a file , copy he key inside it make it executable
and login into ssh as user charlie

![img](17.png)

We successfully login into ssh now lets  view the user.txt flag

![img](18.png)

We have to esclalate our privilage to root in order to find the root flag 

Type command : sudo -l 

Shows what user charlie can run with root privilage 

![img](19.png)

seems user charlie can run vi with root privilage , lets try to exploit it 
i used gtfo bins for the esclation

![img](20.png)

We successfully esclated our privilage to root

![img](21.png)

Lets naviagte to root directory , instead of root.txt there is a python file named root.py

![img](22.png)

Lets see the contens of the file 

![img](23.png)

Its asking for a key to decryt the flag 

In nmap scan we found the path to the key , lets download that and see the content of it

![img](24.png)

We successfully found the key , lets run the python script and enter the key

![img](25.png)

i think some modules are not installed , so lets copy the python script into our system and try it 


![img](26.png)

We successfully found the root flag

------------------------------------------------THE END------------------------------------------------------




