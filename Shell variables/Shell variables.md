# Challenge 1-Redirecting Output
This challenge required the use of redirecting the output to a file.

## Challenge Description
First, let's look at redirect stdout to files. You can accomplish this with the > character, as so:
```bash
hacker@dojo:~$ echo hi > asdf
```
This will redirect the output of echo hi (which will be hi) to the file asdf. You can then use a program such as cat to output this file:
```bash
hacker@dojo:~$ cat asdf
hi
```
In this challenge, you must use this input redirection to write the word PWN (all uppercase) to the filename COLLEGE (all uppercase).
## Solution

Redirecting the word PWN to COLLEGE file.

 ```bash
Connected!
You have created the COLLEGE file and wrote the right value to it, but it 
doesn't look like you did it via input redirection.
hacker@piping~redirecting-output:~$ echo PWN>COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your 
flag:
pwn.college{gjIQ9oGr6CCirLUbazGp-ceODYc.dRjN1QDL1kzM2czW}


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/c-1.png)

<br>
<br>
<br>
<br>
