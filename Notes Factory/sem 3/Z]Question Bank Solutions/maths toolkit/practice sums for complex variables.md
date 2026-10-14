

### **Q1. Prove that $f(z) = (x^3 - 3xy^2 + 2xy) + i(3x^2y - x^2 + y^2 - y^3)$ is analytic and find $f'(z)$ in terms of $z$.**

To prove the function is analytic, we must show that its real and imaginary parts satisfy the Cauchy-Riemann equations ($u_x = v_y$ and $u_y = -v_x$).

  

Let $f(z) = u + iv$:

  

-   $u = x^3 - 3xy^2 + 2xy$
    
      
    
      
    
-   $v = 3x^2y - x^2 + y^2 - y^3$
    
      
    
      
    

Differentiating with respect to $x$ and $y$:

  

-   $\frac{\partial u}{\partial x} = 3x^2 - 3y^2 + 2y$
    
      
    
      
    
-   $\frac{\partial u}{\partial y} = -6xy + 2x$
    
      
    
      
    
-   $\frac{\partial v}{\partial x} = 6xy - 2x$
    
      
    
      
    
-   $\frac{\partial v}{\partial y} = 3x^2 + 2y - 3y^2$
    
      
    
      
    

Comparing the partial derivatives:

  

$$\frac{\partial u}{\partial x} = \frac{\partial v}{\partial y} = 3x^2 - 3y^2 + 2y$$

$$\frac{\partial u}{\partial y} = -\frac{\partial v}{\partial x} = -6xy + 2x$$

Since the Cauchy-Riemann equations are satisfied and the partial derivatives are continuous, $f(z)$ is analytic.

  

**Finding $f'(z)$:**

Using $f'(z) = \frac{\partial u}{\partial x} + i\frac{\partial v}{\partial x}$:

  

$$f'(z) = (3x^2 - 3y^2 + 2y) + i(6xy - 2x)$$

  

Applying the Milne-Thomson method by substituting $x = z$ and $y = 0$:

  

$$f'(z) = 3z^2 - 3(0)^2 + 2(0) + i(6(z)(0) - 2(z))$$

  

$$f'(z) = 3z^2 - 2iz$$

  

### **Q2. Find an analytic function whose imaginary part is $v = e^{-x}(y \sin y + x \cos y)$.**

Given the imaginary part:

  

-   $v = y e^{-x} \sin y + x e^{-x} \cos y$
    
      
    
      
    

Calculate the partial derivatives of $v$:

  

-   $\frac{\partial v}{\partial x} = -y e^{-x} \sin y + e^{-x} \cos y - x e^{-x} \cos y = e^{-x}(\cos y - y \sin y - x \cos y)$
    
      
    
      
    
-   $\frac{\partial v}{\partial y} = e^{-x}(\sin y + y \cos y) - x e^{-x} \sin y = e^{-x}(\sin y + y \cos y - x \sin y)$
    
      
    
      
    

By the Cauchy-Riemann equations, we know $f'(z) = \frac{\partial v}{\partial y} + i\frac{\partial v}{\partial x}$:

  

$$f'(z) = e^{-x}(\sin y + y \cos y - x \sin y) + i[e^{-x}(\cos y - y \sin y - x \cos y)]$$

  

Applying the Milne-Thomson method ($x=z, y=0$):

  

$$f'(z) = e^{-z}(0 + 0 - 0) + i[e^{-z}(1 - 0 - z)]$$

$$f'(z) = i(1-z)e^{-z}$$

Integrating $f'(z)$ with respect to $z$:

  

$$f(z) = \int i(1-z)e^{-z} dz$$

$$f(z) = i \left( \int e^{-z} dz - \int z e^{-z} dz \right)$$

$$f(z) = i \left( -e^{-z} - [z(-e^{-z}) - \int -e^{-z} dz] \right)$$

$$f(z) = i \left( -e^{-z} + ze^{-z} - e^{-z} \right) + c$$

$$f(z) = ize^{-z} + C$$

  

### **Q3. If $f(z) = u + iv$ is analytic and $u - v = e^x(\cos y - \sin y)$, find $f(z)$ in terms of $z$.**

To solve this, we construct a new function. Since $f(z) = u + iv$, we have $if(z) = -v + iu$. Adding these together gives $(1+i)f(z) = (u-v) + i(u+v)$. Let $F(z) = (1+i)f(z) = U + iV$, where the real part is $U = u - v = e^x(\cos y - \sin y)$.

  

Calculate the partial derivatives of $U$:

  

-   $\frac{\partial U}{\partial x} = e^x(\cos y - \sin y)$
    
      
    
      
    
-   $\frac{\partial U}{\partial y} = e^x(-\sin y - \cos y)$
    
      
    
      
    

We can find $F'(z)$ using $F'(z) = \frac{\partial U}{\partial x} - i\frac{\partial U}{\partial y}$:

  

$$F'(z) = e^x(\cos y - \sin y) - i[e^x(-\sin y - \cos y)]$$

  

Using the Milne-Thomson method ($x=z, y=0$):

  

$$F'(z) = e^z(\cos 0 - \sin 0) - i[e^z(-\sin 0 - \cos 0)]$$

  

$$F'(z) = e^z(1) - i[e^z(-1)]$$

  

$$F'(z) = e^z + ie^z = e^z(1+i)$$

  

Substitute back $F'(z) = (1+i)f'(z)$:

  

$$(1+i)f'(z) = (1+i)e^z$$

$$f'(z) = e^z$$

  

Integrating $f'(z)$ with respect to $z$:

  

$$f(z) = \int e^z dz$$

  

$$f(z) = e^z + C$$

  
![image](.attachments/6bd623280f221299e508e13021f54bded2beacaf.png) 

### **Q4. Check whether $u = x + e^{xy} + y + e^{-xy}$ is Harmonic. If yes, find the corresponding Harmonic conjugates.**

For a function to be harmonic, it must satisfy Laplace's equation: $\frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2} = 0$.

  

Given $u = x + e^{xy} + y + e^{-xy}$:

  

First, find the second-order partial derivative with respect to $x$:

  

-   $\frac{\partial u}{\partial x} = 1 + ye^{xy} - ye^{-xy}$
    
      
    
      
    
-   $\frac{\partial^2 u}{\partial x^2} = y^2e^{xy} + y^2e^{-xy}$
    
      
    
      
    

Next, find the second-order partial derivative with respect to $y$:

  

-   $\frac{\partial u}{\partial y} = xe^{xy} + 1 - xe^{-xy}$
    
      
    
      
    
-   $\frac{\partial^2 u}{\partial y^2} = x^2e^{xy} + x^2e^{-xy}$
    
      
    
      
    

Now, check Laplace's equation:

  

$$\frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2} = (y^2e^{xy} + y^2e^{-xy}) + (x^2e^{xy} + x^2e^{-xy})$$

  

Since $(y^2e^{xy} + y^2e^{-xy}) + (x^2e^{xy} + x^2e^{-xy}) \neq 0$, the function fails to satisfy Laplace's equation.

  

Therefore, $u$ is **not a Harmonic function**, and consequently, it has no harmonic conjugate.