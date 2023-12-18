#math 

A Relation is a shortcut for making a mathematical statement about two objects.

>[!note] Examples:
$4<5$
$x^2-y^2 = (x-y)(x+y)$
${1,2,3} \subseteq \mathbb{Z}$
A relation $R$ is a set of ordered pair of objects. We say that "$x \space R \space y$" if and only if $(x,y) \in R$


### Reflexive

A relation $R$ on a set $X$ is said to be reflexive it relates every element of $X$ to itself. 

>[!note] Examples:
> $=$
>| (divisibility)
> $\leq$

Irreflexive relations are relations that are not reflexive.


A relation is considered reflexive even if only one of the elements is reflexive
### Symmetric

A relation $R$ is considered symmetric if $aRb$ and $bRa$.

>[!note] Examples:
> $=$
> $\neq$

Antisymmetric relations are relations that are not symmetric

### Transitive

A relation $R$ on a set $X$ is considered transitive if, for all elements $a,b,c$ in $X$, $aRb$ and $bRc$ means that $aRc$

>[!note] Example:
> if $x<y$ and $y<z$, then $x<z$

Intransitive relations are relations that are not transitive.


## Equivalence Relations

Equivalence relations are relations that are Reflexive, Symmetric, and Transitive. For relations on a set, they are Reflexive, Symmetric, and Transitive for every element in the set. 


#### Congruence modulo n 

Let n be a positive integer. We say that integers x and y are congruent modulo n, and write 
$$x \equiv y \text{ (mod $n$)}$$
provided $n | (x-y)$

In other words, $x \equiv y$ (mod $n$) if and only if x and y differ by a multiple of n. 


### Equivalence Class


If $R$ is an equivalence relation on $A$ and $x \in A$, then the equivalence class of $x$, denoted $[x]_R$, is the set of all elements $A$ that are related to $x$.  i.e.  $[x]_R = \{y \in A | xRy \}$. if $R$ is clear from context, we leave it out. 


>[!note] Examples:
>if A is a set of people, and R is the "is a relative of" relation, then A % R is the set of families
>
>If A is the set of hash tables, and R is the "has the same entries as" relation, then A % R is the set of functions with a finite domain

