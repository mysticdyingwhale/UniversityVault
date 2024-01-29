#math 

## Relations 

A relation $f \subseteq A \times B$ is called a function provided $(aRb_1) \in f$ and $(aRb_2) \in f$ imply $b_1 = b_2$. 

Note that $A$ is the domain, and $B$ is the codomain

### Domain & Image

dom $f = \{a \in A: \exists b, (a,b) \in f \}$

im $f = \{b \in B: \exists a, (a,b) \in f \}$

$f : A \rightarrow B$ means dom $f = A$, im $f \subseteq B$

Think of image as the range based on the domain.
## Proof

Given $f : A \rightarrow B$ :

To prove that $f$ is a function from a set $A$ to a set $B$:

- Prove $f$ is a function
	- $aRb_1 \in f$ , $aRb_2 \in f$ , $b_1 = b_2$
	- Prove that dom ($f$) = $A$
	- Prove that im ($f$) $\subseteq B$

## One-to-one, onto, and bijection

### One-to-one

A function is called one-to-one (injective) provided that for all $a,b \in A$, if $f(a) = f(b)$ then $a=b$. 

This is the same as one-to-one in Calculus, essentially each value of $x$ is mapped to its own unique value. 

A function can be proved/disproved to be one-to-one directly, by contrapositive, or contradiction. 

### Onto

A function is called onto (surjective) provided that for all $y \in B$, there exists $x \in A$ such that $f(x) = y$.

In other words, im($f$) = $B$. Essentially, every value in the image is associated with a value in the domain. 

To prove it, show that im($f$) $=B$. To disprove it, find values that are in $B$ that are not in the image of $f$. 

### Bijection

A bijective function is a function which is both onto and one-to-one.

To prove it just prove that it is one-to-one, and that it is onto.

## Inverse 

The inverse relation of a function $f : A \rightarrow B$, denoted by $f^{-1}$ is the relation $f^{-1}$ defined by $f^{-1} = \{(yRx) : (xRy) \in f \} \subseteq B \times A$ . 

Such that $f(x) = y$ if and only if $f^{-1}(y) =x$ . 

i.e. : $f^{-1} : B \rightarrow A$ if and only if it is a bijection. To prove a function has an inverse, prove it is a bijection.
## Composition

Given $f : A \rightarrow B$ and $g : B \rightarrow C$, the composition of the two functions, denoted by $g \circ f$ , is a function $g \circ f : A \rightarrow C$ . 

Same as composite functions you're used to, $g(f(a))$ essentially.

dom $f$ = dom $g \circ f = A$ 