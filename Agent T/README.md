## Lets Start With an Nmap Scan 

![img](1.png)

We found only http port open 

Lets perform service Detection scan and default Script Scan on port 80

![img](2.png)

Lets also perform Os detection Scan 

![img](3.png)

I cant find any juicy information so lets visit the website 

![img](4.png)

No function has been working , i also tried gobuster scan and ispected the page but no juicy information is found 

Then i used wapallyer exxtension to see the technologies they are using 

![img](5.png)

Here the php version seems vulnerable , i also used curl command to check the php version 

![img](6.png)

Here i got the exact service and version of php 

Lets use searchsploit to search for exploit for this specific version of php

![img](7.png)

I found a payload for this specifc version

Lets try to exploit 

![img](8.png)

We successfully got the interactive shell 

To find the flag lets use find command

![img](9.png)

We successfully found the flag

--------------------------------------------------THE FLAG-------------------------------------------------------------

