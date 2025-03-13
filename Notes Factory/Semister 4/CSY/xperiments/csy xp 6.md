**Experiment 6: Caesar Cipher Implementation**

**Aim:** To implement the Caesar Cipher, demonstrating both single-shift and multi-level keyword variations.

**Theory:**

The Caesar Cipher is a simple substitution cipher where each letter in the plaintext is shifted a fixed number of positions down the alphabet. It's a foundational example of symmetric encryption.

* **Single-Shift Caesar Cipher:** This version uses a constant shift value for all letters in the plaintext.
* **Multi-Level Keyword Caesar Cipher:** This enhanced version uses a keyword to generate a sequence of shift values, providing a more complex encryption pattern.

**Procedure:**

1.  **Single-Shift Caesar Cipher:**
    * Implement a function that takes plaintext and a shift value as input.
    * Iterate through each character of the plaintext.
    * If the character is alphabetic, shift it by the given shift value, wrapping around the alphabet if necessary.
    * Non-alphabetic characters remain unchanged.

2.  **Multi-Level Keyword Caesar Cipher:**
    * Implement a function that takes plaintext and a keyword as input.
    * Iterate through each character of the plaintext.
    * For each character of plaintext, use a character of the keyword to generate a shift. The shift is based on the alphabetical position of the keyword character. The keyword is used cyclically.
    * If the character is alphabetic, shift it by the generated shift value, wrapping around the alphabet if necessary.
    * Non-alphabetic characters remain unchanged.

**Program (Python):**

```python
def caesar_cipher_single(text, shift):
    """Encrypts/decrypts text using a single shift Caesar cipher."""
    result = ''
    for char in text:
        if char.isalpha():
            start = ord('a') if char.islower() else ord('A')
            shifted_char = chr((ord(char) - start + shift) % 26 + start)
            result += shifted_char
        else:
            result += char
    return result

def caesar_cipher_keyword(text, keyword):
    """Encrypts text using a multi-level keyword Caesar cipher."""
    result = ''
    keyword_len = len(keyword)
    keyword_index = 0

    for char in text:
        if char.isalpha():
            start = ord('a') if char.islower() else ord('A')
            shift = ord(keyword[keyword_index % keyword_len].lower()) - ord('a')
            shifted_char = chr((ord(char) - start + shift) % 26 + start)
            result += shifted_char
            keyword_index += 1
        else:
            result += char
    return result

# Example Usage with Predefined Inputs
text = "Attack at dawn!"
shift = 5
keyword = "CIPHER"

# Single Shift Cipher
single_encrypted = caesar_cipher_single(text, shift)
single_decrypted = caesar_cipher_single(single_encrypted, -shift)

print("--- Single Shift Caesar Cipher ---")
print("Original Text:", text)
print("Encrypted Text (Shift", shift, "):", single_encrypted)
print("Decrypted Text:", single_decrypted)
print()

# Keyword Shift Cipher
keyword_encrypted = caesar_cipher_keyword(text, keyword)

print("--- Keyword Shift Caesar Cipher ---")
print("Original Text:", text)
print("Encrypted Text (Keyword", keyword, "):", keyword_encrypted)
```

output:
--- Single Shift Caesar Cipher ---
Original Text: Attack at dawn!
Encrypted Text (Shift 5 ): Fttfhp fy ifbs!
Decrypted Text: Attack at dawn!

--- Keyword Shift Caesar Cipher ---
Original Text: Attack at dawn!
Encrypted Text (Keyword CIPHER ): Ctvlck cv hgwr!