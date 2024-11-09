# vault-door-3

**Flag:** `picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}`

Approach

- step 1<br>
The code takes user input of flag and passes it to the function .Now it scrambles the string using the function:-
  - The first 8 characters of `password` go directly to `buffer[0]` to `buffer[7]`.
  - Characters in `password` from index 15 down to index 8 are placed into `buffer[8]` to `buffer[15]`.
  - Even positions from `buffer[16]` to `buffer[30]` are filled with characters from `password` at mirrored indices, calculated as `46 - i`.
  - Finally, `buffer[31]` to `buffer[17]` (odd positions) are set with characters directly from `password`.

<br>
<br>


```
import java.util.*;

class VaultDoor3 {
    public static void main(String args[]) {
        VaultDoor3 vaultDoor = new VaultDoor3();
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

    // Our security monitoring team has noticed some intrusions on some of the
    // less secure doors. Dr. Evil has asked me specifically to build a stronger
    // vault door to protect his Doomsday plans. I just *know* this door will
    // keep all of those nosy agents out of our business. Mwa ha!
    //
    // -Minion #2671
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        String s = new String(buffer);
        return s.equals("jU5t_a_sna_3lpm18gb41_u_4_mfr340");
    }
}
```

- step 2
Again check password method checks if the scrambles string matches with jU5t_a_sna_3lpm18gb41_u_4_mfr340.
We can write the following script to reveal the flag.


```
public class VaultDoor3 {
    public static void main(String[] args) {
       
        String target = "jU5t_a_sna_3lpm18gb41_u_4_mfr340";
        char[] password = new char[32];

        for (int i = 0; i < 8; i++) {
            password[i] = target.charAt(i);
        }
        for (int i = 8; i < 16; i++) {
            password[23 - i] = target.charAt(i);
        }
        for (int i = 16; i < 32; i += 2) {
            password[46 - i] = target.charAt(i);
        }
        for (int i = 31; i >= 17; i -= 2) {
            password[i] = target.charAt(i);
        }

        System.out.println("\nflag: picoCTF{"+new String(password)+"}");
    }
}

```



![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Reverse%20Engineering/picoCTF/assets/door3.png)



What you learned through solving this challenge:
<br>
- String class and reverse engineering scrambled string algorithm.


References
<br>
- none
