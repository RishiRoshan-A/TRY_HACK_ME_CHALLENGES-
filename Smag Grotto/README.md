## Lets start with an nmap scan 

![img](1.png)

We found that there are two open ports 

Lets perform service version detection and default script scan on them

![img](2.png)

Lets visits the website running on port 80

![img](3.png)

Lets enemurate the web directories using gobuster

![img](4.png)

We found a path /mail

Lets visits it , in that we found a pcap file lets download it and view using wireshark

![img](5.png)

in wireshark right click on any tcp packet and in follow click on tcp stream

![img](6.png)

There is only one stream in which we found a host : development.smag.thm , username ,password

![img](7.png)

Lets add the host to our /etc/hosts file in order to view it 

![img](8.png)

Lets visit the site

![img](9.png)

It consits of a login page , lets login with our username and password found earlier

![img](10.png)

![img](11.png)

Seems like we can execute commands , so lets create a nc reverse shell and execute it

I used reverse shell generator to create a nc reverse shell 

Create a nc listener 

![img](12.png)

![img](13.png)

Execute the command 

![img](14.png)

We successfully got a reverse shell

We found a user name jake and we cant able to read the user.txt file , i think we have to escalate our privilage to jake user in order to read the user.txt

I visited all hidden files and folders in jake folder but no juciy information is found , so lets check the crontab 

![img](15.png)

We found that for every minute the contents of jake_id_rsa.pub.backup file has been overwritten to authorized_keys in .ssh folder 

authorized_keys file consits of the ssh public key so anyone with the ssh private key can login into ssh

so if we create our ssh public and private key and insert our ssh public key in jake_id_rsa.pub.backup file it will be written to authorized_keys automatically within a minute , and we can login with our private key as a jake user

Lets create our ssh private and public key

![img](16.png)

rr --> is the private key
rr.pub --> is the public key

![img](17.png)

![img](18.png)

Lets write the contents of rr.pub file into jake_id_rsa.pub.backup file

![img](19.png)

Lets use our private key to login into ssh as jake user

![img](20.png)

We successfully got our user flag

Lets esclate our privilage to read the root flag

command : sudo -l 

show what normal user can run with root privilage

![img](21.png)

I used gtfo bins to find a escalate our  privilage with apt-get command 

![img](22.png)

![img](23.png)

We successfully found our root flag

--------------------------------------------------------------THE END------------------------------------------------------------------









