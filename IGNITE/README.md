# RECON 

Lets perform Nmap full port scan to find the open ports in the target ip 

![img](1.png)

There is only one availabe service running http , lets perform service detection scan and default script scan on it 

![img](2.png) 

From our Scan we found that the site is built with fuel cms 

lets access the site 

![img](3.png)

They have mentioned the username and password in order to login to their dashboard 

![img](4.png)

Since this site is built with fuel cms , lets search for fuel cms avialable  exploits 

# EXPLOITATION 

![img](5.png)

lets try this python exploit to perform a remote code execution 

command : python3 50477.py -u <url> 

![img](6.png)

now we can successfully perform remote code execution , in order to obtain a reverse shell , generate a nc (net cat) reverse shell payload from reverse shell generator 

Make a nc listening in our terminal to capture the connection 

![img](7.png)

we successfully got the reverse shell , lets visits the /home/www-data in order to get the user flag 

![img](8.png) 

# PRIVILAGE ESCLATION 

Lets visits the database file , searching for fuel cms defualt path for database file 

![img](9.png)

lets visits the database.php file 

![img](10.png)

we got the root user password , lets switch to root user and visits the root flag in /root directory 

![img](11.png) 

--------------------------------------THE END---------------------------------------------





