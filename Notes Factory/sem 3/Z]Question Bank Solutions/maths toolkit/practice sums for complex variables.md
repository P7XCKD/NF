# Q1. Prove that f(z) is analytic and find f'(z) in terms of z

**Given:**

$$  
f(z)=(x^3-3xy^2+2xy)+i(3x^2y-x^2+y^2-y^3)  
$$

## Step 1 — Separate the real and imaginary parts

The standard form is:

$$  
f(z)=u(x,y)+iv(x,y)  
$$

Comparing with the given function:

$$  
u=x^3-3xy^2+2xy  
$$

$$  
v=3x^2y-x^2+y^2-y^3  
$$

> [!hint] What are u and v?
> 
> -   u = the real part (before i).
>     
> -   v = the imaginary part (after i).
>     
> 
> **Trick:** Split the expression at +i.

## Step 2 — Write the Cauchy–Riemann equations

For analyticity, we check:
$$
\frac{\partial v}{\partial y}  
$$

$$

-\frac{\partial v}{\partial x}  
$$

We need four partial derivatives: uₓ, uᵧ, vₓ and vᵧ.

## Step 3 — Calculate the four partial derivatives

### A. Find uₓ

Given:

$$  
u=x^3-3xy^2+2xy  
$$

Differentiate with respect to x. Treat y as a constant.
$$
3x^2-3y^2+2y  
$$

Therefore:

$$  
u_x=3x^2-3y^2+2y  
$$

> [!hint] Why?
> 
> -   x³ becomes 3x².
>     
> -   -3xy² becomes -3y² because y is treated as a constant.
>     
> -   2xy becomes 2y.
>     

### B. Find uᵧ

Use the same expression:

$$  
u=x^3-3xy^2+2xy  
$$

Differentiate with respect to y. Treat x as a constant.

$$
0-6xy+2x  
$$

Therefore:

$$  
u_y=-6xy+2x  
$$

Why?

-   x³ becomes 0 because there is no y.
    
-   -3xy² becomes -6xy.
    
-   2xy becomes 2x.
    

### C. Find vₓ

Given:

$$  
v=3x^2y-x^2+y^2-y^3  
$$

Differentiate with respect to x.

$$
6xy-2x+0-0  
$$

Therefore:

$$  
v_x=6xy-2x  
$$

### D. Find vᵧ

Use:

$$  
v=3x^2y-x^2+y^2-y^3  
$$

Differentiate with respect to y.

$$
3x^2+0+2y-3y^2  
$$

Therefore:

$$  
v_y=3x^2+2y-3y^2  
$$

## Step 4 — Verify the Cauchy–Riemann equations

### First equation

Formula:

$$  
u_x=v_y  
$$

Substitute the values:

$$
3x^2+2y-3y^2  
$$

Both sides are equal. The first equation is satisfied.

### Second equation

Formula:

$$  
u_y=-v_x  
$$

Substitute the values:

$$  
-6xy+2x=-(6xy-2x)  
$$

Remove the brackets:

$$  
-6xy+2x=-6xy+2x  
$$

Both sides are equal. The second equation is satisfied.

> [!hint] Conclusion  
> Both Cauchy–Riemann equations hold everywhere. All the partial derivatives are polynomials and are continuous everywhere.
> 
> Therefore, the function is analytic everywhere.

**Conclusion:**

$$  
f(z)\text{ is analytic everywhere}  
$$

## Step 5 — Find f'(z) in terms of z

For an analytic function, use:

$$  
f'(z)=u_x+i,v_x  
$$

Substitute the derivatives calculated earlier:

$$  
f'(z)=(3x^2-3y^2+2y)+i(6xy-2x)  
$$

We must convert this expression into z.

### A. Start with the definition of z

$$  
z=x+iy  
$$

Square both sides:

$$  
z^2=(x+iy)^2  
$$

Expand:

$$  
z^2=x^2+2ixy+i^2y^2  
$$

Use the identity:

$$  
i^2=-1  
$$

Therefore:

$$  
z^2=x^2-y^2+2ixy  
$$

Multiply by 3:

$$  
3z^2=3x^2-3y^2+6ixy  
$$

### B. Find -2iz

Start with:

$$  
z=x+iy  
$$

Multiply both sides by -2i:

$$  
-2iz=-2i(x+iy)  
$$

Expand:

$$  
-2iz=-2ix-2i^2y  
$$

Since i² = -1:

$$  
-2iz=-2ix+2y  
$$

Rearrange:

$$  
-2iz=2y-2ix  
$$

### C. Add the two results

We have:

$$  
3z^2=3x^2-3y^2+6ixy  
$$

And:

$$  
-2iz=2y-2ix  
$$

Add them:
$$
3x^2-3y^2+6ixy+2y-2ix  
$$

Group the real and imaginary parts:

$$
(3x^2-3y^2+2y)+i(6xy-2x)  
$$

This matches the expression for f'(z) found earlier.

**Final answer:**

$$  
f'(z)=3z^2-2iz  
$$

## Final exam checklist

1.  Write f(z) = u + iv.
    
2.  Find uₓ, uᵧ, vₓ and vᵧ.
    
3.  Verify uₓ = vᵧ.
    
4.  Verify uᵧ = -vₓ.
    
5.  State that f(z) is analytic everywhere.
    
6.  Use f'(z) = uₓ + ivₓ.
    
7.  Convert the answer into terms of z.
    

> [!important] Exam tip  
> If the question says **“prove analytic”**, show both Cauchy–Riemann checks. If it also asks for f'(z), show the derivative formula and the conversion into z.