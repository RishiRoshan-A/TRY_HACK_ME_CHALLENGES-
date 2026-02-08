![img](1.png)

## The first question we want to convert everything to text

![img](2.png)

## The second 

![img](3.png)

seems like the data are in binary format , lets use cyber chef to convert it into text

![img](4.png)

## The Third 

![img](5.png)

seems like it is base32 encoded , lets decode it 

![img](6.png)
![img](7.png)

## The Fourth 

![img](9.png)

seems like the data is in hexa decimal format , lets convert it into text using cyberchef

![img](10.png)

## THE FIFTH 

![img](11.png)

Seems like the text has been altered usign rot13 , lets try rot13 decoder to decrypt it

![img](12.png)

## THE SIXTH 

![img](13.png)

Seems like it is rot47 encoded , lets decode it 

![img](14.png)

## THE SEVENTH 

![img](15.png)

seems like the text has been encoded with Morse code , lets decode it 

![img](16.png)

## THE EIGHT

![img](17.png)

seems like the data has been given in decimal format , lets convert it into text 

![img](18.png)


## THE NINE 

![img](19.png)

the text has been encrypted with so many layers of techniques , lets decrypt it 

base64 --> morse code --> binary --> ROT47 --> Decimal --> Text 

![img](20.png)

## THE TEN 

![img](21.png)

We have been given a audio file , while hearing that it seems like that it is some sort of signals 

lets use sonic visualiser to analyse it 

![img](22.png)

click on file and add the video file we downloaded 

![img](23.png)

click on layer and click on Add spectogram 

![img](24.png)

lets expand it 

![img](25.png)

We successfully find the flag 

## THE ELEVEN 

![img](26.png)

Lets download the task file 

lets use file command to see the property of the file 

![img](27.png)

lets use exitfool to see the metadata of the file 

![img](28.png)

lets use strings command to see the image data into an human readable format 

![img](29.png)

so far no useful information is found , lets use stegseek to see if the file contains any attached file inside it 

![img](30.png)

We successfully found the flag 

## THE TWELVE 

![img](31.png)

similary using file and exiftool command 

![img](32.png)

lets use binwalk tool to see the any check any file is compressed with the file 

![img](33.png)

we extracted all the file compressed within it 

![img](34.png)

lets use strings command on hackerchat.png 

![img](35.png)
![img](36.png)

![img](37.png)

We successfully found the flag 

------------------------------------------THE END------------------------------------------------




