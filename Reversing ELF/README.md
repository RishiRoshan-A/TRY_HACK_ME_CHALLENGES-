## REVERSING ELF 

![img](1.png)


## CRACKME 1

![img](2.png)

lets download the file and run it 

![img](3.png) 

We successfully got the flag 

## CRACKME 2

![img](4.png)

lets download the file and execute it 

![img](5.png)

seems like we need the password to furthure proceed 

lets run strings command

![img](6.png)
![img](7.png)

we have found the password ,now lets run the file with the password 

![img](8.png)

We successfully found the flag 

## CRACKME 3

![img](9.png)

lets download the file and execute it 

![img](10.png)

here too we require a password 

lets use strings command 

![img](11.png)
![img](12.png)

seems like the password has been encoded with base64 , lets decode it 

![img](13.png)

We successfully found the flag 

## CRACKME 4

![img](14.png)

lets download the file and execute it 

![img](15.png)

lets run strings command 

![img](16.png)
![img](17.png)

no juicy information is found 

lets analysis the file in ghidra 

![img](18.png)

![img](19.png)

in the main function , a compare_pwd function is called , lets analyze it 

![img](20.png)

where a string has been stored in a variable named local_28 and it is passed into the function get_pwd 

lets visit get_pwd function

![img](21.png)

seems like that string has been done xor operation with 0x24 

lets write a python program to perform xor operation 

![img](22.png)

lets run the code 

![img](23.png)

We successfully found the flag 

## CRACKME 5

![img](24.png)

lets download the file and analyze it 

![img](25.png)

lets use strings command 

![img](26.png)

lets use a command : ltrace ./crackme5 

ltrace command is used to trace the function calls , libraies while the program is runnning 

![img](27.png)

seems like our text input test123 has been compared with an string , lets try it as input 

![img](28.png)

We successfully found the flag 

## CRACKME 6 

lets download the file and analyze it 

![img](29.png)

lets use strings command 

![img](30.png)

no useful information is found 

lets use ghidra and analyze the file 

in main there is a compare_pwd function has been calling 

![img](31.png)

lets analyze the compare_pwd function 

![img](32.png)

here my_secure_test function has been calling , lets analyze it 

![img](33.png)

seems like we have found the password as 1337_pwd

![img](34.png)


## CRACKME 7

![img](35.png)

lets download and analyze the file 

![img](36.png)

![img](37.png)

until now no juciy information is found , so lets use ghidra and visit the main function 

![img](38.png)

found that if the input value is equal to 0x7a69 a giveFlag() function has been called 

if we click on that hexa value it will automatically show the decimal value , lets enter that 

![img](39.png)

We successfully found the flag 

## CRACKME 8 

![img](40.png)

lets lets download and analyze the file 

![img](41.png)

![img](42.png)

until now no juicy information is found so , lets use ghidra and analyze the main function

![img](43.png)

seems like our input has been stored in uVar1 variable and if the entered variable is equal to -0x3...ff3 giveFlag() function has been called 

if you click on the hexa value you will see the decimal value of it , lets try it as the password 

![img](44.png)

We successfully found the flag 

-------------------------------------------THE END------------------------------------------------------------
