# Experiment 6: Caesar Cipher Implementation  

## **Aim:**  
To implement the Caesar Cipher, demonstrating both single-shift, multi-level shift, and keyword cipher.  

---

## **Theory:**  

The **Caesar Cipher** is a classical **substitution cipher** where each letter in the plaintext is shifted by a fixed number of positions in the alphabet. It is one of the simplest and earliest encryption techniques, relying on a **symmetric key system**.  

### **Types of Caesar Cipher:**  

#### **1. Single-Shift Caesar Cipher**  
Each letter in the plaintext is shifted by a fixed number (**key**) to obtain the ciphertext.  

**Example:**  
- Key = **3**, Plaintext: **HELLO**, Ciphertext: **KHOOR**  

**Mathematical Representation:**  
For each letter **P** in plaintext, the ciphertext letter **C** is:  
\[
C = (P + K) \mod 26
\]
Where **K** is the shift value, and letters are mapped to numbers (A=0, B=1, ..., Z=25).  

---

#### **2. Multi-Level Shift Caesar Cipher**  
Instead of a single shift value, multiple shifts are applied at different positions in the text, making it more complex.  

**Example:**  
- Key sequence = [3, 1, 4], Plaintext: **HELLO**  
- Ciphertext: **KEMOS** (each letter is shifted according to the key pattern cyclically).  

---

#### **3. Keyword-Based Caesar Cipher**  
A **keyword** determines the shift dynamically based on the letter positions in the keyword.  

**Example:**  
- Keyword = **"KEY"**  
- Shift values are derived from letters (A=0, B=1, ..., K=10, E=4, Y=24)  
- Plaintext: **HELLO**, shifts as per **KEY**, results in **RIJVS**.  

---

## **Procedure**  

### **1. Implementing Single-Shift Caesar Cipher**  

```java
// Caesar Cipher Implementation
class CaesarCipher {
    // Encrypt function
    public static String encrypt(String text, int shift) {
        StringBuilder result = new StringBuilder();
        
        for (char character : text.toCharArray()) {
            if (Character.isLetter(character)) {
                char base = Character.isUpperCase(character) ? 'A' : 'a';
                result.append((char) ((character - base + shift) % 26 + base));
            } else {
                result.append(character);
            }
        }
        
        return result.toString();
    }

    // Decrypt function
    public static String decrypt(String text, int shift) {
        return encrypt(text, 26 - shift);  // Reverse shift
    }

    public static void main(String[] args) {
        String plaintext = "HELLO";
        int shift = 3;

        String encrypted = encrypt(plaintext, shift);
        System.out.println("Encrypted: " + encrypted);

        String decrypted = decrypt(encrypted, shift);
        System.out.println("Decrypted: " + decrypted);
    }
}
