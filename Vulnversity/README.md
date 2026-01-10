## Lets start with an Nmap scan 

![img](1.png)

We found six open ports lets perform service version detection and default script scan on them

![img](2.png)

We found that a apache http service is running on port 3333 lets visits it 

![img](3.png)

Lets use gobuster to enemurate the web directories

![img](4.png)

in path /internal we can able to upload files , lets try file upload vulnerablity and obtain a reverse shell

![img](5.png)

![img](6.png)

Semms the php extension , so lets different extensions 

after trying many exxtensions .phtml worked 

![img](7.png)

![img](8.png)

Since we dont know the path where the php shell is uploaded so lets use gobuster to find it

![img](9.png)

Lets go navigate /uploads path

![img](10.png)

set up a nc listener and click on the reverse shell code we created 

![img](11.png)

![img](12.png)

We successfully got the reverse shell 

Lets go to home directory 

![img](13.png)





