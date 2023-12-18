#math 

## Combinatorial Proofs


To prove something combinatorically:

- Given an assertion in the form LHS = RHS
- Ask "in how many ways"
- Show LHS is the correct answer
- Show RHS is the correct answer
- Thus, LHS = RHS


## Product Principle:

**The product principle (AND rule) states that:**
-   The number of ways in which both choice A and choice B can be made is the product of the number of options for A and the number of options for B.
-   Think of it as Logic Gates AND. 

$$n(A \space AND \space B) = n(A) \times n(B)$$
   

## Addition Principle:

**The Addition principle (OR rule) states that: 
-   The number of ways in which either choice A or choice B can be made is the sum of the number of options for A and the number of options for B


$$n(A \space OR \space B) = n(A) + n(B)$$

## Exclusion Principle
The exclusion principle says that to find the number of permutations of things which do not possess a certain property, we find the number of permutations of things which do and subtract it from the total number of permutations. 

## Separation and Grouping
If a group of items need to be kept together, we treat them as one object. This group may still have permutations, so that should be accounted for in the calculation

For Example, if we have the word SQUARE and we want to keep QU next to each other:
![[Pasted image 20211219155859.png|350]]
![[Pasted image 20211219155913.png|350]]

- There are 6 letters, but 5 'tiles' since QU are together. We find the number of permutations for these 5 'tiles': $5!$
- AND We find the number of permutations for our fused tile: $2!$
To be left with: $2! \times 5! = 240$ ways.

If objects have to be kept apart, we permute all the other objects and then count the permutations of the gaps.

For Example, if we have the word SQUARE, and we want to keep all vowels separate:
![[Pasted image 20211219155532.png|350]]
We would:
- **Permute** all the consonants: $3!$
- AND **Choose** 3 gaps out of the 4 available: $\begin{pmatrix} 4 \\ 3 \end{pmatrix}$
- AND **Permute** the vowels into the gaps: $3!$

To be left with: $3! \times 3! \times \begin{pmatrix} 4 \\ 3 \end{pmatrix} = 144$ ways.

## Combinations & Permutations
In Counting Principles, r is the number of things we select and n is the total number of things available.

![[Pasted image 20211219135705.png]]
### Combinations
Combinations are the number of ways something can occur without considering order. 

The Equation for finding the number of combinations is:
$$\begin{pmatrix} n \\ r \end{pmatrix} = \frac{n!}{r!(n-r)!}$$

The two main types of permutation are:
1.  **Repetition is Allowed**: such as coins in your pocket (5,5,5,10,10)
2.  **No Repetition**: such as lottery numbers (2,14,15,27,30,33)

### Repetition Allowed
The best way to explain this is with an example. 

If we have 5 flavours of icecream: **banana, chocolate, lemon, strawberry and vanilla**,  and we can have 3 scoops. {b,c,l,s,v}.

Here, $n = 5$ and $r = 3$.

If we think of each flavour as being in a box, we could say "move past the first box, then take 3 scoops, then move along 3 more boxes to the end" and we will have 3 scoops of chocolate.

![[Pasted image 20211219152148.png]]

We can then represent our selection possibilities as arrows and circles, so if we were to go for {c,c,c}:
![[Pasted image 20211219152320.png]]
Or if we went for {b,l,v}:
![[Pasted image 20211219152334.png]]

So now instead of worrying about different flavours, we only worry about how many ways we can arrange the arrows and circles. In this scenario, there are always 3 circles and 4 arrows. 

So, there are r + (n-1) positions, and we want to choose r of them to have circles.

From here we modify the Combination Formula to match this rule:
$$\begin{pmatrix} n \\ r \end{pmatrix} = \frac{(r+n-1)!}{r!(n-1)!}$$

### No Repetition 
For when there is **no repetition**, we use the number of combinations formula above.

## Permutations
Permutations are the number of ways something can occur considering order. Think of it as ordered combinations.

The Equation for finding the number of permutations is:
$$\begin{pmatrix} n\\r \end{pmatrix} = \frac{n!}{(n-r)!}$$

The two main types of permutation are:
1.  **Repetition is Allowed**: It could be "333"
2.  **No Repetition**: for example the first three people in a running race. You can't be first _and_ second.

### Repetition Allowed
For when repetition is allowed, we simply find: $n^r$. 

### No Repetition
For when there is no repetition:
- If we're finding the permutations for the entire set we do $n!$ 
- Otherwise we use the number of permutations formula.