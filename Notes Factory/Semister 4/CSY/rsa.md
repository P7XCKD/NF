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

***
```python
from sympy import mod_inverse

def gcd(a,b):
    while b>0:
        a,b = b,a%b
    return a

p=int(input("Enter 1st prime number : "))
q=int(input("Enter 2nd prime number : "))
M=int(input("Enter the message : "))
n=p*q
phi = (p-1)*(q-1)
e=2  # 1<e<phi
while e<phi:
    if gcd(e,phi)==1:
        break
    e+=1

d=mod_inverse(e,phi)

C = pow(M,e,n)

M_decrypted = pow(C,d,n)

print(f"Public key: (n={n}, e={e})")
print(f"Private key: (n={n}, d={d})")
print(f"Encrypted Message (Ciphertext): {C}")
print(f"Decrypted Message: {M_decrypted}")

```