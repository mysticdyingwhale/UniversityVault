#math 

### Definition

A set is a repetition-free, unordered collection of objects.

Examples: {1,2,3} = {3,1,2} = ... = {1,1,2,3}, $\mathbb{N}$, {A, 1, $\mathbb{R}$}  

Objects that belong to sets are called elements.

Membership in a set is denoted by $\in$ 

The notation |A| refers to the cardinality (size) of A. 
### List VS Set

|                       | List    | Set         |
| --------------------- | ------- | ----------- |
| Collection of Objects | ordered | unordered   |
| Repetition            | Allowed | Not Allowed |
| Notation              | (a,b,c) | {a,b,c}     |
| Number of objects     | Length  | Cardinality 

### Set notation


Listing the elements of the set:

- Appropriate for smaller sets.

#### Set Builder notation

- In the form {dummy variable : conditions}
- i.e $\{ x : x\in \mathbb{Z}, x \geq 0 \}$
- or in the form {dummy variable $\in$ set : conditions}
-  $\{ x\in \mathbb{Z} : x \geq 0 \}$


#### Special Sets

- $\mathbb{Z}, \mathbb{R}, \mathbb{Q}, \mathbb{N}$
- Empty set $\emptyset$


### Equal Sets

#### Definition:
Two sets are equal if they have exactly the same elements.
#### Proof Template:

- Suppose $x \in A$, ... , therefore $x \in B$
- Suppose $x \in B$, ... ,therefore $x \in A$

Therefore, A = B


### Subsets

#### Definition

B is a subset of A if each element in B is also in A, denoted by $B \subseteq A$ or $B \supseteq A$

#### Proof Template

- Suppose $x \in B$, ... , therefore $x \in A$
Therefore $B \subseteq A$

### Power Set

Suppose that A is a set. The power set of A is the set of all subsets of A, noted by $\mathcal{P}(A)$

Given A = {1,2,3}, the power set of A would be {$\emptyset$, {1}, {2}, {3}, {1,2}, {2,3}, {1,2,3}}


### Set Operations


#### Union and Intersection

Union of sets, noted by $\cup$, is the set of **all** elements in both sets.

Intersection of sets, noted by $\cap$, is the set of **only** the elements which are present in both sets.

#### Set Difference

Set difference, noted by $\Delta$ , is the elements which **only** appear in **one** set.

#### Set Subtraction

A-B consists of all elements that are in A but not B
#### Disjoint Sets

We say that two sets are disjoint provided their intersection is the empty set.

We say that a collection of sets is **pairwise** disjoint provided no one set is equal to another. 

#### Set counting

Given two sets A, B

|A| + |B| = |A $\cup$ B| + |A $\cup$ B|



### Set Quantifiers

- For all (every, each, any, all):
	- $\forall$ 
	- "Every natural number is an integer"
		- $\forall x \in \mathbb{N}, x \in \mathbb{Z}$
	- The universal quantifier

- There exists:
	- $\exists$ 
	- "There exists an integer that is both prime and even"
		- $\exists x \in \mathbb{Z},$ x is prime and even.
	- The existential quantifier

#### Negations 


- $\neg$ $(\exists x \in A$, assertions about $x$)  = $\forall x \in A, \neg$ (assertions about $x$)
- $\neg$ $(\forall x \in A$, assertions about $x$)  = $\exists x \in A, \neg$ (assertions about $x$)

#### Converse, Contrapositive, Inverse

The converse of a statement "If A then B" is "If B then A"

The contrapositive of the statement "If A then B" is "If not B then not A"

The inverse of the statement "If A then B" is "If not A then not B"
