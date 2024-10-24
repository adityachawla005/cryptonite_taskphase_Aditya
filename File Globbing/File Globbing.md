# Challenge 1-Matching with * 
This challenge required the use of globbing with * to change directory.

## Challenge Description
The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as "wildcard" and try to replace that argument with any files that match the pattern. It's easier to show you than explain:
```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_*
Look: file_a file_b file_c
```
Of course, though in this case, the glob resulted in multiple arguments, it can just as simply match only one. For example:
```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: file_*
Look: file_a
```
When zero files are matched, by default, the shell leaves the glob unchanged:
```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: nope_*
Look: nope_*
```
The * matches any part of the filename except for / or a leading . character. For example:
```bash
hacker@dojo:~$ echo ONE: /ho*/*ck*
ONE: /home/hacker
hacker@dojo:~$ echo TWO: /*/hacker
TWO: /home/hacker
hacker@dojo:~$ echo THREE: ../*
THREE: ../hacker
```
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use globbing to keep the argument you pass to cd to at most four characters! Once you're there, run /challenge/run for the flag!

## Solution

Change the directory to /challenge using globbing and then invoke /challenge/run.

 ```bash
Connected!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{onMfAgKL3_LCyxsIihalLttXtXr.dFjM4QDL1kzM2czW}


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/File%20Globbing/assets/1.png)

<br>
<br>
<br>
<br>

# Challenge 2-Matching with ?
This challenge required the use of globbing with ? to change directory.

## Challenge Description

Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as single-character wildcard. This works like *, but only matches one character. For example:
```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_cc
hacker@dojo:~$ ls
file_a	file_b	file_cc
hacker@dojo:~$ echo Look: file_?
Look: file_a file_b
hacker@dojo:~$ echo Look: file_??
Look: file_cc
```
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!

## Solution

Change the directory to /challenge using globbing and then invoke /challenge/run.

 ```bash
Connected!
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{Y-xt81HUyOdUovNrLNxBkKMyXGy.dJjM4QDL1kzM2czW}
hacker@globbing~matching-with-:/challenge$ 


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/File%20Globbing/assets/2.png)

<br>
<br>
<br>
<br>

# Challenge 3-Matching with []
This challenge required the use of globbing to invoke the program for the files in [].

## Challenge Description

Next, we will cover []. The square brackes are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b

Try it here! We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!


## Solution

Change the directory to /challenge/files and then invoke /challenge/run with argument as file_[bash].

 ```bash
onnected!
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{URA3vf0qXSIweDz8P5pKmGJFOea.dNjM4QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/File%20Globbing/assets/3.png)

<br>
<br>
<br>
<br>


# Challenge 4-Matching paths with []
This challenge required the use of globbing to invoke the program for the files in [] by using their absolute paths.

## Challenge Description

Globbing happens on a path basis, so you can expand entire paths with your globbed arguments. For example:
```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
Look: /home/hacker/file_a /home/hacker/file_b
```
Now it's your turn. Once more, we've placed a bunch of files in /challenge/files. Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!

## Solution

Change the directory to /challenge/files and then invoke /challenge/run with argument as /path/file_[bash].

 ```bash
Connected!
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{AvTZP99SEuAEHox9iL0ZGAbf9Ll.dRjM4QDL1kzM2czW}


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/File%20Globbing/assets/4.png)

<br>
<br>
<br>
<br>

# Challenge 5-Mixing Globs
This challenge required the use of globbing with *,[] and ? to show speicific directories.

## Challenge Description

Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that will match the files "challenging", "educational", and "pwning"!

## Solution

Change the directory to /challenge/files and then use echo [cep]*.

 ```bash
Connected!
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ echo [cep]*
challenging educational pwning
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{sbc9C1MF94xkaucjl3uSPUqn-R_.dVjM4QDL1kzM2czW}
hacker@globbing~mixing-globs:/challenge/files$ 



```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/File%20Globbing/assets/5.png)

<br>
<br>
<br>
<br>

# Challenge 6-Exclusionary Globbing
This challenge required the use of globbing by ! along with [].

## Challenge Description

Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. For example:
```bash
hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[!ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[^ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
```
Armed with this knowledge, go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

NOTE: The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep that in mind if things stop making sense! ^ does not have this problem, but is also not compatible with older shells.

## Solution

Change the directory to /challenge/files and then invoke /challenge/run with file_[!pwn]*.

 ```bash
Connected!
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{g_J1sxp2FOPyvmV5WCXcPbKvZD6.dZjM4QDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/File%20Globbing/assets/6.png)
