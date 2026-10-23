# DSA — Unit VI: Hashing and Hash Functions (Exam-Oriented Notes)

> [!abstract] Scope of these notes
> These notes cover the **hashing portion actually explained in the attached Unit VI PDF**, mainly hash functions and the four methods: Truncation, Mid-Square, Folding, and Division. The PDF's syllabus lists collision-resolution techniques, but the slides only introduce collisions briefly; detailed collision-resolution notes are therefore not added here.

## 1. Introduction to Hashing

**Hashing** is a technique used to store and retrieve data efficiently by converting a key into an index or address in a hash table. The conversion is performed by a **hash function**.

### Working principle
1. **Input key:** Take the key of the data, such as a student roll number.
2. **Apply hash function:** Calculate an index from the key.
3. **Store or search:** Use the calculated index to insert, search, or retrieve the data in the hash table.

**Example:** A student's roll number `123` is passed to a hash function to calculate the location where the student's record should be stored.

> [!hint] Memory trick
> **Key → Hash function → Table index.** The hash function decides where to look.

> [!attention] AI
> A hash function gives the table address; it does not magically store the record by itself. The program still has to use that address.

## 2. Hash Functions

A **hash function** converts a given key into an index or address in a hash table. It helps store and retrieve data efficiently.

The PDF covers four hash-function methods:
- Truncation Method
- Mid-Square Method
- Folding Method
- Division Method

## 3. Truncation Method

The **Truncation Method** constructs a hash address by selecting specific digits or bits from a key and ignoring the remaining digits or bits.

### Steps
1. Take the key.
2. Select the required digits or bits.
3. Use the selected digits or bits as the hash address.

### Example
Given keys `123456`, `234567`, and `345678`, select the last three digits.

| Key | Selected digits | Hash address |
|---:|---:|---:|
| `123456` | `456` | `456` |
| `234567` | `567` | `567` |
| `345678` | `678` | `678` |

Therefore, `h(123456) = 456`. If only the last two digits are selected, `123456` maps to address `56`.

**Advantages**
- Simple and easy to implement.
- Requires very little computation.
- Suitable when the selected digits are distributed uniformly.

**Disadvantages**
- May produce many collisions if the selected digits repeat.
- Ignores much of the information contained in the key.
- Performance depends on the distribution of the selected digits.

> [!hint] Memory trick
> **Truncation = cut off the unwanted digits and keep the selected ones.**

> [!attention] AI
> If two keys have the same selected digits, they can get the same address. Ignoring digits is fast, but those ignored digits cannot help distinguish the keys.

## 4. Mid-Square Method

The **Mid-Square Method** squares the given key and selects the middle digits of the squared result to obtain the hash address.

### Steps
1. Take the key.
2. Calculate the square of the key.
3. Select the required number of middle digits.
4. Use the selected digits as the hash address.

### Example 1
Given key: `k = 1234`

**Step 1: Square the key**

`1234² = 1522756`

**Step 2: Select the middle three digits**

The middle three digits are `227`.

Therefore, `h(1234) = 227`.

### Example 2
Given key: `k = 123`

`123² = 15129`

Selecting the middle two digits gives `51`.

Therefore, `h(123) = 51`.

**Advantages**
- Uses information from different parts of the key.
- Can provide a better distribution than selecting only the last digits.
- Relatively easy to implement.

**Disadvantages**
- Requires multiplication to calculate the square.
- The distribution may still be uneven for some key sets.
- The number of middle digits must be chosen according to the table size.

> [!hint] Memory trick
> **Mid-Square = square the key, then take the middle digits.**

> [!attention] AI
> Do not take the first or last digits by mistake. The method specifically selects the middle digits of the squared value.

## 5. Folding Method

The **Folding Method** divides a key into equal-sized groups of digits, adds the groups together, and uses the result to generate the hash address. It is useful for long numeric keys.

### Steps
1. Divide the key into groups of equal length.
2. Add the groups.
3. If necessary, take the required number of digits or apply a table-size operation.
4. Use the result as the hash address.

### Example
Given key: `k = 123456789`

Assume the hash table has `100` locations, numbered `0` to `99`.

**Step 1: Divide into groups of three digits**

`123 | 456 | 789`

**Step 2: Add the groups**

`123 + 456 + 789 = 1368`

**Step 3: Select the last two digits**

`h(k) = 68`

Therefore, key `123456789` maps to hash-table index `68`.

**Advantages**
- Useful for long numeric keys.
- Uses different parts of the key.
- The steps are straightforward.

**Limitations**
- Different keys may produce the same sum and therefore the same address.
- Computation is low to moderate compared with simpler digit-selection methods.

> [!hint] Memory trick
> **Folding = split the key, add the groups, then select the address.**

> [!attention] AI
> Keep the groups in the correct order and add every group. Forgetting one group gives the wrong hash address.

## 6. Division Method

The **Division Method** calculates the remainder when a key is divided by the hash-table size. It is one of the simplest and most commonly used hash-function methods.

### Hash function

`h(k) = k mod m`

Where:
- `k` = key
- `m` = size of the hash table
- `mod` = remainder operator

### Example
Suppose the hash-table size is `m = 10`, with indices `0` to `9`. The keys are `23`, `45`, `12`, `34`, and `25`.

| Key | Calculation | Hash address |
|---:|---:|---:|
| `23` | `23 mod 10` | `3` |
| `45` | `45 mod 10` | `5` |
| `12` | `12 mod 10` | `2` |
| `34` | `34 mod 10` | `4` |
| `25` | `25 mod 10` | `5` |

**Collision example:** Keys `45` and `25` both map to index `5`. This is called a **collision** because two different keys produce the same hash address.

**Advantages**
- Very simple to implement.
- Requires only division and remainder operations.
- Efficient for many numeric keys.

**Disadvantages**
- A poor choice of table size can lead to more collisions.
- Keys with similar patterns may map to the same index.
- Collision resolution may be needed.

**Applications**
- Hash tables and dictionaries.
- Database indexing.
- Symbol tables in compilers.
- Fast data retrieval in software applications.

> [!hint] Memory trick
> **Division = divide by table size and keep the remainder.**

> [!attention] AI
> For `m = 10`, the answer is the last digit for non-negative decimal integers. But the general rule is the remainder—not “always take the last digit.”

## 7. Comparison of the Four Hash-Function Methods

| Feature | Truncation | Mid-Square | Folding | Division |
|---|---|---|---|---|
| Basic operation | Select specific digits | Square key and select middle digits | Divide key into groups and add | Calculate remainder |
| Computation | Very low | Moderate | Low to moderate | Very low |
| Uses different parts of key | Usually limited | Yes | Yes | Depends on key remainder |
| Main limitation | Selected digits may repeat | Requires squaring and digit selection | Different keys may produce the same sum | Poor table size may cause collisions |
| Best suited for | Keys with useful selected digits | Numeric keys | Long numeric keys | General numeric keys |

### Quick revision
- **Truncation:** Selects particular digits from a key.
- **Mid-Square:** Squares the key and extracts middle digits.
- **Folding:** Splits a key into groups and adds them.
- **Division:** Uses the remainder after dividing the key by the table size.

> [!hint] One-line recall
> **Select → Square → Split and Add → Remainder.** These correspond to Truncation, Mid-Square, Folding, and Division.

## 8. Collision — Brief Note

A **collision** occurs when two different keys produce the same hash address.

**Example:** With `h(k) = k mod 10`, both `45` and `25` map to index `5`.

The PDF briefly lists these common collision-resolution methods:
- Separate Chaining
- Linear Probing
- Quadratic Probing
- Double Hashing

> [!warning] PPT coverage limit
> **The attached PPT/PDF only introduces collision resolution at this point; it does not explain these techniques in detail.** The detailed working, examples, and analysis of collision-resolution methods are outside the portion covered by these slides, so they are not expanded into notes here.

## 9. Last-Minute Revision Checklist

- [ ] Define hashing and a hash function.
- [ ] Explain the three steps in the working principle of hashing.
- [ ] Solve one example each for Truncation, Mid-Square, Folding, and Division.
- [ ] Memorize the hash function `h(k) = k mod m`.
- [ ] Explain a collision using keys `45` and `25` with table size `10`.
- [ ] Compare all four hash-function methods.
- [ ] Remember that detailed collision-resolution techniques are not covered in the attached slides.

> [!hint] Exam strategy
> For a method-based question, write **definition → steps → worked example → advantages/disadvantages**. Show each calculation clearly so the examiner can follow how the address was obtained.
