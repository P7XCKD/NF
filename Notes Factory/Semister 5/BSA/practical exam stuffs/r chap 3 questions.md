### Q.4 Write an R program to demonstrate working with operators (arithmetic, logical, relational, and assignment operators).
```r
# ----------------------------------------------------------
# ARITHMETIC OPERATORS
# ----------------------------------------------------------

a <- 10
b <- 3

# Addition
add_result <- a + b      # Output: 13
# Subtraction
sub_result <- a - b      # Output: 7


# ----------------------------------------------------------
# RELATIONAL OPERATORS
# ----------------------------------------------------------

# Greater than
rel1 <- a > b            # Output: TRUE
# Equal to
rel2 <- a == b           # Output: FALSE


# ----------------------------------------------------------
# LOGICAL OPERATORS
# ----------------------------------------------------------

x <- TRUE
y <- FALSE

# Logical AND
log1 <- x & y            # Output: FALSE
# Logical OR
log2 <- x | y            # Output: TRUE


# ----------------------------------------------------------
# ASSIGNMENT OPERATORS
# ----------------------------------------------------------

# Left assignment
num1 <- 50               # Output: 50
# Right assignment
75 -> num2               # Output: 75


# Display all results
add_result; sub_result
rel1; rel2
log1; log2
num1; num2
```

In R, vectors are the most basic data structure, and they store elements of the same data type.
Here are the main types of vectors with simple explanations and examples:

---

1. **Numeric Vector**

Stores numeric values (integers or doubles).

num_vec <- c(10, 20, 30)
print(num_vec)
# Output: 10 20 30

---

2. **Integer Vector**

Created using the L suffix.

int_vec <- c(1L, 2L, 3L)
print(int_vec)
# Output: 1 2 3

---

3. **Character Vector**

Stores text strings.

char_vec <- c("apple", "banana", "mango")
print(char_vec)
# Output: "apple" "banana" "mango"

---

4. **Logical Vector**

Contains TRUE/FALSE values.

log_vec <- c(TRUE, FALSE, TRUE)
print(log_vec)
# Output: TRUE FALSE TRUE

---

5. **Complex Vector**

Stores complex numbers.

comp_vec <- c(2+3i, 4-1i)
print(comp_vec)
# Output: 2+3i 4-1i

---

6. **Raw Vector**

Stores raw bytes (uninterpreted data).

raw_vec <- charToRaw("ABC")
print(raw_vec)
# Output: 41 42 43

---

## Summary Table

| Vector Type | Example            |
|-------------|--------------------|
| Numeric     | c(1.2, 3.5, 4.8)    |
| Integer     | c(1L, 2L, 3L)       |
| Character   | c("a", "b", "c")    |
| Logical     | c(TRUE, FALSE)      |
| Complex     | c(5+2i, 3-1i)       |
| Raw         | charToRaw("Hi")     |

---

If you want, I can also explain vector operations, indexing, or mixed-type vectors (coercion).
































```