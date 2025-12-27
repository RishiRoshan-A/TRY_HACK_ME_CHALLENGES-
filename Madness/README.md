## Lets start with an nmap scan 

![img](1.png)

We found that there are two open ports , Lets perform service version detection scan and default script scan on them

![img](2.png)

Lets visit the website running on port 80

![img](3.png)

Lets use gobuster to find the web directories

![img](4.png)

We found no directories , lets view the source code of the page for any information disclosure

![img](5.png)

We found a jpg file lets try to open it 

![img](6.png)

![img](7.png)

In head if we see , it is mentioned as png image , and also we have a hint thm.jpg contains some error

Lets use curl to get the image to our system

![img](8.png)

when i use file command , it is showing data instead of JPEG 
so i imported the image in hex editor and the magic headers are in png format , lets change it to jpg and download the image

![img](9.png)

![img](10.png)

When i visited the image i found a hidden directory

![img](11.png)

Lets naviagte to that hidden url

![img](12.png)

We have to find the secret to further continue , lets inspect the page

![img](13.png)

We found that the secret code is in between 0 to 99

i embedded ?secret=1 in the url and noticed it is reflected in the page 

![img](14.png)

Lets capture the requets in burp and forward it to intruder , lets try 0 to 100 and notice the content length , if we see a change that must be the secret code

![img](15.png)

There is a change in content length in code 73 , go to response and click on render 

![img](16.png)

i thought this would be the ssh password and tried to brute force the username with hydra , but it didnt work

Then remebered about the jpg file lets use this as a passphase and try to retrive any information

![img](17.png)

We found the username , but we dont know the password 

i tried to use gobuster to find a web directories with .png, .jgp, .png , .txt extension but none of them worked 

Then in tryhackme page found this image 

![img](18.png)

Lets download this image and see if this contains any information

![img](19.png)

we succesfully found the password

Lets try to login with ssh 

![img](20.png)

It didnt login , i think the username has to be encoded with some ciphers , lets first try rot13

![img](21.png)

We found the username , it has been encoded with rot13 

Now lets login with ssh

![img](22.png)

We successfully found the user flag

Lets esclate our privilage to see the root flag

tried command : sudo -l 

![img](23.png)

but the current user cant run sudo on this machine 

I also visited crontab but no juicy information is found 

So lets look for files with suid permission

![img](24.png)

where screen-4.5.0 looks suspicious , lets look the exploits 

![img](25.png)

We found a exploit , create a file , paste the exploit and run it 

![img](26.png)

![img](27.png)

![img](28.png)

We successfully found the root flag 


-------------------------------------------------------THE END----------------------------------------------------------------------------------------






