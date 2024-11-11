# No Padding,No Problem

**Flag:** `picoCTF{m4yb3_Th0se_m3s54g3s_4r3_difurrent_5814368}`

Approach

- step 1<br>
In a homomorphic encryption scheme, encrypting two values and then multiplying the encrypted results is the same as encrypting the product of the original values.
We make use of the formula of multiplying ciphertext c* pow(2, e, n) and dividing by 2 to get the flag and convert it into hexadecimal string.

```
bytearray.fromhex(format(m, 'x')).decode()
'picoCTF{m4yb3_Th0se_m3s54g3s_4r3_difurrent_5052620}'

```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Cryptography/assets/nop.png)



What you learned through solving this challenge:
<br>
-We learn that unpadded RSA is homomorphic.


Other incorrect methods you tried:
<br>
- Tried writing a python script for getting the flag.


References
<br>
- [Formula](https://www.splunk.com/en_us/blog/learn/homomorphic-encryption.html)
