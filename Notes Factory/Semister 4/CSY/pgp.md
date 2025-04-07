```python
import pgpy

def generate_pgp_keypair(name="User", email="user@example.com"):
    key = pgpy.PGPKey.new(pgpy.constants.PubKeyAlgorithm.RSAEncryptOrSign, 2048)
    uid = pgpy.PGPUID.new(name, email=email)
    key.add_uid(
        uid,
        usage={pgpy.constants.KeyFlags.EncryptCommunications, pgpy.constants.KeyFlags.Sign},
        hashes=[pgpy.constants.HashAlgorithm.SHA256],
        ciphers=[pgpy.constants.SymmetricKeyAlgorithm.AES256],
        compression=[pgpy.constants.CompressionAlgorithm.ZLIB]
    )
    return key, key.pubkey

def encrypt_message(message, pubkey):
    return str(pubkey.encrypt(pgpy.PGPMessage.new(message)))

def decrypt_message(enc_message, privkey):
    msg = pgpy.PGPMessage.from_blob(enc_message)
    with privkey.unlock(""):
        return privkey.decrypt(msg).message

# Demo
private_key, public_key = generate_pgp_keypair()
original = "Hello, this is a secret!"
encrypted = encrypt_message(original, public_key)
print("Encrypted:\n", encrypted)
decrypted = decrypt_message(encrypted, private_key)
print("Decrypted:\n", decrypted)
```
output

Encrypted:
-----BEGIN PGP MESSAGE-----
Version: PGPy v0.5.4

hQGMA4Lh8jNxGUEiAQwAqUiGknREqQwK8XYT3mP4Evq6+3TkdUpbH2clRq4sYga4
dBuEoc0jJe0MRN6OiXEmkwevP88pEZXG9rhUavXmQmfG9IN3F6drcwB+LZHecCwO
...
=eA9s
-----END PGP MESSAGE-----

Decrypted:
Hello, this is a secret!