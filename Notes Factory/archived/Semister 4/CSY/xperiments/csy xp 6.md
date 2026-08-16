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
/# Caesar Cipher Implementation
def encrypt(text, shift):
    result = ""

    for char in text:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            result += char

    return result

def decrypt(text, shift):
    return encrypt(text, 26 - shift)  # Reverse shift

# Example usage
plaintext = "HELLO"
shift = 3

encrypted_text = encrypt(plaintext, shift)
print("Encrypted:", encrypted_text)

decrypted_text = decrypt(encrypted_text, shift)
print("Decrypted:", decrypted_text)
  ```
output

Encrypted: KHOOR  
Decrypted: HELLO  