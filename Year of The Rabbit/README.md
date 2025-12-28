## Lets Start With an Nmap Scan 

![img](1.png)

We found that there are three open ports , lets perform service version detection and default script them on these open ports

![img](2.png)

Lets vistis the site runnig on port 80

![img](3.png)

Lets use gobuster to enemurate the web directories 

![img](4.png)

We found a path /assets lets visit it 

![img](5.png)

It consits of a mp4 video and a css file , 

i downloaded the video i tried to extract any hidden information in it , but no juicy is found 

So lets visit style.css file

![img](6.png)

We found a path , when i vistis that it opened the same mp4 video in youtube 

![img](7.png)

Lets use burp suite to see the request flow while accessing the path

![img](8.png)

We found a hidden_directory 

Lets vistis it 

![img](9.png)

It contains an image , lets download it 

i used stegseek tool and exiftool to see any hidden file is ecrypted inside it , but no information is found 

![img](10.png)

So lets use strings command to see the image binary in human readable format 

![img](11.png)

![img](12.png)

We found a ftp username and a list of password , lets copy that list of password to a file and use hydra to crack it 

![img](13.png)

We successfully found the ftp password , lets login into ftp

![img](14.png)

We got a file Eli's_creds.txt , lets get the file to our system and see the contents of it 

![img](15.png)

The text is encryted with some ciphers , lets use decode fr to identify the cipher as well as to decode it 

![img](16.png)

![img](17.png)

Now we got the username and password , lets use it to login into ssh

![img](18.png)

We have got one hint to check the s3cr3t hidden place 

Lets use locate command to find it 

![img](19.png)

we have a hidden meassage lets see the contents of it

![img](20.png)

we have the username and password for another user , lets try login into that user

![img](21.png)

We have successfully found the user flag

Now we have to esclate our privilage to see the root flag 

when i type sudo -l , i didnt notice !root , and i searched for vi sudo privalge esclation in gtfo bins and tired the command and it didnt work

![img](22.png)

!root means user can run commands as anyone except root 

there is a not root vulnerability : !root vulnerability (CVE-2019-14287)

we can use commands like : sudo -u#-1 <command>

Where -u for uid 

uid for root user : # or 0
uid for normal user : 1000 ,1001 like that

when we give -u#-1 sudo thinks it is not a root , but linux thinks it is a root 

and this vulnerability is aplicable only for odler version of sudo

![img](23.png)

![img](24.png)

lets try gtfo bins command with this command

![img](25.png)

![img](26.png)

we successfully found the root flag 

----------------------------------------------------------THE END-----------------------------------------------------------











