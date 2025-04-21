```python
import math
from sympy import mod_inverse

p = int(input("Enter p (1st prime no.): "))
q = int(input("Enter q (2nd prime no.): "))
M = int(input("Enter M message (Int Only): "))

n, phi = p*q, (p-1)*(q-1)
print(f"N: {n}\nPhi of N: {phi}")

e = next(i for i in range(2, phi) if math.gcd(i, phi) == 1)
d = mod_inverse(e, phi)

print(f"E: {e}")
print(f"Public Key: ({n}, {e})")
print(f"Private Key: ({n}, {d})")

C = pow(M, e, n)
DM = pow(C, d, n)

print(f"Cipher Text: {C}")
print(f"Decrypted Message: {DM}")

```