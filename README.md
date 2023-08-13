<h1>🕵🏻‍♀️🔐🚩 Digital Forensics Investigation CTF</h1>

<h2>Description:</h2>

- <b>Exposure to Digital Forensics concepts such as evidence types and Chain of Custody</b> 
- <b>Retriving of hidden information hidden inside Steganography files</b>
- <b>Conduct dictionary and brute-force attacks to crack passworded ZIP files using Linux CLI</b>
- <b>CTF activity to simulate an investigation on a hard drive.</b>

<h2>Languages and Utilities Used:</h2>

- <b>Challenge Disk Image[Security Blue Team] </b>
- <b>steghide apt [Kali Linux]</b> 
- <b>fcrackzip apt [Kali Linux]</b>
- <b>rockyou.txt to conduct dictionary attacks [Kali Linux]</b>
- <b>Bash</b> 

<h2>Environments Used: </h2>

- <b>Oracle VirtualBox Machine</b>
- <b>Kali Linux OS </b> 

<h2>Challenge Brief:</h2>
<p align="center">
<img src=https://i.imgur.com/DlaMPAc.png" height="80%" width="80%" /><br/>

<h2>Challenge Disk Image:</h2>
<p align="center">
<img src=https://i.imgur.com/sLugpcZ.png" height="80%" width="80%" /><br/>  
<b>We are tasked to find 4 different clues for this activity. </b>  <br/>
<b>We will use the following methods and techniques for investigation: </b>  <br/>
<br/>
1. Using the CLI command [ls -a], go through every directory, and scan through every file including hidden ones. <br/>
2. For suspicious files we will use the [file] command to check if the file extension has been altered to hide information. <br/>
3. Look through every file with [cat, strings, head] command to view contents. <br/>
4. Run steghide apt for image and audio files to check if it is a steganography file. <br/>
5. Run fcrackzip apt for password-protected zip files to launch a brute force or dictionary attack to unlock contents. <br/>

<h2>Program walk-through:</h2>

<p align="center">
<b>Clue {1 of 4}</b><br/>
  
<br/>
 1. Hidden password-protected zip folder found in [J Harrison Disk Image 10.09.2019/WebDev work/unfinished webpages/to-do] path <br/>
<br/>
<img src="https://i.imgur.com/9ZBPJZQ.png" height="80%" width="80%" /> <br/>
  
<p align="center">
2. Launch dictionary attack to extract password [brute force attack is also viable]<br/>
3. In this case we will be using the rockyou.txt dictionary list that is preinstalled on Kali <br/>
4. Run command [fcrackzip -D -u -p /home/kevinyyh/Downloads/rockyou.txt .a0415ns.zip]<br/>
5. Extract the zip file with password [vendy13031988] <br/>
<img src="https://i.imgur.com/udGPQ5O.png" height="80%" width="80%" />
<br />

<p align="center">
6. View contents of newly extracted employeedump file  <br/>
<img src="https://imgur.com/fNZCM7Q.png" height="80%" width="80%" />
<br />
 
<p align="center">
<b>Unofficial Clue</b><br/>
<br/>
 1. Suspicious jpg file found in [/J Harrison Disk Image 10.09.2019/Saved Emails] path <br/>
 2. Run the [cat, heads, strings] command to see if there's any information <br/>
<img src=https://i.imgur.com/YEVIrlq.png" height="80%" width="80%" /> <br/>
<img src=https://i.imgur.com/oX5Z3sK.png" height="80%" width="80%" /> <br/>
<br/>
 3. We are given a clue. The password to extract stego files is 'password' <br/>
<br/>

<p align="center">
<b>Clue {2 of 4}</b><br/>
<br/>
 1. Multiple audio and image files found in [J Harrison Disk Image 10.09.2019/Images] path which could potentially be stego files <br/>
 2. Run command [steghide extract -sf 'file name'] for all files using [password] as the password.<br/>
 3. Output if the file is not a stego file:
<img src=https://i.imgur.com/0V94Dvn.png" height="80%" width="80%" /> <br/>
 4. File name [laptop.jpg] returned as a stego file. <br/>
<img src=https://i.imgur.com/xPGlfrb.png" height="80%" width="80%" /> <br/>
 5. Open extracted ASCII text file [passwords] <br/>
<img src=https://i.imgur.com/ijpFM7R.png" height="80%" width="80%" /> <br/>

<p align="center">
<b>Clue {3 of 4}</b><br/>
<br/>
 1. Files found in [J Harrison Disk Image 10.09.2019/Weekly Meeting Notes/Week 10] <br/>
 2. Using [file] command we can see that posidon.xml is actually a png image file<br/>
<img src=https://i.imgur.com/BsDHbDb.png" height="80%" width="80%" /> <br/>
<br/>
 3. Change file extension to .jpg using mv command as Kali opens image files via jpg<br/>
<img src=https://i.imgur.com/g671Pb7.png" height="80%" width="80%" /> <br/>
 4. Open the image file in GUI
<img src=https://i.imgur.com/jvQQ8VH.png" height="80%" width="80%" /> <br/>

<p align="center">
<b>Clue {4 of 4}</b><br/>
<br/>
 1. Suspicious extension file [bootstrap.min.abc] found in css folder path [WebDev work/unfinished webpages/templatemo_508_power/css] <br/>
 2. Run the [cat, head, strings] command to view contents.<br/>
<img src=https://i.imgur.com/Q2En0kk.png" height="80%" width="80%" /> <br/>
<img src=https://i.imgur.com/tWoUlQS.png" height="80%" width="80%" /> <br/>
 








</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
