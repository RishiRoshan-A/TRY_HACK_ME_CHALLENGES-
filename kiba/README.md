## RECON 

Lets start with our nmap full port scan on the target ip 

![img](1.png)

found that there are 4 open ports , lets perform service version detection scan and default scan on them 

![img](2.png)

lets visit the service running on port 80 

![img](3.png)

performed directory enemuration , but no juicy information is found , so lets move on to port 5601

while accessing the port 5601 there comes a kibana interface and while exploring functionalities in dev tools modifying the GET requests to GET / and got the version of the kibana 

![img](4.png)

Found that kibana 6.5.4 is vulnerable to rce via cve-2019-7609 

![img](5.png)

and found the exploit code for cve-2018-7601

![img](6.png)

## EXPLOITATION 

![img](7.png)

set up  a nc listener and run our python exploit 

![img](8.png)

We successuflly got the reverse shell and in /home/kiba found the user.txt file

![img](9.png)

## PRIVILAGE ESCLATION 

We successuflly got the reverse shell and in /home/kiba found the user.txt file
--> command : getcap -r / 2>/dev/null --> to list the files with capabilities 

![img](10.png)

We successuflly got the reverse shell and in /home/kiba found the user.txt file
python3 has been set to cap_setuid that means Change the process's user ID

![img](11.png)

utilizing gtfo bins to exploit the python3 capabilities 

![img](12.png)

we successflly found the root.txt file 

------------------------------------------------------THE END-----------------------------------------
