# RSA

## Starters

![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Cryptography/assets/starter.png)


## Crossed Wires 
**Flag:** `crypto{3ncrypt_y0ur_s3cr3t_w1th_y0ur_fr1end5_publ1c_k3y}`

Approach

- step 1<br>
We first save the list of the friends' private keys as an array for future use fr = [106979, 108533, 69557, 97117, 103231].
we can write the following script to get p and q value.

```
    k = d * e - 1
    t = k
    while True:
        g = random.randint(2, n - 1)
        while True:
            if t % 2 == 0:
                t = t // 2
                x = pow(g, t, n)
                if x > 1:
                    y = gcd(x - 1, n)
                    if y > 1:
                        p = y
                        q = n // y
                        return (p, q)
            else:
                break

```

- step 2<br>
We can take the friends' private keys in reverse order to decrypt the ciphertext.

<br>
<br>
<br>

## Square Eyes
**Flag:** `crypto{squar3_r00t_i5_f4st3r_th4n_f4ct0r1ng!}`

Approach

- step 1<br>
A file output.txt was provided to us with the following content.

```
n = 535860808044009550029177135708168016201451343147313565371014459027743491739422885443084705720731409713775527993719682583669164873806842043288439828071789970694759080842162253955259590552283047728782812946845160334801782088068154453021936721710269050985805054692096738777321796153384024897615594493453068138341203673749514094546000253631902991617197847584519694152122765406982133526594928685232381934742152195861380221224370858128736975959176861651044370378539093990198336298572944512738570839396588590096813217791191895941380464803377602779240663133834952329316862399581950590588006371221334128215409197603236942597674756728212232134056562716399155080108881105952768189193728827484667349378091100068224404684701674782399200373192433062767622841264055426035349769018117299620554803902490432339600566432246795818167460916180647394169157647245603555692735630862148715428791242764799469896924753470539857080767170052783918273180304835318388177089674231640910337743789750979216202573226794240332797892868276309400253925932223895530714169648116569013581643192341931800785254715083294526325980247219218364118877864892068185905587410977152737936310734712276956663192182487672474651103240004173381041237906849437490609652395748868434296753449
e = 65537
ct = 222502885974182429500948389840563415291534726891354573907329512556439632810921927905220486727807436668035929302442754225952786602492250448020341217733646472982286222338860566076161977786095675944552232391481278782019346283900959677167026636830252067048759720251671811058647569724495547940966885025629807079171218371644528053562232396674283745310132242492367274184667845174514466834132589971388067076980563188513333661165819462428837210575342101036356974189393390097403614434491507672459254969638032776897417674577487775755539964915035731988499983726435005007850876000232292458554577437739427313453671492956668188219600633325930981748162455965093222648173134777571527681591366164711307355510889316052064146089646772869610726671696699221157985834325663661400034831442431209123478778078255846830522226390964119818784903330200488705212765569163495571851459355520398928214206285080883954881888668509262455490889283862560453598662919522224935145694435885396500780651530829377030371611921181207362217397805303962112100190783763061909945889717878397740711340114311597934724670601992737526668932871436226135393872881664511222789565256059138002651403875484920711316522536260604255269532161594824301047729082877262812899724246757871448545439896
```

- step 2<br>
I tired finding the sqrt of N using isqrt and get the value of p.Then I calculate the Euler's totient using p*(p-1) and calulate the value of private key using pow(e,-1,phi). After that, we just decrypt the ciphertext using pow(c,d,n) and we get the flag.

<br>
<br>
<br>

## Lets Decrypt
**Flag:** `crypto{dupl1c4t3_s1gn4tur3_k3y_s3l3ct10n}`

Approach

- step 1<br>
We are given the script in the challenge. We need to change the server code such that r is returned as true as well as the calc_digest == og_digest.
we need to forge the value of N and e.Then we can encode `I am Mallory and I own Cryptohack.org`.To ensure calc_digest == og_digest we put e=1.

```
#!/usr/bin/env python3

import re
from Crypto.Hash import SHA256
from Crypto.Util.number import bytes_to_long, long_to_bytes
from utils import listener
from pkcs1 import emsa_pkcs1_v15
# from params import N, E, D

FLAG = "crypto{?????????????????????????????????}"

MSG = 'We are hyperreality and Jack and we own CryptoHack.org'
DIGEST = emsa_pkcs1_v15.encode(MSG.encode(), 256)
SIGNATURE = pow(bytes_to_long(DIGEST), D, N)


class Challenge():
    def __init__(self):
        self.before_input = "This server validates domain ownership with RSA signatures. Present your message and public key, and if the signature matches ours, you must own the domain.\n"

    def challenge(self, your_input):
        if not 'option' in your_input:
            return {"error": "You must send an option to this server"}

        elif your_input['option'] == 'get_signature':
            return {
                "N": hex(N),
                "e": hex(E),
                "signature": hex(SIGNATURE)
            }

        elif your_input['option'] == 'verify':
            msg = your_input['msg']
            n = int(your_input['N'], 16)
            e = int(your_input['e'], 16)

            digest = emsa_pkcs1_v15.encode(msg.encode(), 256)
            calculated_digest = pow(SIGNATURE, e, n)

            if bytes_to_long(digest) == calculated_digest:
                r = re.match(r'^I am Mallory.*own CryptoHack.org$', msg)
                if r:
                    return {"msg": f"Congratulations, here's a secret: {FLAG}"}
                else:
                    return {"msg": f"Ownership verified."}
            else:
                return {"error": "Invalid signature"}

        else:
            return {"error": "Invalid option"}


import builtins; builtins.Challenge = Challenge # hack to enable challenge to be run locally, see https://cryptohack.org/faq/#listener
listener.start_server(port=13391)
```

- step 2<br>
 a % (a-b) = a - (a-b) = b.
We encrypt the signature using the original parameters and give N as signature - message(in long form) and e = 1.
With this the the digests match as well as re.match returns True.

```{'msg': "Congratulations, here's a secret: crypto{dupl1c4t3_s1gn4tur3_k3y_s3l3ct10n}"}```





