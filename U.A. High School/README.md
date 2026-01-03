## Lets Start With an Namp scan 

![img](1.png)

We found that there are two open ports , lets perform default script scan and service version detection on them

![img](2.png)

Lets visit the running on port 80

![img](3.png)

Lets use gobuster to enemurate the web directories

![img](4.png)

we found a path /assets lets again use gobuster to enemurate the directories under assets 

![img](5.png)

We found that we found a index.php file , when i visit the url it showed a blank page

Lets use burp to see the backend requests 

![img](6.png)

![img](7.png)

We can see that there is a PHPSESSID is created that means , a PHPSESSID is created when Php code runs on a server 

That blank might due to error might have occured when the index.php code is executed so the program might excepting a parameter 

So lets perform parameter enemuration using gobusters 

![img](8.png)

since we get 200 ok for all the parameters so lets exculde the length 0

![img](9.png)

We found the parameter cmd

Lets see the contents 

![img](10.png)

it is in base 64 encrypted format , lets decode it 

![img](11.png)

Seems the id command has been executed , so instead of id lets try executing a nc reverse shell 

![img](12.png)

Lets set up a nc listener

![img](13.png)

if we paste the payload normally it is not working , so lets perform url encode on it and send it

![img](14.png)

We successfully got a reverse shell

![img](15.png)

While visting the directories found a folder Hidden_contens

Lets see the files inside it 

![img](16.png)

![img](17.png)

We got a passphrase usually when extracting a hidden information from an image we required an passphrase

The passphrase looks like it is base64 encrypted , lets decrypt it

![img](18.png)

We found that in gobuster in assets directory there is a path /image 

Lets visit it , found two images lets get one of them and check that

![img](19.png)

![img](20.png)

Lets use steghide to exxtract the information with the passphrase

![img](21.png)

I think the file format is wrong , while checking in hex editor the magic bytes are in png format ,lets change it to jpg

![img](22.png)

![img](23.png)

Now lets download the image and check it 

![img](24.png)

We found a username and password , lets use that to login into ssh 

![img](25.png)

We successfuly login into the ssh

Lets view the user.txt file

![img](26.png)

We successfully found the user flag

Lets esclate our privilage to get the root flag 

type command : sudo -l  

to see what the current user can run with root privilage 

![img](27.png)

Seems like he can execute an bash file feedback.sh 

We cannot able to edit or  remove the file , so while reading the file 

![img](28.png)

We can see that it is not filtering ">>" symbol and before it is writing the contens to feedback.txt , it is executing the command using eval 

eval is used to execute commands 

![img](29.png)

When i gave root , it is using eval "echo "root"" this will print root on the terminal before writing it into feedback.txt

so lets edit the sudoers file and give the user deku NOPASSWD for all commands

![img](30.png)

![img](31.png)

Now we can run any commands with root privilages 

So lets spawn a bash shell and view the root file 

![img](32.png)

We successfully found the root flag 

----------------------------------------------------------------------------THE END------------------------------------------------------------------------------------------------




