# Diffie Hellman

## Parameter Injection 
**Flag:** `crypto{n1c3_0n3_m4ll0ry!!!!!!!!}`

Approach

- step 1<br>
I am Mallory intercepting Alice and Bob's messages.Alice sent this.

```
{"p": "0xffffffffffffffffc90fdaa22168c234c4c6628b80dc1cd129024e088a67cc74020bbea63b139b22514a08798e3404ddef9519b3cd3a431b302b0a6df25f14374fe1356d6d51c245e485b576625e7ec6f44c42e9a637ed6b0bff5cb6f406b7edee386bfb5a899fa5ae9f24117c4b1fe649286651ece45b3dc2007cb8a163bf0598da48361c55d39a69163fa8fd24cf5f83655d23dca3ad961c62f356208552bb9ed529077096966d670c354e4abc9804f1746c08ca237327ffffffffffffffff", "g": "0x02", "A": "0x142932b25abb5c3f469178b98001216c149089c3368756040bf9ca524f089d81a126e1819df08c945d9207125d0bf93ff40e9c26c0fee97e3aca45410a9e66757f92b4deec1ec68b546ec90f822c49afcda2df91bc984e8a59f8e9e608ba1100f3184b52cfe4e443436f8acff79e50f19bbc63288ea16bb28c7fbabf756b8e819b50e639ffa17df2ad8c0cce35180b4d30c2853903dea8fd71da36df4f7547031d425c389b06580fdf5f54d47e670cb27e0efe446d3c8aebc336c0a2a8fe3f74"}
```

- step 2<br>
As the iv and ciphertext is given, we need to fool Alice and cover ourselves as Bob. I share to Bob the exact same set Alice sent me.
Now I intercept the value of B from Bob. For this, I select b = 3, calculate B using B = pow(g,b,p) which is 8. I share the value of B as 8 to Alice and she gives me the iv and ciphertext.
I calculate the shared secret using Alice's A and my b using ss = pow(A,b,p) and give that to the decrypt.py script.


What you learned through solving this challenge:
<br>
-Man in the Middle attack


<br>
<br>
<br>

## Export-grade
**Flag:** `crypto{d0wn6r4d35_4r3_d4n63r0u5}`

Approach

- step 1<br>
For this one, we intercepted this from Alice: {"supported": ["DH1536", "DH1024", "DH512", "DH256", "DH128", "DH64"]}
So we are going to send Bob the least secure DH64 as an option.

```
Send to Bob: {"supported":["DH64"]}
Intercepted from Bob: {"chosen": "DH64"}
Send to Alice: {"chosen": "DH64"}
```

- step 2<br>
Now they generate each other's secret a anf b and exchange public info such as A,b,g,p.

```
Intercepted from Alice: {"p": "0xde26ab651b92a129", "g": "0x2", "A": "0x5f4bdbd075ab16a8"}
Intercepted from Bob: {"B": "0xb4a16ddd7572bcc5"}
Intercepted from Alice: {"iv": "b60b37e1758cf3187b744676db544505", "encrypted_flag": "6e9c6a58a7c0a68d01870f788b456ba39134c723339a166826e8dbad3448884b"}
```

- step 2<br>
Now for DH64,we have to calculate the discrete log of A or B to find the secret key .
I calculate the value of a=4835204181707442854 and find the shared secret ss = pow(B,a,p).
I give it to decrypt.py to get the flag.


What you learned through solving this challenge:
<br>
-Man in the Middle attack

