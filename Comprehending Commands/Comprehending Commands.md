# Challenge 1-cat:not the pet,but the command!
This level required the use of reading the contents of flag file with cat command.

## Challenge Description
One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:

hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:

cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:

```bash
hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!
```

Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later challenges...

In this challenge, I will copy the flag to the flag file in your home directory (where your shell starts). Go read it with cat!



## Solution

Using the command cat with flag to read its contents in the current directory.

 ```bash
Connected!
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{4VQhCrQjskrYC-bzBM0PyXwCOZs.dFzN1QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/1.png)

<br>
<br>
<br>
<br>

# Challenge 2-catting absolute paths
This level required the use of reading the contents of flag file with cat command and the file's absolute path.

## Challenge Description
In the last level, you did cat flag to read the flag out of your home directory! You can, of course, specify cat's arguments as absolute paths:

```bash
hacker@dojo:~$ cat /challenge/DESCRIPTION.md
In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths:
...
```

In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.

FUN FACT: /flag is where the flag always lives in pwn.college, but unlike in this challenge, you typically can't access that file directly.


## Solution

Using the command cat with absolute path /flag to read its contents.

 ```bash
Connected!
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{MetMmt7W_RBxzWKSQ8aCq42cCAn.dlTM5QDL1kzM2czW}
```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/2.png)

<br>
<br>
<br>
<br>

# Challenge 3-more catting practice
This level required the use of reading the contents of flag file with cat command and the file's absolute path.

## Challenge Description
You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with cd, so no cat flag for you. You must 

In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.


## Solution

 Using the command cat with absolute path /flag to read its contents.

 ```bash
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/share/systemd/flag. Go cat it out **without** cding into that 
directory!
hacker@commands~more-catting-practice:~$ cat /usr/share/systemd/flag
pwn.college{U0b1cVSr7WAGywrVCyrdufGEVSy.dBjM5QDL1kzM2czW}
```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/3.png)

<br>
<br>
<br>
<br>

# Challenge 3-more catting practice
This level required the use of reading the contents of flag file with cat command and the file's absolute path.

## Challenge Description
You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with cd, so no cat flag for you. You must 

In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.


## Solution

 Using the command cat with absolute path /flag to read its contents.

 ```bash
Connected!
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/share/systemd/flag. Go cat it out **without** cding into that 
directory!
hacker@commands~more-catting-practice:~$ cat /usr/share/systemd/flag
pwn.college{U0b1cVSr7WAGywrVCyrdufGEVSy.dBjM5QDL1kzM2czW}
```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Comprehending%20Commands/assets/3.png)




