Write Up

This is a WriteUp for the memlab memory forensic Lab 1. 

Hints:

 **suddenly saw a black window pop up with some thing being executed**
 
**she was trying to draw something**

First i check out the memory profile using image info and use the profile `Win7SP1x64`

Next, i look at the processes that is running. I found 3 process that stands out, mspaint (hint), cmd (hint) and WinRar

mspaint : 2424
WinRAR : 1512
cmd : 1984

So i first dump the cmdlines for these processes which we found out that Alissa have a important.rar, we can use this info later

Next, i use consoles to print out the consoles history and found `ZmxhZ3t0aDFzXzFzX3RoM18xc3Rfc3Q0ZzMhIX0=` so i base64 it and the flag is 

`flag{th1s_1s_th3_1st_st4g3!!}`

Next, i memdump the mspaint memory, and got a dmp file. I was frustrated and didn't know how to proceed, so i look up a write up and found out that i was suppose to change the .dmp file into a .data file and view the data on a image viewer program, which in this case i use gimp. So after tweaking the settings i have a image. The theory was paint is a art program and the dmp file contain the image of the flag




![mspaint memory.png](https://github.com/CoolGuyWithTech/MemLab_Lab_1/blob/main/mspaint%20memory.PNG?raw=true)

And i try rotating it and it didn't work so i try flipping it and the flag was there


![Flip_Image](https://github.com/CoolGuyWithTech/MemLab_Lab_1/blob/main/mspaint%20memory%20(2).PNG?raw=true)

`flag{Good_Boy_good_girl}`


And lastly, we have the WinRAR process to go. 

Since WinRAR is link to files and we also found out the important.rar file that Alissa had, i use filescan to find out the physical memory location of the rar file. 

Next, i use dumpfiles and specific the physical memory location with -Q and the destination location with -D and we got a .dat file  

I rename the file to important.rar and pass it through 7z. 

![ntlm.png](https://github.com/CoolGuyWithTech/MemLab_Lab_1/blob/main/ntlm.PNG)

and we need Alissa NTML hash to unzip the file and i use hashdump and dump Alissa password. We only need the second part of the hash since the first part is LM and the hash also is needed to be uppercase

and we got the 3rd flag 

`flag{w3ll_3rd_stage_was_easy}`

As a beginner, i would say the lab is on the hard side, since i don't know what to do half of the time if no one told me what to do, like in the mspaint process, i would have never thought to dump the file and convert it into a data form. I hope that the lab will have more guidance to help beginners like me. But in the end i still enjoy the lab.  Fluffy Signout~~ ʕ•́ᴥ•̀ʔっ
