# ExpNo 8: Solve Cryptarithmetic Problem, a CSP (Constraint Satisfaction Problem) Using Python

**Name:** L Ganesh Kanna  
**Register Number:** 212225230072  
**Date:** 20-11-2026

## Aim:
To solve a Cryptarithmetic Problem, a CSP (Constraint Satisfaction Problem) using Python.

## Procedure:

### Input and Output

**Input:** This algorithm will take three words.

```text
      B A S E
      B A L L
    ----------
    G A M E S
```

**Output:** It will show which letter holds which number from 0–9.

For this case, the solution is:

```text
      B A S E          2 4 6 1
      B A L L          2 4 5 5
    ---------        ---------
    G A M E S          4 9 1 6
```

## Algorithm:

For this problem, we will define a node that contains a letter and its corresponding numerical value.

```text
isValid(nodeList, count, word1, word2, word3)

Input:
A list of nodes, the number of elements in the node list,
and three words.

Output:
True if the sum of the values of word1 and word2
is equal to the value of word3.

Begin
    m := 1

    For each letter i from right to left of word1:
        ch := word1[i]

        For all elements j in nodeList:
            If nodeList[j].letter = ch:
                break
        done

        val1 := val1 + (m * nodeList[j].value)
        m := m * 10
    done

    m := 1

    For each letter i from right to left of word2:
        ch := word2[i]

        For all elements j in nodeList:
            If nodeList[j].letter = ch:
                break
        done

        val2 := val2 + (m * nodeList[j].value)
        m := m * 10
    done

    m := 1

    For each letter i from right to left of word3:
        ch := word3[i]

        For all elements j in nodeList:
            If nodeList[j].letter = ch:
                break
        done

        val3 := val3 + (m * nodeList[j].value)
        m := m * 10
    done

    If val3 = (val1 + val2):
        return true

    return false
End
```

## Sample Input and Output:

```text
SEND = 9567
MORE = 1085
------------
MONEY = 10652
```

## Program:

```python
from itertools import permutations

def solve_cryptarithmetic():
    for perm in permutations(range(10), 8):
        S, E, N, D, M, O, R, Y = perm

        if S == 0 or M == 0:
            continue

        SEND = 1000 * S + 100 * E + 10 * N + D
        MORE = 1000 * M + 100 * O + 10 * R + E
        MONEY = 10000 * M + 1000 * O + 100 * N + 10 * E + Y

        if SEND + MORE == MONEY:
            return SEND, MORE, MONEY

    return None


solution = solve_cryptarithmetic()

if solution:
    SEND, MORE, MONEY = solution

    print(f'SEND = {SEND}')
    print(f'MORE = {MORE}')
    print(f'MONEY = {MONEY}')

else:
    print("No solution found.")
```

## Output:

```text
SEND = 9567
MORE = 1085
MONEY = 10652
```

## Result:

Thus, the Cryptarithmetic Problem was solved successfully using Python by applying the Constraint Satisfaction Problem (CSP) technique.
