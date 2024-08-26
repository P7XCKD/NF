Certainly! Here is the demonstration of the circular queue operations formatted as a table:

| Operation               | Queue                   | Front | Rear |
|-------------------------|-------------------------|-------|------|
| **Initial State**       | `[ - , - , - , - , - ]` | -1    | -1   |
| **Insert 7**            | `[ 7 , - , - , - , - ]` | 0     | 0    |
| **Insert 6**            | `[ 7 , 6 , - , - , - ]` | 0     | 1    |
| **Insert 8**            | `[ 7 , 6 , 8 , - , - ]` | 0     | 2    |
| **Delete 7**            | `[ - , 6 , 8 , - , - ]` | 1     | 2    |
| **Insert 9**            | `[ - , 6 , 8 , 9 , - ]` | 1     | 3    |
| **Insert 14**           | `[ - , 6 , 8 , 9 , 14 ]`| 1     | 4    |
| **Delete 6**            | `[ - , - , 8 , 9 , 14 ]`| 2     | 4    |
| **Delete 8**            | `[ - , - , - , 9 , 14 ]`| 3     | 4    |
| **Insert 88**           | `[ - , - , - , 9 , 88 ]`| 3     | 0    |
| **Delete 9**            | `[ - , - , - , - , 88 ]`| 4     | 0    |
| **Insert 55**           | `[ 55 , - , - , - , 88 ]`| 4    | 1    |
| **Insert 65**           | `[ 55 , 65 , - , - , 88 ]`| 4    | 2    |
| **Delete 14**           | `[ 55 , 65 , - , - , - ]`| 0     | 2    |
| **Insert 78**           | `[ 55 , 65 , 78 , - , - ]`| 0    | 3    |
| **Insert 34**           | `[ 55 , 65 , 78 , 34 , - ]`| 0    | 4    |

This table captures the state of the queue and the positions of `front` and `rear` after each operation.