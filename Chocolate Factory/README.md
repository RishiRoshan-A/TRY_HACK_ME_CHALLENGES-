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


