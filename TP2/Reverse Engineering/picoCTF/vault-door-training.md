# vault door training

**Flag:** `picoCTF{w4rm1ng_Up_w1tH_jAv4_be8d9806f18}`

Approach

- step 1<br>
In this file the flag is being taken as user input and a checkPAssword method is being used.From the code we are given the flag in the string format of picoCTF and password.

```
import java.util.*;

class VaultDoorTraining {
    public static void main(String args[]) {
        VaultDoorTraining vaultDoor = new VaultDoorTraining();
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

    // The password is below. Is it safe to put the password in the source code?
    // What if somebody stole our source code? Then they would know what our
    // password is. Hmm... I will think of some ways to improve the security
    // on the other doors.
    //
    // -Minion #9567
    public boolean checkPassword(String password) {
        return password.equals("w4rm1ng_Up_w1tH_jAv4_be8d9806f18");
    }
}
```



![](https://github.com/adityachawla005/cryptonite_taskphase_Aditya/raw/main/TP2/Web%20Exploitation/assets/rob.png)



What you learned through solving this challenge:
<br>
- Basics of String methods and java methods and classes.


References
<br>
- none
