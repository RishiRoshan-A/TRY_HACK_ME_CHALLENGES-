## Lets start with an nmap scan 

![img](1.png)

we found 5 open ports , lets perform service version detection scan and default script scan on them 

![img](2.png)

![img](3.png)

When i try to visit the site running on port 80 it redirects to port 4040

![img](4.png)

I tired using gobuter to enemurate web directories and also inspected the page for any information disclosure but no information is found

seems like there is a service listening on port 9009 , lets use net cat to connect to it 

![img](5.png)

we cant able to excute commands but it seems like we can get the private key and client certificate 

![img](6.png)

![img](7.png)

Lets copy them both into a separte file 

in our nmap scan we found ssl service is active on port 54321 , lets use this private key and client certificate to connect to it

![img](8.png)

![img](9.png)

Seems like here also we cant able to execute commands , type password to get the password hints

![img](10.png)

We found a username barney and the password seems to be it is hashed with md5 , but i cant to crack it , so lets try the same password to login into ssh 

![img](11.png)

we successfully found the barley.txt file 

i found a user fred and listed his files there is a file called fred.txt but we cant able to visit it as our permission is denied

![img](12.png)

Lets try sudo -l to see what the current user can run with root privilage

![img](13.png)

certutil command is used to list the certificates , manage certificates etc .. 

lets use it view the certifictes of fred 

![img](14.png)

lets view the fred.certificate.pem file 

![img](15.png)
![img](16.png)

We got the freds private key and certificate 

similary lets connect to ssl serivce and retrive the freds password

![img](17.png)

![img](18.png)

We successfully got the freds password , lets login into ssh with username fred and the password 

![img](19.png)

We successfully got the fred.txt file 

type command sudo -l to see what command this current user can run with root privilage 

![img](20.png)

seems like we can encode the root password with base64 

![img](21.png)

Lets decode it with base64 

![img](22.png)

We got an encrytped text , lets try cyber chef which automatically identifies and decrypts the text when we click on the magic icon 

![img](23.png)

seems like it is an md5 hash , lets use hashes.com to crack it 

![img](24.png)

We successfully found the root password , lets escalte to root privilage and view the root flag

![img](25.png)



