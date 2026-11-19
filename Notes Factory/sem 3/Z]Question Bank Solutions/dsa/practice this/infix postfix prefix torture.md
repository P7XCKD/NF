# Infix to Postfix and Prefix – Fully Worked Solutions

## Operator priority and rules

| Operator | Priority | Associativity |
|---|---:|---|
| `^` | 3 | Right to left |
| `*`, `/` | 2 | Left to right |
| `+`, `-` | 1 | Left to right |

**Infix to Postfix using a stack**
1. Operand: add directly to output.
2. `(`: push onto stack.
3. `)`: pop to output until `(`; discard the bracket.
4. Operator: pop higher-priority operators. For equal priority, pop first for left-associative operators (`+`, `-`, `*`, `/`). Do not pop equal-priority `^`.
5. At the end, pop all remaining operators.

> **Same-priority rule:** For left-associative operators (`+`, `-`, `*`, `/`), the operator already on the stack is popped first when another operator of equal priority arrives.
>
> **A rule made by cruel fate for the creator as well as users of postfix, who have remained single their whole life and will continue to remain so. I pray and hope that there never comes a time when you have to use it yourself, or I won't even wish this on my worst enemy (wait, I definitely would, and so should you, cause why not).**
>
> **Famous last words said by yours truly – Probz**
>
> *(May no one suffer the same fate.)*
>
> *(P.S. The guy is very much alive even at this moment. Don't you dare mourn.)*

## Infix to Prefix using a stack

1. Reverse the infix expression.
2. Swap `(` with `)` and `)` with `(`.
3. Convert the modified expression to postfix using a stack. For this reversed conversion, handle equal-priority operators in the opposite direction to the ordinary postfix scan.
4. Reverse the postfix result to obtain prefix.

---

# Easy

## Q1. `A+B*C`

### Postfix: scan left to right

| Scanned | Action | Stack (bottom → top) | Output |
|---|---|---|---|
| A | Operand → output | Empty | A |
| + | Push | + | A |
| B | Operand → output | + | AB |
| * | Higher priority than + → push | + * | AB |
| C | Operand → output | + * | ABC |
| End | Pop * then + | Empty | `ABC*+` |

**Postfix:** `ABC*+`

### Prefix: reverse, swap brackets, then use stack

Reverse: `C*B+A` (no brackets to swap).

| Scanned | Action | Stack | Output |
|---|---|---|---|
| C | Operand → output | Empty | C |
| * | Push | * | C |
| B | Operand → output | * | CB |
| + | Pop *; push + | + | CB* |
| A | Operand → output | + | CB*A |
| End | Pop + | Empty | `CB*A+` |

Reverse output: `CB*A+` → **Prefix: `+A*BC`**

## Q2. `12+5-6`

Treat `12` as one operand.

### Postfix: scan left to right

| Scanned | Action | Stack | Output |
|---|---|---|---|
| 12 | Operand → output | Empty | 12 |
| + | Push | + | 12 |
| 5 | Operand → output | + | 12 5 |
| - | Equal priority: pop +, then push - | - | 12 5 + |
| 6 | Operand → output | - | 12 5 + 6 |
| End | Pop - | Empty | `12 5 + 6 -` |

**Postfix:** `12 5 + 6 -`

### Prefix: reverse, then use stack

Reverse: `6-5+12`.

For this reversed scan, equal-priority operators are handled in the opposite direction so the original left-to-right grouping is preserved.

| Scanned | Action | Stack | Output |
|---|---|---|---|
| 6 | Operand → output | Empty | 6 |
| - | Push | - | 6 |
| 5 | Operand → output | - | 65 |
| + | Keep - below + for reversed conversion | - + | 65 |
| 12 | Operand → output | - + | 6512 |
| End | Pop + then - | Empty | `6512+-` |

Reverse output: `6512+-` → **Prefix: `-+12 5 6`**

---

# Medium

## Q3. `(A-B)*C+D/E`

### Postfix: scan left to right

| Scanned | Action | Stack | Output |
|---|---|---|---|
| ( | Push | ( | Empty |
| A | Operand → output | ( | A |
| - | Push | ( - | A |
| B | Operand → output | ( - | AB |
| ) | Pop -; discard ( | Empty | AB- |
| * | Push | * | AB- |
| C | Operand → output | * | AB-C |
| + | Pop *; push + | + | AB-C* |
| D | Operand → output | + | AB-C*D |
| / | Higher priority → push | + / | AB-C*D |
| E | Operand → output | + / | AB-C*DE |
| End | Pop / then + | Empty | `AB-C*DE/+` |

**Postfix:** `AB-C*DE/+`

### Prefix: reverse, swap brackets, then use stack

Reverse and swap: `E/D+C*(B-A)`.

| Scanned | Action | Stack | Output |
|---|---|---|---|
| E | Operand | Empty | E |
| / | Push | / | E |
| D | Operand | / | ED |
| + | Pop /; push + | + | ED/ |
| C | Operand | + | ED/C |
| * | Push | + * | ED/C |
| ( | Push | + * ( | ED/C |
| B | Operand | + * ( | ED/CB |
| - | Push | + * ( - | ED/CB |
| A | Operand | + * ( - | ED/CBA |
| ) | Pop -; discard ( | + * | ED/CBA- |
| End | Pop * then + | Empty | `ED/CBA-*+` |

Reverse output: `ED/CBA-*+` → **Prefix: `+*-ABC/DE`**

## Q4. `A*B+C/D-E`

### Postfix: scan left to right

| Scanned | Action | Stack | Output |
|---|---|---|---|
| A | Operand | Empty | A |
| * | Push | * | A |
| B | Operand | * | AB |
| + | Pop *; push + | + | AB* |
| C | Operand | + | AB*C |
| / | Higher priority → push | + / | AB*C |
| D | Operand | + / | AB*CD |
| - | Pop / and equal-priority +; push - | - | AB*CD/+ |
| E | Operand | - | AB*CD/+E |
| End | Pop - | Empty | `AB*CD/+E-` |

**Postfix:** `AB*CD/+E-`

### Prefix: reverse, then use stack

Reverse: `E-D/C+B*A`.

| Scanned | Action | Stack | Output |
|---|---|---|---|
| E | Operand | Empty | E |
| - | Push | - | E |
| D | Operand | - | ED |
| / | Push | - / | ED |
| C | Operand | - / | EDC |
| + | Pop /; keep - below + for reversed conversion | - + | EDC/ |
| B | Operand | - + | EDC/B |
| * | Push | - + * | EDC/B |
| A | Operand | - + * | EDC/BA |
| End | Pop *, +, - | Empty | `EDC/BA*+-` |

Reverse output: `EDC/BA*+-` → **Prefix: `-+*AB/CDE`**

---

# Hard

## Q5. `(A+B)*(C-D)/E+F`

### Postfix: scan left to right

| Scanned | Action | Stack | Output |
|---|---|---|---|
| ( | Push | ( | Empty |
| A | Operand | ( | A |
| + | Push | ( + | A |
| B | Operand | ( + | AB |
| ) | Pop +; discard ( | Empty | AB+ |
| * | Push | * | AB+ |
| ( | Push | * ( | AB+ |
| C | Operand | * ( | AB+C |
| - | Push | * ( - | AB+C |
| D | Operand | * ( - | AB+CD |
| ) | Pop -; discard ( | * | AB+CD- |
| / | Equal priority: pop *; push / | / | AB+CD-* |
| E | Operand | / | AB+CD-*E |
| + | Pop /; push + | + | AB+CD-*E/ |
| F | Operand | + | AB+CD-*E/F |
| End | Pop + | Empty | `AB+CD-*E/F+` |

**Postfix:** `AB+CD-*E/F+`

### Prefix: reverse, swap brackets, then use stack

Reverse and swap: `F+E/(D-C)*(B+A)`.

| Scanned | Action | Stack | Output |
|---|---|---|---|
| F | Operand | Empty | F |
| + | Push | + | F |
| E | Operand | + | FE |
| / | Push | + / | FE |
| ( | Push | + / ( | FE |
| D | Operand | + / ( | FED |
| - | Push | + / ( - | FED |
| C | Operand | + / ( - | FEDC |
| ) | Pop -; discard ( | + / | FEDC- |
| * | Keep / below * for reversed conversion | + / * | FEDC- |
| ( | Push | + / * ( | FEDC- |
| B | Operand | + / * ( | FEDC-B |
| + | Push | + / * ( + | FEDC-B |
| A | Operand | + / * ( + | FEDC-BA |
| ) | Pop +; discard ( | + / * | FEDC-BA+ |
| End | Pop *, /, + | Empty | `FEDC-BA+*/+` |

Reverse output: `FEDC-BA+*/+` → **Prefix: `+/*+AB-CDEF`**

## Q6. `(A-B)/(C+D)*E^F`

### Postfix: scan left to right

| Scanned | Action | Stack | Output |
|---|---|---|---|
| ( | Push | ( | Empty |
| A | Operand | ( | A |
| - | Push | ( - | A |
| B | Operand | ( - | AB |
| ) | Pop -; discard ( | Empty | AB- |
| / | Push | / | AB- |
| ( | Push | / ( | AB- |
| C | Operand | / ( | AB-C |
| + | Push | / ( + | AB-C |
| D | Operand | / ( + | AB-CD |
| ) | Pop +; discard ( | / | AB-CD+ |
| * | Equal priority: pop /; push * | * | AB-CD+/ |
| E | Operand | * | AB-CD+/E |
| ^ | Higher priority → push | * ^ | AB-CD+/E |
| F | Operand | * ^ | AB-CD+/EF |
| End | Pop ^ then * | Empty | `AB-CD+/EF^*` |

**Postfix:** `AB-CD+/EF^*`

### Prefix: reverse, swap brackets, then use stack

Reverse and swap: `F^E*(D+C)/(B-A)`.

| Scanned | Action | Stack | Output |
|---|---|---|---|
| F | Operand | Empty | F |
| ^ | Push | ^ | F |
| E | Operand | ^ | FE |
| * | Push; lower priority than ^ | ^ * | FE |
| ( | Push | ^ * ( | FE |
| D | Operand | ^ * ( | FED |
| + | Push | ^ * ( + | FED |
| C | Operand | ^ * ( + | FEDC |
| ) | Pop +; discard ( | ^ * | FEDC+ |
| / | Keep * below / for reversed conversion | ^ * / | FEDC+ |
| ( | Push | ^ * / ( | FEDC+ |
| B | Operand | ^ * / ( | FEDC+B |
| - | Push | ^ * / ( - | FEDC+B |
| A | Operand | ^ * / ( - | FEDC+BA |
| ) | Pop -; discard ( | ^ * / | FEDC+BA- |
| End | Pop /, *, ^ | Empty | `FEDC+BA-/*^` |

Reverse output: `FEDC+BA-/*^` → **Prefix: `*/-AB+CD^EF`**

---

# Final Answer Sheet

| Q | Difficulty | Infix | Postfix | Prefix |
|---|---|---|---|---|
| 1 | Easy | `A+B*C` | `ABC*+` | `+A*BC` |
| 2 | Easy | `12+5-6` | `12 5 + 6 -` | `-+12 5 6` |
| 3 | Medium | `(A-B)*C+D/E` | `AB-C*DE/+` | `+*-ABC/DE` |
| 4 | Medium | `A*B+C/D-E` | `AB*CD/+E-` | `-+*AB/CDE` |
| 5 | Hard | `(A+B)*(C-D)/E+F` | `AB+CD-*E/F+` | `+/*+AB-CDEF` |
| 6 | Hard | `(A-B)/(C+D)*E^F` | `AB-CD+/EF^*` | `*/-AB+CD^EF` |

## Exam reminders

- Operands go directly to output.
- Operators are stored temporarily in the stack.
- Parentheses control when operators are popped.
- For equal-priority left-associative operators (`+`, `-`, `*`, `/`), pop the operator already on the stack first in ordinary infix-to-postfix conversion.
- `^` is right-associative.
- For prefix, reverse the expression, swap brackets, convert using the adjusted equal-priority rule, then reverse the result.
- Treat a multi-digit number such as `12` as one operand.
- In the stack table, write the stack from bottom to top.

**Exam tip:** Show the stack and output after every scanned symbol. This makes your method clear and can earn working marks even if the final expression contains an error.
