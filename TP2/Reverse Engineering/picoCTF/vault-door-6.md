# vault-door-5

**Flag:** `picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_95be5dc}`

Approach

- step 1<br>
We have been the given the script of the flag characters encoded using XOR encoding with 0x55(85) and then subtracting.After XORing, the result is subtracted by myBytes[i].
After XORing and subtracting, the result should be equal to zero. If the result of ((passBytes[i] ^ 0x55) - myBytes[i]) is not zero,
it means the password character did not match the expected encoded value, and the method returns false.

```
import java.util.*;

class VaultDoor6 {
    public static void main(String args[]) {
        VaultDoor6 vaultDoor = new VaultDoor6();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Dr. Evil gave me a book called Applied Cryptography by Bruce Schneier,
    // and I learned this really cool encryption system. This will be the
    // strongest vault door in Dr. Evil's entire evil volcano compound for sure!
    // Well, I didn't exactly read the *whole* book, but I'm sure there's
    // nothing important in the last 750 pages.
    //
    // -Minion #3091
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x6c, 0x60, 0x37, 0x30, 0x60, 0x31, 0x36,
        };
        for (int i=0; i<32; i++) {
            if (((passBytes[i] ^ 0x55) - myBytes[i]) != 0) {
                return false;
            }
        }
        return true;
    }
}
```

- step 1<br>
The following script can be written to decode the characters of the flag.

```
public class DecodePassword {
    public static void main(String[] args) {
        byte[] myBytes = {
            0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x6c, 0x60, 0x37, 0x30, 0x60, 0x31, 0x36,
        };

        StringBuilder password = new StringBuilder();
        for (int i = 0; i < myBytes.length; i++) {

            char decodedChar = (char) (myBytes[i] ^ 0x55);
            password.append(decodedChar);
        }

        System.out.println("\n picoCTF{" + password.toString() + "}");
    }
}


```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/picoCTF/assets/door6.png)



What you learned through solving this challenge:
<br>
- I learnt about XOR encoding with 0x55.


Other incorrect methods you tried:
<br>
- none

References:
<br>
-[XOR](https://codedamn.com/news/java/what-is-xor-operator-in-java)
