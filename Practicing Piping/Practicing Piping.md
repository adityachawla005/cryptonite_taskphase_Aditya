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


<br>
<br>
<br>
<br>

# Challenge 2-Redirecting more output
This challenge required the use of redirecting the output to a file.

## Challenge Description

Aside from redirecting the output of echo, you can, of course, redirect the output of any command. In this level, /challenge/run will once more give you a flag, but only if you redirect its output to the file myflag. Your flag will, of course, end up in the myflag file!

You'll notice that /challenge/run will still happily print to your terminal, despite you redirecting stdout. That's because it communicates its instructions and feedback over standard error, and only prints the flag over standard out!.

## Solution

Redirecting the word /challenge/run output to myflag file.

 ```bash
Connected!
hacker@piping~redirecting-more-output:~$ /challenge/run>myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{UIrTWJC4XunD5FVyj-ScG5x6nZV.dVjN1QDL1kzM2czW}

hacker@piping~redirecting-more-output:~$ 


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/2.png)

<br>
<br>
<br>
<br>


# Challenge 3-Appending Output
This challenge required the use of redirecting in append mode to a file.

## Challenge Description

A common use-case of output redirection is to save off some command results for later analysis. Often times, you want to do this in aggregate: run a bunch of commands, save their output, and grep through it later. In this case, you might want all that output to keep appending to the same file, but > will create a new output file every time, deleting the old contents.

You can redirect input in append mode using >> instead of >, as so:
```bash
hacker@dojo:~$ echo pwn > outfile
hacker@dojo:~$ echo college >> outfile
hacker@dojo:~$ cat outfile
pwn
college
hacker@dojo:$
```

To practice, run /challenge/run with an append-mode redirect of the output to the file /home/hacker/the-flag. The practice will write the first half of the flag to the file, and the second half to stdout if stdout is redirected to the file. If you properly redirect in append-mode, the second half will be appended to the first, but if you redirect in truncation mode (>), the second half will overwrite the first and you won't get the flag!

Go for it now!

## Solution

Redirecting /challenge/run to /home/hacker/the-flag in append mode.

 ```bash
                                                                                                                                                                Connected!
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do 
the first write directly to the file, and the second write, I'll do to stdout 
(if it's pointing at the file). If you redirect the output in append mode, the 
second write will append to (rather than overwrite) the first write, and you'll 
get the whole flag!
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 | 
\|/ This is the first half:
 v 
pwn.college{ENMBUagOuE_b-zw1AhN-6MDqq1r.ddDM5QDL1kzM2czW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>) 
rather than *append* mode (>>), and so the write of the second half to stdout 
overwrote the initial write of the first half directly to the file. Try append 
mode!
hacker@piping~appending-output:~$ 


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/c-3.png)

<br>
<br>
<br>
<br>


# Challenge 4-Redirecting Errors
This challenge required the use of redirecting the output and errors in a file using File Descriptors.

## Challenge Description
Just like standard output, you can also redirect the error channel of commands. Here, we'll learn about File Descriptor numbers. A File Descriptor (FD) is a number the describes a communication channel in Linux. You've already been using them, even though you didn't realize it. We're already familiar with three:

    FD 0: Standard Input
    FD 1: Standard Output
    FD 2: Standard Error

When you redirect process communication, you do it by FD number, though some FD numbers are implicit. For example, a > without a number implies 1>, which redirects FD 1 (Standard Output). Thus, the following two commands are equivalent:

```bash
hacker@dojo:~$ echo hi > asdf
hacker@dojo:~$ echo hi 1> asdf
```
Redirecting errors is pretty easy from this point. If you have a command that might produce data via standard error (such as /challenge/run), you can do:
```bash
hacker@dojo:~$ /challenge/run 2> errors.log
```
That will redirect standard error (FD 2) to the errors.log file. Furthermore, you can redirect multiple file descriptors at the same time! For example:
```bash
hacker@dojo:~$ some_command > output.log 2> errors.log
```
That command will redirect output to output.log and errors to errors.log.

Let's put this into practice! In this challenge, you will need to redirect the output of /challenge/run, like before, to myflag, and the "errors" (in our case, the instructions) to instructions. You'll notice that nothing will be printed to the terminal, because you have redirected everything! You can find the instructions/feedback in instructions and the flag in myflag when you successfully pull this off!

## Solution
Redirect the output of /challenge/flag to myflag and the errors to instructions.

 ```bash
Connected!                                                                        
hacker@piping~redirecting-errors:~$ /challenge/run>myflag  /challenge/run 2>instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{gVuSVQcaPUd_CNDJWD1Ta6rdx8L.ddjN1QDL1kzM2czW}


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/c-4.png)

<br>
<br>
<br>
<br>

# Challenge 4-Redirecting input
This challenge required the use of redirecting the input in a file.

## Challenge Description
Just like you can redirect output from programs, you can redirect input to programs! This is done using <, as so:
```bash
hacker@dojo:~$ echo yo > message
hacker@dojo:~$ cat message
yo
hacker@dojo:~$ rev < message
oy
```
You can do interesting things with a lot of different programs using input redirection! In this level, we will practice using /challenge/run, which will require you to redirect the PWN file to it and have the PWN file contain the value COLLEGE! To write that value to the PWN file, recall the prior challenge on output redirection from echo!

## Solution
Redirect the output COLLEGE to PWN and further redirect it as input to /challenge/run.

 ```bash
Connected!
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read 
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{At043z1DpVDTl9Iqc9ukvO_VIm3.dBzN1QDL1kzM2czW}



```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/c-5.png)

<br>
<br>
<br>
<br>

# Challenge 6-Grepping Stored Results
This challenge required the use of redirecting the output to a file and using grep command.

## Challenge Description
You know how to run commands, how to redirect their output (e.g., >), and how to search through the resulting file (e.g., grep). Let's put this together!

In preparation for more complex levels, we want you to:

    Redirect the output of /challenge/run to /tmp/data.txt.
    This will result in a hundred thousand lines of text, with one of them being the flag, in /tmp/data.txt.
    Grep that for the flag!

## Solution
Redirect the output of /challenge/run to /tmp/data.txt.Then use grep command for the flag.

 ```bash
Connected!
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$ grep pwn.college /tmp/data.txt
pwn.college{4hNQU5zpT2s89k2-JL513MYhC2_.dhTM4QDL1kzM2czW}
hacker@piping~grepping-stored-results:~$ 




```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/c-6.png)

<br>
<br>
<br>
<br>

# Challenge 7-Grepping live output
This challenge required the use of redirecting the output and grepping at the same time using | operator.

## Challenge Description

It turns out that you can "cut out the middleman" and avoid the need to store results to a file, like you did in the last level. You can use this using the | (pipe) operator. Standard output from the command to the left of the pipe will be connected to (piped into) the standard input of the command to the right of the pipe. For example:
```bash
hacker@dojo:~$ echo no-no | grep yes
hacker@dojo:~$ echo yes-yes | grep yes
yes-yes
hacker@dojo:~$ echo yes-yes | grep no
hacker@dojo:~$ echo no-no | grep no
no-no
```
Now try it for yourself! /challenge/run will output a hundred thousand lines of text, including the flag. Grep for the flag!

## Solution
Redirect the output of /challenge/run and grep "pwn.college" using | operator.

 ```bash
                                                                                                                                                    Connected!
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{QJFEkXxKqGOWaq_wYFV_fUYZ9RV.dlTM4QDL1kzM2czW}
hacker@piping~grepping-live-output:~$ ^C
hacker@piping~grepping-live-output:~$ 




```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/c-7.png)

<br>
<br>
<br>
<br>

# Challenge 8-Grepping Errors
This challenge required the use of redirecting the output and errors and grepping at the same time using | operator.

## Challenge Description
You know how to redirect errors to a file, and you know how to pipe output to another program, such as grep. But what if you wanted to grep through errors directly?

The > operator redirects a given file descriptor to a file, and you've used 2> to redirect fd 2, which is standard error. The | operator redirects only standard output to another program, and there is no 2| form of the operator! It can only redirect standard output (file descriptor 1).

Luckily, where there's a shell, there's a way!

The shell has a >& operator, which redirects a file descriptor to another file descriptor. This means that we can have a two-step process to grep through errors: first, we redirect standard error to standard output (2>& 1) and then pipe the now-combined stderr and stdout as normal (|)!

Try it now! Like the last level, this level will overwhelm you with output, but this time on standard error. Grep through it to find the flag!

## Solution
Redirect the output and errors of /challenge/run and grep "pwn.college" using | and & operator.

 ```bash
Connected!                                                                        
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/xpq4yhadyhazkcsggmqd7rsgvxb3kjy4-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{0mjkqVHsDRW7y-SrvOUyU4p89e9.dVDM5QDL1kzM2czW}
hacker@piping~grepping-errors:~$ 

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/c-8.png)

<br>
<br>
<br>
<br>

# Challenge 9-Duplicating piped data with tee
This challenge required the use of tee command to intercept the input going from one program to another via piping.

## Challenge Description
When you pipe data from one command to another, you of course no longer see it on your screen. This is not always desired: for example, you might want to see the data as it flows through between your commands to debug unintended outcomes (e.g., "why did that second command not work???").

Luckily, there is a solution! The tee command, named after a "T-splitter" from plumbing pipes, duplicates data flowing through your pipes to any number of files provided on the command line. For example:
```bash
hacker@dojo:~$ echo hi | tee pwn college
hi
hacker@dojo:~$ cat pwn
hi
hacker@dojo:~$ cat college
hi
hacker@dojo:~$
```
As you can see, by providing two files to tee, we ended up with three copies of the piped-in data: one to stdout, one to the pwn file, and one to the college file. You can imagine how you might use this to debug things going haywire:
```bash
hacker@dojo:~$ command_1 | command_2
Command 2 failed!
hacker@dojo:~$ command_1 | tee cmd1_output | command_2
Command 2 failed!
hacker@dojo:~$ cat cmd1_output
Command 1 failed: must pass --succeed!
hacker@dojo:~$ command_1 --succeed | command_2
Commands succeeded!
```
Now, you try it! This process' /challenge/pwn must be piped into /challenge/college, but you'll need to intercept the data to see what pwn needs from you!

## Solution
Redirect the output of /challenge/pwn to a file called command then change the input going to /challenge/college as per the hint given.
 ```bash
Connected!                                                                        
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn | tee command
Processing...
You are trying to use 'tee' *instead* of /challenge/college. Use it *between* 
/challenge/pwn and /challenge/college!
You must pipe the output of /challenge/pwn into /challenge/college (or 'tee' 
for debugging).
hacker@piping~duplicating-piped-data-with-tee:~$ cat command
Usage: /challenge/pwn --secret [SECRET_ARG]

SECRET_ARG should be "8gdYCe88"
hacker@piping~duplicating-piped-data-with-tee:~$ /challenge/pwn --secret 8gdYCe88 | /challenge/college
Processing...
Correct! Passing secret value to /challenge/college...
Great job! Here is your flag:
pwn.college{8gdYCe88pJ4mdflhD1yK5GuLq9V.dFjM5QDL1kzM2czW}
```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/c-9.png)

<br>
<br>
<br>
<br>

# Challenge 9-Writing to multiple programs
This challenge required us to duplicate the output of one program to two programs using tee command.

## Challenge Description
Okay, so you can duplicate data to two files with tee:
```bash
hacker@dojo:~$ echo HACK | tee THE > PLANET
hacker@dojo:~$ cat THE
HACK
hacker@dojo:~$ cat PLANET
HACK
hacker@dojo:~$
```
And you've used tee to duplicate data to a file and a command:
```bash
hacker@dojo:~$ echo HACK | tee THE | cat
HACK
hacker@dojo:~$ cat THE
HACK
hacker@dojo:~$
```
But what about duplicating to two commands? As tee says in its manpage, it's designed to write to files and to standard output:

TEE(1)                           User Commands                          TEE(1)

NAME
       tee - read from standard input and write to standard output and files

Luckily, Linux follows the philosophy that "everything is a file". This is, the system strives to provide file-like access to most resources, including the input and output of running programs! The shell follows this philosophy, allowing you to, for example, use any utility that takes file arguments on the command line (such as tee) and hook it up to the input or output side of a program!

This is done using what's called Process Substitution. If you write an argument of >(rev), bash will run the rev command (this command reads data from standard input, reverses its order, and writes it to standard output!), but hook up its input to a temporary file that it will create. This isn't a real file, of course, it's what's called a named pipe, in that it has a file name:
```bash
hacker@dojo:~$ echo >(rev)
/dev/fd/63
hacker@dojo:~$
```
Where did /dev/fd/63 come from? bash replaced >(rev) with the path of the named pipe file that's hooked up to rev's input! While the command is running, writing to this file will pipe data to the standard input of the command. Typically, this is done using commands that take output files as arguments (like tee):
```bash
hacker@dojo:~$ echo HACK | rev
KCAH
hacker@dojo:~$ echo HACK | tee >(rev)
HACK
KCAH
```
Above, the following sequence of events took place:

    bash started up the rev command, hooking a named pipe (presumably /dev/fd/63) to rev's standard input
    bash started up the tee command, hooking a pipe to its standard input, and replacing the first argument to tee with /dev/fd/63. tee never even saw the argument >(rev); the shell substituted it before launching tee
    bash used the echo builtin to print HACK into tee's standard input
    tee read HACK, wrote it to standard output, and then wrote it to /dev/fd/63 (which is connected to rev's stdin)
    rev read HACK from its standard input, reversed it, and wrote KCAH to standard output

Now it's your turn! In this challenge, we have /challenge/hack, /challenge/the, and /challenge/planet. Run the /challenge/hack command, and duplicate its output as input to both the /challenge/the and the /challenge/planet commands!

Trivia!

The observant learner will realize that the following are equivalant:
```bash
hacker@dojo:~$ echo hi | rev
ih
hacker@dojo:~$ echo hi > >(rev)
ih
hacker@dojo:~$
```
More than one way to pipe data! Of course, the second route is way harder to read and also harder to expand. For example:
```bash
hacker@dojo:~$ echo hi | rev | rev
hi
hacker@dojo:~$ echo hi > >(rev | rev)
hi
hacker@dojo:~$
```
That's just silly! The lesson here is that, while Process Substitution is a powerful tool in your toolbox, it's a very specialized tool; don't use it for everything!

## Solution
Redirect the output of /challenge/hack to /challenge/the and /challenge/planet using tee command and | operator.
 ```bash
Connected!                                                                        
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >(/challenge/the)|tee >(/challenge/planet)
This secret data must directly and simultaneously make it to /challenge/the and 
/challenge/planet. Don't try to copy-paste it; it changes too fast.
19400288871383914137
Congratulations, you have duplicated data into the input of two programs! Here 
is your flag:
pwn.college{UftqN4sRFKLF-ZZ-s1EFbBcTvzv.dBDO0UDL1kzM2czW}
hacker@piping~writing-to-multiple-programs:~$ 

```
<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/c-10.png)

<br>
<br>
<br>
<br>

# Challenge 11-Split piping stderr and stdout
This challenge required the use of combining the concepts of >(), 2>and | to send stderr and stdout through different pipes.

## Challenge Description
Now, let's put your knowledge together. You must master the ultimate piping task: redirect stdout to one program and stderr to another.

The challenge here, of course, is that the | operator links the stdout of the left command with the stdin of the right command. Of course, you've used 2>&1 to redirect stderr into stdout and, thus, pipe stderr over, but this then mixes stderr and stdout. How to keep it unmixed?

You will need to combine your knowledge of >(), 2>, and |. How to do it is a task I'll leave to you.

In this challenge, you have:

    /challenge/hack: this produces data on stdout and stderr
    /challenge/the: you must redirect hack's stderr to this program
    /challenge/planet: you must redirect hack's stdout to this program

Go get the flag!


## Solution
Redirecting the error stream of hack to the and output stream to planet.
```bash
Connected!                                                                        
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts 
struggle with! Here is your flag:
pwn.college{865E6xlzeh6LG3odavdL82GTOeN.dFDNwYDL1kzM2czW}
hacker@piping~split-piping-stderr-and-stdout:~$ 

```

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Practicing%20Piping/assets/c-11.png)
