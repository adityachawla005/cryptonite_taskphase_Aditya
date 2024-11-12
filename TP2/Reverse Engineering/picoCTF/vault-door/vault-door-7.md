# vault-door-7

**Flag:** `picoCTF{A_b1t_0f_b1t_sh1fTiNg_07990cd3b6}`

Approach

- step 1<br>
The program checks a password by converting the input string into an array of integers, where we get each integer from 4 bits and each bit is shifted with 24,16,8 and 0 positions and combined.
The passwordToIntArray method converts the 32-character hex string into an array of 8 integers. 
The checkPassword method compares the converted integers against predefined values. 

```
import java.util.*;
import javax.crypto.Cipher;
import javax.crypto.spec.SecretKeySpec;
import java.security.*;

class VaultDoor7 {
    public static void main(String args[]) {
        VaultDoor7 vaultDoor = new VaultDoor7();
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

    // Each character can be represented as a byte value using its
    // ASCII encoding. Each byte contains 8 bits, and an int contains
    // 32 bits, so we can "pack" 4 bytes into a single int. Here's an
    // example: if the hex string is "01ab", then those can be
    // represented as the bytes {0x30, 0x31, 0x61, 0x62}. When those
    // bytes are represented as binary, they are:
    //
    // 0x30: 00110000
    // 0x31: 00110001
    // 0x61: 01100001
    // 0x62: 01100010
    //
    // If we put those 4 binary numbers end to end, we end up with 32
    // bits that can be interpreted as an int.
    //
    // 00110000001100010110000101100010 -> 808542562
    //
    // Since 4 chars can be represented as 1 int, the 32 character password can
    // be represented as an array of 8 ints.
    //
    // - Minion #7816
    public int[] passwordToIntArray(String hex) {
        int[] x = new int[8];
        byte[] hexBytes = hex.getBytes();
        for (int i=0; i<8; i++) {
            x[i] = hexBytes[i*4]   << 24
                 | hexBytes[i*4+1] << 16
                 | hexBytes[i*4+2] << 8
                 | hexBytes[i*4+3];
        }
        return x;
    }

    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        int[] x = passwordToIntArray(password);
        return x[0] == 1096770097
            && x[1] == 1952395366
            && x[2] == 1600270708
            && x[3] == 1601398833
            && x[4] == 1716808014
            && x[5] == 1734291511
            && x[6] == 960049251
            && x[7] == 1681089078;
    }
}

```

- step 2<br>
The following script can be written to decode the characters of the flag.

```
import java.util.*;

class Solution {

    public static void main(String[] args) {
        int[] correctPasswordInts = {
            1096770097, 1952395366, 1600270708, 1601398833, 
            1716808014, 1734291511, 960049251, 1681089078
        };
        
        String password = reconstructPassword(correctPasswordInts);
        
        System.out.println("Access granted.");
        System.out.println("\nFlag: picoCTF{" + password + "}");
    }

    public static String reconstructPassword(int[] correctPasswordInts) {
        StringBuilder password = new StringBuilder();
        
        for (int i = 0; i < correctPasswordInts.length; i++) {
            int value = correctPasswordInts[i];
            
            for (int j = 0; j < 4; j++) {
                byte byteValue = (byte) (value >> (24 - 8 * j) & 0xFF);
                password.append((char) byteValue);
            }
        }
        
        return password.toString();
    }
}

```


![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/picoCTF/assets/door7.png)



What you learned through solving this challenge:
<br>
- I learnt about bit shifting using << operator.


Other incorrect methods you tried:
<br>
- none

References:
<br>
- none
