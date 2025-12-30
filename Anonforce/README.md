## Lets Start with an namp scan 

![img](1.png)

We found that there are two ports are open , lets perform service version detection scan and script default scan on them 

![img](2.png)
![img](3.png)
![img](4.png)

In the namp scan result we can see that Ftp anonymous is allowed , lets login into ftp with username and password as Anonymous 

![img](5.png)

we can see the home folder , lets navigate inside it 

![img](6.png)

We can see an user melodias , lets navigate into the user and see his files

![img](7.png)

We found the user.txt file , use get that to our system 

command : get user.txt

![img](8.png)

We successfully found the user flag 

Lets search for root flag , in ftp we cant able to go or get the root directory as our permission is denied 

In / folder i found an intresting folder notread

![img](9.png)

Lets naviagate inside that folder and see the files 

![img](10.png)

we got an pgp and an asc file ,lets get that two files into our system

![img](11.png)

psg files usually encryted and requires an key like passphase to decrypt the content inside it 

![img](12.png)

Letss view the asc file 

![img](13.png)

we got an pgp key , password protected 

Lets decode the key using john , so first we have to convert the key into an hash format that john can understand and crack it 

![img](14.png)

Lets use john to crack it 

![img](15.png)

we successfully found the passphase of the pgp file 

Lets see the contents of the pgp file 

we are using a tool gpg in order to see the contents inside the pgp file with an passphase

![img](16.png)

it asks for the passphase in an pop up format after entering the command 

now we found the hash value for root user , lets decrypt the hash to find the roots password

lets use hashes.com to crack this hash

![img](17.png)

We successufly found the root password

Lets login into ssh with the root password

![img](18.png)

We successfully found the root flag 

--------------------------------------------------------THE END-----------------------------------------------------------------------





