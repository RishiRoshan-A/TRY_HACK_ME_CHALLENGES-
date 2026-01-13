## Lets ping the target to see it is alive 

![img](1.png)

The pings packets have not been recived , lets perform a nmap scan with diabling ping probes

![img](2.png)

We found two open ports , since it is a windows target , windows usually blocks the icmp packets , so ping does not work against it 

Now lets perform service verison detection scan and default script scan on the two open ports

![img](3.png)

We found a http site running on port 80 , lets visit it

![img](4.png)

Lets use gobuster to enemurate the hidden web directories

![img](5.png)

Lets try with different wordlists 

![img](6.png)

We found a directory named Retro , lets naviagete to it 

![img](7.png)

We found a username wade , while reading a post wade mentioned that he mistyping the name of the avatar whenever he login , so the password should be the name of the avatar 

![img](8.png)

click on the Ready player one url

![img](9.png)

so found the wade password 

since rdp is open , lets try login into rdp with username wade and his password 

![img](10.png)

![img](11.png)

We successfully found the user.txt file 

Lets eslcate our privilage to find the root flag 

There is a executable named hhupd 

![img](12.png)

While researching about it , found its cve number 

![img](13.png)

Lets follow the steps to esclate our privilage to nt authority 

Right click on hhupd and click on run as administrator 

![img](14.png)

click on show more details 

![img](15.png)

click on show information

![img](16.png)

click on the link and click on okay 

![img](17.png) 

in this click on the settings 

![img](18.png)

click and file and click on save us 

![img](19.png)

enter the file name as c:\windows\system32\*.* and click on save 

![img](20.png)

scrool down until cmd and right click on it and click on run as administrator

![img](21.png)

We successfully escalted our privilage to nt authority 

![img](22.png)

in Users/Adminstrator/Desktop folder found the root flag 

![img](23.png)

Lets use a metasploit module to gain a meterpreter shell and maintain persistance

![img](24.png)

set LHOST , payload , target

![img](25.png)

command : run -j to start 

![img](26.png)

copy paste the payload in the cmd on windows and we will get a meterpreter shell

![img](27.png)

meterpreter command to maintain persistence is : run persistance -X 

----------------------------------------------THE END-------------------------------------------------------------------------------------------------------------





