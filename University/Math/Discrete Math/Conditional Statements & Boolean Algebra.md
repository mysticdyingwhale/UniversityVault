#math 

## IF-THEN

Suppose A and B are two statements, for example A: x=1, B: x>0

$A \implies B$
"A" Implies "B"

If-Then truth table (If A then B):

|        | Condition B | Condition A |          |
| ------ | ----------- | ----------- | -------- |
| Case 1 | True        | True        | Possible |
| Case 2 | True        | False       |    Not Possible      |
| Case 3 | False       | False       | Possible |
| Case 4 | False       | True        | Possible         |


"If A then B" can be rewritten as NOT(A) OR B.

### Writing If-Then Proofs

1. Rewrite statements as an if-then statement
	1. Restate the hypothesis of the result
	2. Invent suitable notation
	3. Assign letters to represent variables
2. Write the last statement of the proof by restating the conclusion of the result
3. Use Definitions
	1. Work forwards from the beginning of the proof
	2. Work backwards from the end of the proof
4. Link the two halves of your argument


#### Example


## AND

The statement "A and B" is only true if both A and B are true:

$$\text{If } x \text{ and } y \text{ are even integers, then } xy \text{ is divisible by } 4$$

|        | Condition A | Condition B |          |
| ------ | ----------- | ----------- | -------- |
| Case 1 | True        | True        | True |
| Case 2 | True        | False       |    False      |
| Case 3 | False       | False       | False |
| Case 4 | False       | True        | False         |


## OR

The statement "A or B" is  true if either A or B are true:

$$\text{If } x \text{ or } y \text{ are even integers, then } xy \text{ is even}$$

|        | Condition A | Condition B |          |
| ------ | ----------- | ----------- | -------- |
| Case 1 | True        | True        | True |
| Case 2 | True        | False       |    True      |
| Case 3 | False       | False       | False |
| Case 4 | False       | True        | True         |


## NOT

The statement "Not A" returns true if A is false:

## Contrapositives


A contrapositive statement example:

"If A then B" -> "If not B then not A"


## Vacuous Truth

Statements of the form "If A, then B" in which condition A are impossible are known as vacuous truths. 


### Important Properties

- Commutative - x AND y  = y AND x,  x OR y = y OR x
- Associative - (x AND y) AND z  = x AND (y AND z),  (x OR y) OR z  = x OR (y OR z)
- Identity - x AND TRUE  = x, x OR False  = x
- Double Negative - NOT(NOT x) = x
- Idempotency - x AND x = x, x OR x = x
- Distributive - x AND (y OR z) = (x AND y )OR (x AND z),  x OR (y AND z) = (x OR y )AND (x OR z)
	- x AND NOT x = FALSE, x OR NOT x = TRUE
- DeMorgan's Laws: NOT(x AND y) = (NOT x) OR (NOT y), NOT(x OR y) = (NOT x) AND (NOT y)

Tautology : always TRUE
Contradiction : always FALSE
Contingency : some TRUE, some FALSE