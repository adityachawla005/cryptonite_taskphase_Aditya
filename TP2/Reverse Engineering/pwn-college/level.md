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

**Flag:** `pwn.college{cXyyudpmqOzVQmDinFQbDvyiYwk.0VM2IDL1kzM2czW} `

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
The bits have been mangled in the following order
1.Reversed
2.Swap indexes 11 and 16
3.Reversed
I entered xqivthjqkczwowzxtdi as input


```
Connected!                                                                        
hacker@reverse-engineering~level6-0:~$ /challenge/babyrev-level-6-0
###
### Welcome to /challenge/babyrev-level-6-0!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

xqivthjqkczwowzxtdi
Initial input:

	78 71 69 76 74 68 6a 71 6b 63 7a 77 6f 77 7a 78 74 64 69 

This challenge is now mangling your input using the `reverse` mangler.

This mangled your input, resulting in:

	69 64 74 78 7a 77 6f 77 7a 63 6b 71 6a 68 74 76 69 71 78 

This challenge is now mangling your input using the `swap` mangler for indexes `11` and `16`.

This mangled your input, resulting in:

	69 64 74 78 7a 77 6f 77 7a 63 6b 69 6a 68 74 76 71 71 78 

This challenge is now mangling your input using the `reverse` mangler.

This mangled your input, resulting in:

	78 71 71 76 74 68 6a 69 6b 63 7a 77 6f 77 7a 78 74 64 69 

The mangling is done! The resulting bytes will be used for the final comparison.

Final result of mangling input:

	78 71 71 76 74 68 6a 69 6b 63 7a 77 6f 77 7a 78 74 64 69 

Expected result:

	78 71 71 76 74 68 6a 69 6b 63 7a 77 6f 77 7a 78 74 64 69 

Checking the received license key!

You win! Here is your flag:
pwn.college{cXyyudpmqOzVQmDinFQbDvyiYwk.0VM2IDL1kzM2czW}



```

<br>
<br>

# Level 6.1	

**Flag:** `pwn.college{cNyonRYiyWE6AKh6ikQlxrQ9g4X.0lM2IDL1kzM2czW} `

Approach

- step 1<br>
Used ghidra to disassemble and view the EXPECTED RESULT value.
The bits have been mangled in the following order
1.Swap first 7 bits with last 7 bits
2.Bubble Sort
3.Same as 1


```
Connected!                                                                        
hacker@reverse-engineering~level6-1:~$ /challenge/babyrev-level-6-1
###
### Welcome to /challenge/babyrev-level-6-1!
###

This license verifier software will allow you to read the flag. However, before you can do so, you must verify that you
are licensed to read flag files! This program consumes a license key over stdin. Each program may perform entirely
different operations on that input! You must figure out (by reverse engineering this program) what that license key is.
Providing the correct license key will net you the flag!

Ready to receive your license key!

bdeimooprvvxxyz
Checking the received license key!

You win! Here is your flag:
pwn.college{cNyonRYiyWE6AKh6ikQlxrQ9g4X.0lM2IDL1kzM2czW}



```

<br>
<br>

# Level 7	

**Flag:** `pwn.college{c6dGTob2O3hgq9ulW-g6uJ59t52.01M2IDL3AjN1czW} `

Approach

- step 1<br>
We have toreverse the byte order to undo the reverse operation and apply XOR alternately with 0x99 and 0xAB to perform our reverse XOR.

```
Expected result:

        e1 d3 e1 dc ef dd ec df ea d9 eb db f4 c7 f2 c2 f1 cc fe ce fc cf fd c8 f8

Checking the received license key!

You win! Here is your flag:
pwn.college{c6dGTob2O3hgq9ulW-g6uJ59t52.01M2IDL3AjN1czW}


```

<br>
<br>

# Level 8	

**Flag:** `pwn.college{gkfU8kJ9AGOw5afx0OhLKS9f4wf.0VN2IDL3AjN1czW} `

Approach

- step 1<br>
operations:
1.Swap: 12 and 32 index
2.Reverse
3.Swap: 17 and 23 index
4.XOR: With a cyclic key 0xf8, 0xf6, 0x35, 0x9f
5.Reverse
6.Sort: Ascending order
7.Swap: 3 and 17 index

```
Expected result:

        b0 47 f8 64 00 93 8c 79 aa 7c 20 03 77 4f 9c 21 31 25 fe 4f b2 0f 71 2f df 3b 4f 3f 42 74 cc 1a df ca 7a ac 9f

Checking the received license key!

You win! Here is your flag:
pwn.college{gkfU8kJ9AGOw5afx0OhLKS9f4wf.0VN2IDL3AjN1czW}


```

<br>
<br>

# Level 9	

**Flag:** `pwn.college{Msf0y3AiBTHpW2W-J_GHyYHMSd4.01N2IDL1kzM2czW}
 `

Approach

- step 1<br>
It allows us to change any 5 bytes at any address in the memory.
It uses MD5 hashing for the second operation.
We can use NOP sliding to change the Opcodes to 90 (NOP operation) at the offsets.

```bash
0x2911 <main+1185>:	0x75	0x14	0xb8	0x00

```


```
Changing byte 1/5.
Offset (hex) to change: 2911
New value (hex): 90
The byte has been changed: *0x5fbc661b3911 = 90.
Changing byte 2/5.
Offset (hex) to change: 2912
New value (hex): 90
The byte has been changed: *0x5fbc661b3912 = 90.
Changing byte 3/5.
Offset (hex) to change: 0
New value (hex): 0
The byte has been changed: *0x5fbc661b1000 = 0.
Changing byte 4/5.
Offset (hex) to change: 0
New value (hex): 0
The byte has been changed: *0x5fbc661b1000 = 0.
Changing byte 5/5.
Offset (hex) to change: 0
New value (hex): 0
The byte has been changed: *0x5fbc661b1000 = 0.
Ready to receive your license key!

AA
Initial input:

	41 41 0a 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 

This challenge is now mangling your input using the `md5` mangler. This mangler cannot be reversed.

This mangled your input, resulting in:

	e4 16 c0 5e 78 b1 2c be ee 9a 28 b4 b8 3e 64 f0 00 00 00 00 00 00 00 00 00 00 00 00 

The mangling is done! The resulting bytes will be used for the final comparison.

Final result of mangling input:

	e4 16 c0 5e 78 b1 2c be ee 9a 28 b4 b8 3e 64 f0 00 00 00 00 00 00 00 00 00 00 00 00 

Expected result:

	9e 04 ec 85 d8 af b7 dc fa e6 87 99 84 2e 0f 80 00 00 00 00 00 00 00 00 00 00 00 00 

Checking the received license key!

You win! Here is your flag:
pwn.college{Msf0y3AiBTHpW2W-J_GHyYHMSd4.01N2IDL1kzM2czW}



```

<br>
<br>


