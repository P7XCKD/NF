```python
import random
import string

def caesar_cipher(text: str, shift: int) -> str:
    """
    Shifts each letter in the input text by a specified amount.
    
    - Works with both uppercase and lowercase letters.
    - Non-alphabetic characters remain unchanged.
    - Uses modular arithmetic to wrap around the alphabet.
    """
    result = ""
    for char in text:
        if char.isalpha():
            base = 65 if char.isupper() else 97
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            result += char
    return result

def rot13(text: str) -> str:
    """
    A specific implementation of the Caesar cipher with a fixed shift of 13.
    
    - Effectively reverses itself when applied twice.
    - Commonly used for simple text obfuscation.
    - Works for both uppercase and lowercase letters.
    """
    return caesar_cipher(text, 13)

def random_shift_cipher(text: str) -> tuple[str, int]:
    """
    Encrypts the text using a Caesar cipher with a randomly chosen shift value.
    
    - The shift value is randomly selected between 1 and 25.
    - Returns both the encrypted text and the shift used.
    """
    shift = random.randint(1, 25)
    return caesar_cipher(text, shift), shift

def keyword_cipher(text: str, keyword: str) -> str:
    """
    Implements a keyword-based substitution cipher.
    
    - Constructs a unique alphabet using the provided keyword.
    - Duplicates in the keyword are removed while preserving order.
    - The remaining letters of the alphabet are appended to form a complete mapping.
    - Works with both uppercase and lowercase text.
    """
    alphabet = string.ascii_lowercase  # Standard alphabet
    
    # Remove duplicates from keyword while preserving order
    seen = set()
    keyword_unique = "".join(ch for ch in keyword.lower() if not (ch in seen or seen.add(ch)))
    
    # Generate cipher alphabet
    remaining_letters = "".join(ch for ch in alphabet if ch not in keyword_unique)
    key = keyword_unique + remaining_letters  # Ensure 26 letters in total

    # Create translation table for both lowercase and uppercase
    table = str.maketrans(alphabet + alphabet.upper(), key + key.upper())

    return text.translate(table)

def atbash_cipher(text: str) -> str:
    """
    Implements the Atbash cipher, a simple monoalphabetic substitution cipher.
    
    - The alphabet is reversed (A ↔ Z, B ↔ Y, etc.).
    - Works with both uppercase and lowercase letters.
    - Non-alphabetic characters remain unchanged.
    """
    alphabet = string.ascii_lowercase
    reversed_alphabet = alphabet[::-1]
    table = str.maketrans(alphabet + alphabet.upper(), reversed_alphabet + reversed_alphabet.upper())
    return text.translate(table)

def atbash_caesar_cipher(text: str, shift: int) -> str:
    """
    Combines the Atbash cipher with the Caesar cipher.
    
    - First, applies the Atbash cipher (reversing the alphabet).
    - Then, applies a Caesar cipher shift to the reversed text.
    - The result is a double-encrypted message.
    """
    atbash_text = atbash_cipher(text)
    return caesar_cipher(atbash_text, shift)

def vigenere_cipher(text: str, key: str) -> str:
    """
    Implements the Vigenère cipher, a polyalphabetic substitution cipher.
    
    - Uses a repeating keyword to determine shifts for each letter.
    - Each letter is shifted by the corresponding letter in the key.
    - Works with both uppercase and lowercase letters.
    - Non-alphabetic characters remain unchanged.
    """
    key = key.lower()
    key_length = len(key)
    key_as_int = [ord(i) - 97 for i in key]
    text_as_int = [ord(i) - (65 if i.isupper() else 97) for i in text if i.isalpha()]
    ciphertext = ''
    index = 0
    for char in text:
        if char.isalpha():
            base = 65 if char.isupper() else 97
            value = (text_as_int[index] + key_as_int[index % key_length]) % 26
            ciphertext += chr(value + base)
            index += 1
        else:
            ciphertext += char
    return ciphertext