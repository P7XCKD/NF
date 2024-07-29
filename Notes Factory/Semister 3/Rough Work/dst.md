
### Expression 1: \( a + b \times (c^d - e)^{(f + g \times h)} - i \)

| Step | Token | Stack            | Output         |
|------|-------|-------------------|----------------|
| 1    | a     |                   | a              |
| 2    | +     | +                 | a              |
| 3    | b     | +                 | a b            |
| 4    | *     | + *               | a b            |
| 5    | (     | + * (             | a b            |
| 6    | c     | + * (             | a b c          |
| 7    | ^     | + * ( ^           | a b c          |
| 8    | d     | + * ( ^           | a b c d        |
| 9    | -     | + * ( - ^         | a b c d ^      |
| 10   | e     | + * ( - ^         | a b c d ^ e    |
| 11   | )     | + *               | a b c d ^ e -  |
| 12   | ^     | + ^ *             | a b c d ^ e -  |
| 13   | (     | + ^ * (           | a b c d ^ e -  |
| 14   | f     | + ^ * (           | a b c d ^ e - f|
| 15   | +     | + ^ * ( +         | a b c d ^ e - f|
| 16   | g     | + ^ * ( +         | a b c d ^ e - f g|
| 17   | *     | + ^ * ( + *       | a b c d ^ e - f g|
| 18   | h     | + ^ * ( + *       | a b c d ^ e - f g h|
| 19   | )     | + ^ *             | a b c d ^ e - f g h * +|
| 20   | -     | -                 | a b c d ^ e - f g h * + ^ * +|
| 21   | i     | -                 | a b c d ^ e - f g h * + ^ * + i|

**Final Postfix Expression**: `a b c d ^ e - f g h * + ^ * + i -`

### Expression 2: \( (a + (b + c) / (d - e)) \)

| Step | Token | Stack         | Output    |
|------|-------|---------------|-----------|
| 1    | (     | (             |           |
| 2    | a     | (             | a         |
| 3    | +     | ( +           | a         |
| 4    | (     | ( + (         | a         |
| 5    | b     | ( + (         | a b       |
| 6    | +     | ( + ( +       | a b       |
| 7    | c     | ( + ( +       | a b c     |
| 8    | )     | ( +           | a b c +   |
| 9    | /     | ( + /         | a b c +   |
| 10   | (     | ( + / (       | a b c +   |
| 11   | d     | ( + / (       | a b c + d |
| 12   | -     | ( + / ( -     | a b c + d |
| 13   | e     | ( + / ( -     | a b c + d e|
| 14   | )     | ( + /         | a b c + d e -|
| 15   | )     | (             | a b c + d e - /|
| 16   | )     |               | a b c + d e - / +|

**Final Postfix Expression**: `a b c + d e - / +`

These tables show the tokens being processed, the state of the stack at each step, and the resulting postfix output.