## Lets start with an Nmap Scan 

![img](1.png)

Found three open ports , lets perform service version detection and default script scan on them 

![img](2.png)

lets visit the site running on port 8080 

![img](3.png)

On clicking on Manage App it popup a login page 

![img](4.png)

on 401 unauthorized page we found the username and password , lets login with those credentials 

![img](5.png)

after login found a file upload functionality , seems like we can only upload war files 

![img](6.png)

lets creat a java payload with msfvenom with .war extension 

![img](7.png)

lets set up a multi/handler for receving our connection 

![img](8.png)

![img](9.png)

our test.war payload has been uploaded , click on the /test to access it 

![img](10.png)

![img](11.png)

we got our reverse shell , there is post exploit module in metasploit to upgrade our shell to meterpreter , lets try that 

![img](12.png)

![img](13.png)

We successfully found got the meterpreter shell , lets visit the /home
/jack folder 

![img](14.png)

![img](15.png)

![img](16.png)

We successfully found our user flag , lets esclate our privilege to find the root flag

tried sudo -l , searched for files with suid permission but no privilege esclation factor has been found , lets visits the crontab 

![img](17.png)

found that root user has been executing  a id.sh script every minute , we have read and write permission to the id.sh script 

![img](18.png)

so generate a bash reverse shell and modify the contents of the id.sh file with our reverse shell 

![img](19.png)

set up a nc listener 

![img](20.png)

lets modify the contents of id.sh with our reverse shell 

![img](21.png)

after some seconds we got a reverse shell with root privilege 

![img](22.png)

lets navigate to root directory and read the root.txt 

![img](23.png)

We successfully found the root flag 

----------------------------------------------------THE END---------------------------------------------------------

