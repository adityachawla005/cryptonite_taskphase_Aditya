# SRA


**Flag:** `picoCTF{7h053_51n5_4r3_n0_m0r3_b2f9b414}`

Approach

- step 1<br>
We were given the python code of the encryption scheme.
Formula:(p-1) * (q-1) * k = e * d - 1


We can write the following script:

```
from pwn import process, remote
from sage.all import divisors, is_pseudoprime
from Crypto.Util.number import long_to_bytes

io = remote("saturn.picoctf.net", 61367)

io.recvuntil(b"anger = ")
c = int(io.recvline().strip())
io.recvuntil(b"envy = ")
d = int(io.recvline().strip())
e = 65537
kphi = e * d - 1

for pm1 in divisors(kphi):
    p = pm1 + 1
    if is_pseudoprime(p) and p.nbits() == 128:
        for k in range(1, e):
            if kphi % k != 0:
                continue
            q = (kphi // k // pm1) + 1
            if is_pseudoprime(q) and q.nbits() == 128:
                print(f"Found primes: p = {p}, q = {q}")
                n = p * q
                m = pow(c, d, n)
                m = int(m)
                msg = long_to_bytes(m)
                print(f"Decrypted message: {msg}")
                if msg.isalnum():
                    io.sendline(msg)
                    print(io.recvall())
                    exit()
```
Explanation:
It receives a ciphertext and part of an RSA private key, and then tries to find two  prime numbers 128-bit (p and q) by factoring a number derived from the key.
Once it finds the primes, it decrypts the ciphertext using RSA and checks if the resulting message is alphanumeric.
The message is sent back to get the flag.
 


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Cryptography/assets/sra.png)



What you learned through solving this challenge:
<br>
- This code teaches RSA encryption and decryption,prime factorization and  also using sage to test the functionality of pseudo-primes.


Other incorrect methods you tried:
<br>
- none

References
<br>
-[Explanation](https://www.johndcook.com/blog/2018/12/13/rsa-with-pseudoprimes/)
