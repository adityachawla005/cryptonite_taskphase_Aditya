# Challenge 1-Chaining with Semicolons
This challenge required the use of ; to chain two commands.

## Challenge Description
The easiest way to chain commands is ;. In most contexts, ; separates commands in a similar way to how Enter separates lines. So, this:
```bash
hacker@dojo:~$ echo COLLEGE > pwn
hacker@dojo:~$ cat pwn
COLLEGE
hacker@dojo:~$
```
Is roughly the same as this:
```bash
hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
hacker@dojo:~$
```
Basically, when you hit Enter, your shell executes your typed command and, after that command terminates, give you the prompt to input another command. The semicolon is analogous, just without the prompt and with you entering both commands before anything is executed.

Give it a try now! In this level, you must run /challenge/pwn and then /challenge/college, chaining them with a semicolon.

## Solution
Chaining /challenge/pwn and /challenge/college using ";".

 ```bash
Connected!
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{kWLxw9ZyAZhI398Y3SamuvPzmCc.dVTN4QDL1kzM2czW}
hacker@chaining~chaining-with-semicolons:~$ c

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Chaining%20Commands/assets/ch-1.png)

<br>
<br>
<br>
<br>

# Challenge 2-First Shell Script
This challenge required the creation of a shell script to store commands.

## Challenge Description
As you combine more and more commands to achieve complex effects, the length of the combined prompt quickly gets really annoying to deal with. When this happens, you can put these commands in a file, called a shell script, and run them by executing the file! For example, consider our semicolon technique:
```bash
hacker@dojo:~$ echo COLLEGE > pwn; cat pwn
COLLEGE
hacker@dojo:~$
````
We can create a shell script called pwn.sh (by convention, shell scripts are frequently named with a sh suffix):
```bash
echo COLLEGE > pwn
cat pwn
```
And then we can execute by passing it as an argument to a new instance of our shell (bash)! When a shell is invoked like this, rather than taking commands from the user, it reads commands from the file.
```bash
hacker@dojo:~$ ls
hacker@dojo:~$ bash pwn.sh
COLLEGE
hacker@dojo:~$ ls
pwn
hacker@dojo:~$
```
You can see that the shell script executed both commands, creating and printing the pwn file.

Now, it's your turn! Same as last level, run /challenge/pwn and then /challenge/college, but this time in a shell script called x.sh, then run it with bash!

NOTE: We haven't yet talked about Linux's amazing array of competent command line file editors. For now, feel free to use the Text Editor application in Desktop mode (Applications->Accessories->Text Editor) or the default editor in the VSCode Workspace!

## Solution
Creating a x.sh file and putting the challenge commands in it.Using the command bash to run x.sh.

 ```bash
Connected!
hacker@chaining~your-first-shell-script:~$ nano x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{I6pVbhnlA0EbYYuZaeLjKk28z-H.dFzN4QDL1kzM2czW}


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Chaining%20Commands/assets/ch-21.png)

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Chaining%20Commands/assets/ch-22.png)


<br>
<br>
<br>
<br>

# Challenge 3-redirecting Script Output
This challenge required piping the output of a shell script to another script.

## Challenge Description
Let's try something a bit trickier! You've piped output between programs with |, but so far, this has just been between one command's output and a different command's input. But what if you wanted to send the output of several programs to one command? There are a few ways to do this, and we'll explore a simple one here: redirecting output from your script!

As far as the shell is concerned, your script is just another command. That means you can redirect its input and output just like you did for commands in the Piping module! For example, you can write it to a file:
```bash
hacker@dojo:~$ cat script.sh
echo PWN
echo COLLEGE
hacker@dojo:~$ bash script.sh > output
hacker@dojo:~$ cat output
PWN
COLLEGE
hacker@dojo:~$
```
All of the various redirection methods work: > for stdout, 2> for stderr, < for stdin, >> and 2>> for append-mode redirection, >& for redirecting to other file descriptors, and | for piping to another command.

In this level, we will practice piping (|) from your script to another program. Like before, you need to create a script that calls the /challenge/pwn command followed by the /challenge/college command, and pipe the output of the script into a single invocation of the /challenge/solve command!

## Solution

Creating a shell script with the commands and piping the output of the execution to /challenge/solve.

 ```bash
Connected!
hacker@chaining~redirecting-script-output:~$ nano chal.sh
hacker@chaining~redirecting-script-output:~$ bash chal.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{8SAptxOSrXogyhGOhy-ec5GYDwH.dhTM5QDL1kzM2czW}
hacker@chaining~redirecting-script-output:~$ 


```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Chaining%20Commands/assets/ch-3.png)


<br>
<br>
<br>
<br>

# Challenge 4-Executable Shell Scripts
This challenge required us to make the bash file executable and then invoke the program.

## Challenge Description
You have written your first shell script, but calling it via bash script.sh is a pain. Why do you need that bash?

When you invoke bash script.sh, you are, of course launching the bash command with the script.sh argument. This tells bash to read its commands from script.sh instead of standard input, and thus your shell script is executed.

It turns out that you can avoid the need to manually invoke bash. If your shell script file is executable (recall File Permissions), you can simply invoke it via its relative or absolute path! For example, if you create script.sh in your home directory and make it executable, you can invoke it via /home/hacker/script.sh or ~/script.sh or (if your working directory is /home/hacker) ./script.sh.

Try that here! Make a shellscript that will invoke /challenge/solve, make it executable, and run it without explicitly invoking bash!

## Solution

Creating a shell script with the command and making it executable using chmod to invoke the program without using bash.

 ```bash
 Connected!
hacker@chaining~executable-shell-scripts:~$ nano d.sh
hacker@chaining~executable-shell-scripts:~$ chmod +x d.sh
hacker@chaining~executable-shell-scripts:~$ d.sh
ssh-entrypoint: d.sh: command not found
hacker@chaining~executable-shell-scripts:~$ ./d.sh
Congratulations on your shell script execution! Your flag:
pwn.college{otAfSI4IVJVTmFvIzRYi_6nPLWB.dRzNyUDL1kzM2czW}

```

<br>
<br>

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/Chaining%20Commands/assets/ch-4.png)


