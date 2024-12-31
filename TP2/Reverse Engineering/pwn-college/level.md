# Level 1	

**Flag:** `pwn.college{gwmmteZDfkn1G492tPqkU3HGpnh.0VM1IDL1kzM2czW} `

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
I converted the hex bits to text as 'avaio'.

```
hacker@reverse-engineering~level1-0:~$ /challenge/babyrev-level-1-0
###
### Welcome to /challenge/babyrev-level-1-0!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

avaio
Initial input:

	61 76 61 69 6f 

The mangling is done! The resulting bytes will be used for the final comparison.

Final result of mangling input:

	61 76 61 69 6f 

Expected result:

	61 76 61 69 6f 

Checking the received license key!

You win! Here is your flag:
pwn.college{gwmmteZDfkn1G492tPqkU3HGpnh.0VM1IDL1kzM2czW}

```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/pwn-college/assets/level-1.png) 


What you learned through solving this challenge:
<br>
- Disassembling using Ghidra

<br>
<br>

# Level 1.1	

**Flag:** `pwn.college{s-Z9O7FPbWGGF5_7UWZHXMhO2P-.0lM1IDL1kzM2czW} `

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.

```
Connected!                                                                        
hacker@reverse-engineering~level1-1:~$ /challenge/babyrev-level-1-1
###
### Welcome to /challenge/babyrev-level-1-1!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

chhjb
Checking the received license key!

You win! Here is your flag:
pwn.college{s-Z9O7FPbWGGF5_7UWZHXMhO2P-.0lM1IDL1kzM2czW}



```


What you learned through solving this challenge:
<br>
- Disassembling using Ghidra

<br>
<br>

# Level 2	

**Flag:** ` pwn.college{kQBxdW1Npf5PUV3J510zXTDXIa4.01M1IDL1kzM2czW}`

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
However for this the function mangles the 2nd and 4th index bits.

```
Connected!                                                                        
hacker@reverse-engineering~level2-0:~$ /challenge/babyrev-level-2-0
###
### Welcome to /challenge/babyrev-level-2-0!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

dwnak
Initial input:

	64 77 6e 61 6b 

This challenge is now mangling your input using the `swap` mangler for indexes `2` and `4`.

This mangled your input, resulting in:

	64 77 6b 61 6e 

The mangling is done! The resulting bytes will be used for the final comparison.

Final result of mangling input:

	64 77 6b 61 6e 

Expected result:

	64 77 6b 61 6e 

Checking the received license key!

You win! Here is your flag:
pwn.college{kQBxdW1Npf5PUV3J510zXTDXIa4.01M1IDL1kzM2czW}

```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/pwn-college/assets/2.png) 


What you learned through solving this challenge:
<br>
- Disassembling using Ghidra

<br>
<br>

# Level 2.1	

**Flag:** `pwn.college{Mo-sGddBSpI9LkgbJPiMqE_4iK0.0FN1IDL1kzM2czW}`

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
However for this the function mangles the 1st and 2nd bits.

```
  001014ae 0f b6 45 f2     MOVZX      EAX,byte ptr [RBP + local_16]
        001014b2 88 45 f0        MOV        byte ptr [RBP + local_18],AL
        001014b5 0f b6 45 f3     MOVZX      EAX,byte ptr [RBP + local_16+0x1]
        001014b9 88 45 f1        MOV        byte ptr [RBP + local_17],AL
        001014bc 0f b6 45 f1     MOVZX      EAX,byte ptr [RBP + local_17]
        001014c0 88 45 f2        MOV        byte ptr [RBP + local_16],AL
        001014c3 0f b6 45 f0     MOVZX      EAX,byte ptr [RBP + local_18]
        001014c7 88 45 f3        MOV        byte ptr [RBP + local_16+0x1],AL

```


What you learned through solving this challenge:
<br>
- Disassembling using Ghidra

<br>
<br>

# Level 3	

**Flag:** ` pwn.college{EnjPKbm2gaZ1feL045LMCp39Xs0.0VN1IDL1kzM2czW}`

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
This transformation simply reverses the order of the 5 bytes in local_16.


```
hacker@reverse-engineering~level3-0:~$ /challenge/babyrev-level-3-0
###
### Welcome to /challenge/babyrev-level-3-0!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

ruzox
Initial input:

	72 75 7a 6f 78 

This challenge is now mangling your input using the `reverse` mangler.

This mangled your input, resulting in:

	78 6f 7a 75 72 

The mangling is done! The resulting bytes will be used for the final comparison.

Final result of mangling input:

	78 6f 7a 75 72 

Expected result:

	78 6f 7a 75 72 

Checking the received license key!

You win! Here is your flag:
pwn.college{EnjPKbm2gaZ1feL045LMCp39Xs0.0VN1IDL1kzM2czW}


```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/pwn-college/assets/l-3.png) 


What you learned through solving this challenge:
<br>
- Disassembling using Ghidra

<br>
<br>

# Level 3.1	

**Flag:** `pwn.college{YEweWFzXdZ0eQ105nS2CHkV7bWS.0lN1IDL1kzM2czW}`

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
This transformation simply reverses the order of the 5 bytes.


```
Connected!                                                                        
hacker@reverse-engineering~level3-1:~$ /challenge/babyrev-level-3-1
###
### Welcome to /challenge/babyrev-level-3-1!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

zvfea
Checking the received license key!

You win! Here is your flag:
pwn.college{YEweWFzXdZ0eQ105nS2CHkV7bWS.0lN1IDL1kzM2czW}

```


What you learned through solving this challenge:
<br>
- Disassembling using Ghidra


<br>
<br>

# Level 4	

**Flag:** ` pwn.college{chvf3n6MmRoBGzItSUweMhwA72c.01N1IDL1kzM2czW}`

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
The bits have been mangled using Bubble Sort Algorithm.


```
###
### Welcome to /challenge/babyrev-level-4-0!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

jlvxy
Initial input:

	6a 6c 76 78 79 

This challenge is now mangling your input using the `sort` mangler.

This mangled your input, resulting in:

	6a 6c 76 78 79 

The mangling is done! The resulting bytes will be used for the final comparison.

Final result of mangling input:

	6a 6c 76 78 79 

Expected result:

	6a 6c 76 78 79 

Checking the received license key!

You win! Here is your flag:
pwn.college{chvf3n6MmRoBGzItSUweMhwA72c.01N1IDL1kzM2czW}




```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/pwn-college/assets/l-4.png) 


What you learned through solving this challenge:
<br>
- Disassembling using Ghidra

<br>
<br>

# Level 4.1	

**Flag:** `pwn.college{80Y_wm3kZ8wlIu8nr2nvncprv4R.0FO1IDL1kzM2czW}`

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
The bits have been mangled using Bubble Sort Algorithm.


```
###
### Welcome to /challenge/babyrev-level-4-1!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

imoqw
Checking the received license key!

You win! Here is your flag:
pwn.college{80Y_wm3kZ8wlIu8nr2nvncprv4R.0FO1IDL1kzM2czW}



```


What you learned through solving this challenge:
<br>
- Disassembling using Ghidra


<br>
<br>

# Level 5	

**Flag:** ` pwn.college{sngtKbAG0FW5uuE7wD_xvwCYKD_.0VO1IDL1kzM2czW}`

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
The bits have been mangled using XOR operation with 0xac.


```
###
### Welcome to /challenge/babyrev-level-5-0!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

ecdxi
Initial input:

	65 63 64 78 69 

This challenge is now mangling your input using the `xor` mangler with key `0xac`

This mangled your input, resulting in:

	c9 cf c8 d4 c5 

The mangling is done! The resulting bytes will be used for the final comparison.

Final result of mangling input:

	c9 cf c8 d4 c5 

Expected result:

	c9 cf c8 d4 c5 

Checking the received license key!

You win! Here is your flag:
pwn.college{sngtKbAG0FW5uuE7wD_xvwCYKD_.0VO1IDL1kzM2czW}


```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/pwn-college/assets/l-5.png) 


What you learned through solving this challenge:
<br>
- Disassembling using Ghidra

<br>
<br>

# Level 5.1	

**Flag:** `pwn.college{khSMx0gpY6S_8JjmhmQn_7p9aWB.0FM2IDL1kzM2czW}`

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
The bits have been mangled using XOR operation with 0x1c.


```
###
### Welcome to /challenge/babyrev-level-5-1!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

akwny
Checking the received license key!

You win! Here is your flag:
pwn.college{khSMx0gpY6S_8JjmhmQn_7p9aWB.0FM2IDL1kzM2czW}

```



What you learned through solving this challenge:
<br>
- Disassembling using Ghidra

<br>
<br>

# Level 6	

**Flag:** ` `

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
The bits have been mangled using XOR operation with 0xac.


```



```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/pwn-college/assets/l-6.png) 


What you learned through solving this challenge:
<br>
- Disassembling using Ghidra

<br>
<br>

