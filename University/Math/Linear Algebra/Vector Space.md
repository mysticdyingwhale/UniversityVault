#math 

# Vector Space 

Let $\mathbb{F}$ denote a field (EG. $\mathbb{F}= \mathbb{R}$  or $\mathbb{F} = \mathbb{C}$ ). 

A 2D real-number vector $(a,b)$ would be defined as $\mathbb{R}^2 = \{(a,b)\ | a \in \mathbb{R}, b  \in \mathbb{R} \}$ 

### Definition

A vector space $V$ over a field $\mathbb{F}$ is a set that is closed under "scalar multiplication" and closed under "addition". 

That is, $\alpha \in \mathbb{F}, x \in V$ then $\alpha \in V$ (closed under scalar multiplication), and $x,y \in V$ then $x+y \in V$ (closed under addition).

It is also required that:

- $\forall x,y \in V, x+y = y+x$  (commutativity of addition)
- $\forall x,y,z \in V, (x+y)+z = x+(y+z)$ (associativity of addition)
- $\exists 0 \in V$ such that $x+0 = x$  $\forall x \in V$ (additive)
- $\forall x \in V$, $\exists (-x) \in V$ such that $x + (-x) = 0$ (additive inverse)
- $\forall x \in V, 1 \cdot x = x$ such that 1 is the multiplicative identity in $F$. 
- $\forall a,b \in \mathbb{F}$ and $x \in V$, $(ab)x = a(bx)$ (associativity of scalar multiplication)
- $\forall a \in \mathbb{F}$ and $x,y \in V$, $a(x+y) = ax+ay$ (distributive)
- $\forall a,b \in \mathbb{F}$ and $x \in V$, $(a+b)x = ax+bx$ (distributive) 

>[!NOTE]
>This definition exposes the linearity of vector spaces

### Basic operations

Addition: 
$(a,b) + (c,d) = (a+c, b+d)$ 

Scalar multiplication:
$c \cdot (a,b) = (ac, bc)$ 

## Examples

$P_n = \{\text{polynomials of degree } \leq n\}$ 

EG: $v = 6x+5+2x^5$ , ($n=5$) 

$f,g \in P_n$, then $(f+g)(x) = f(x) + g(x)$ 
With addition defined this way, $P_n$ is a vector space. 

### Proofs

Theorem: A vector space $V$ over a field $\mathbb{F}$ has a unique additive identity.

Proof: Let $O, \tilde{O}$ be additive identities on $V$.  Then, $$\tilde{O} = \tilde{O} + O$$Since $O$ is an additive identity, order doesn't matter, so $\tilde{O} + O = O + \tilde{O}$ . Since $\tilde O$ is an additive identity $O + \tilde{O} = O$.  Thus, $\tilde O = O$. Therefore $V$ has a unique additive identity. 

Theorem: Every element in a vector space has a unique additive inverse.

Proof: Let $x \in V$ and suppose $\hat x, \tilde x \in V$ such that $x + \tilde x = 0, x + \hat x = 0$. Then, $\hat x = \hat x + 0 = \hat x + (x + \tilde x) = (\hat x + x) + \tilde x = 0 + \tilde x = \tilde x$. So $\hat x = \tilde x$ Thus, $V$ has a unique additive inverse. 

>[!NOTE]
>We will typically denote the additive inverse as $-x$, and when we write $x-y$ we mean $x + (-y)$.


**Theorem:** $0 \cdot v = 0$ for every $v \in V$. ($0$ is scalar, $v$ is a vector.)

**Proof:** $0v = (0+0)v = 0v+0v$. Adding additive inverse $-0v$ to both sides gives the result, ..., thus $0v = 0$. 

**Theorem:** $a0 = 0$ for every $a \in \mathbb{F}$ 

**Proof:** For $a \in \mathbb{F}$ we have $0 = a0 + (-a0)=a(0+0) + (-a0) = a0 + a0 + (-a0) = a0+(a0+(-a0)) = a0 + 0 = a0$ 

Adding additive inverse and using additive inverse property.

**Theorem:** $(-1)x = -x$ $\forall x \in V$ .

**Proof: **For every $x \in V$ we have:

$x + (-1)x=1 \cdot x + (-1) \cdot x = (1+(-1))x = 0x = 0$.

Thus $(-1)x$ is the unique additive inverse of $x$, denoted by $-x$. 


## Subspaces 

Definition: A subset $U$ of $V$ ($U \subseteq V$) is called a subspace of $V$ if $U$ is also a vector space (using the same rules of addition/multiplication as $V$). 

Theorem: A subset $U \subset V$ is a subspace if and only if $U$ satisfies the following:
1. $U$ is closed under addition ($x+y  \in U$ if $x,y \in U$) 
2. $U$ is closed under scalar multiplication ($\alpha \in \mathbb{F}, x \in U$, then $\alpha x \in U)$ 
3. $0 \in U$ 

Proof: ($\implies$) Suppose $U$ is a vector space. Conditions (1) and (2) hold immediately by definition. Suppose $U$ contains some additive identity $\tilde 0$. However, $0$ is unique in $V$ so $\tilde 0 = 0$. Thus (3) holds.

($\impliedby$) Conversely, suppose (1), (2) and (3) are satisfied by $U$. (3) ensures the additive identity of $V$ is in $U$, (1) and (2) ensure the addition/scalar multiplication make sense on $U$. 
If $x \in U$ then by (2), $(-1)x \in U$. This is the unique additive inverse such that $-x \in U$. Finally, commutativity and associativity are inherited from $V$. 

Definition: Suppose $u_1, u_2, ..., u_m$ are subsets of $V$. The sum of elements $u_1,u_2,...u_m$ denoted by $u_1+ u_2+...+u_m$ is the set of all possible sums of elements of $u_1, u_2,...,u_m$. That is,
$$u_1+ u_2+...u_m = \{u_1+u_2+...u_m | u_1 \in U_1, u_2 \in U_2, ... u_m \in U_m \}$$

For example: 
$u_1 = \{(x,0,0) \in \mathbb{R}^3 | x \in \mathbb{R}\}$ 
$u_2 = \{(0,y,0) \in \mathbb{R}^3 | y \in \mathbb{R}\}$ 
$u_1+ u_2 = \{(x,y,0) \in \mathbb{R}^3 | x,y \in \mathbb{R}\}$

Is $W = u_1+ u_2+...+u_m$ a subspace? 

Verify that (1)-(3) hold or find a counterexample:

#### (1)
Consider $x = u_1+ u_2+...+u_m$ and $y = \tilde u_1+ \tilde u_2+...+\tilde u_m$ where $x,y \in W$ and $u_k, \tilde u_k \in U_k$. 

Then, $x+y = (u_1+ u_2+...+u_m) +  \tilde u_1+ \tilde u_2+...+\tilde u_m$ 

$= (u_1 + \tilde u_1) + (u_2 + \tilde u_2) + ... + (u_m + \tilde u_m)$

Since $U_k$ is a subspace, $(u_k+ \tilde u_k) \in U_k$. So $x+y \in W$, thus (1) holds.

#### (2)

Let $\alpha \in F$ and $x = u_1+ u_2+...+u_m \in W$ such that $u_k \in U_k$. 

Then, 
$\alpha x = \alpha (u_1 + u_2+...+u_m)= \alpha u_1 + \alpha u_2 + ...  \alpha u_m$ . Since $U_k$ are subspaces we have $\alpha u_k \in U_k$ then $\alpha x \in W$. Thus (2) holds. 

#### (3)
Since each $u_k$ is a subspace, $0 \in U_k$ so that trivially $0 \in W$. Thus (3) holds and $W$ is a subspace. 


#### Proving $W$ is Smallest Subspace
Suppose $u_1,...,u_m$ are subspaces of $V$. Then $W = u_1+u_2+...+u_m$ is the smallest subspace of $V$ containing $u_1, u_2,...,u_m$ .

Suppose for the sake of contradiction that there exists a subspace $\tilde W$ containing $u_1, u_2, ..., u_m$ that is smaller than $W$. 

This means that $W$ cannot be contained within $\tilde W$ ($W \not \in \tilde W$). 

Since $U_k \subseteq \tilde W$ we have, if $u_k \in U_k$, then $x =  u_1+u_2+...+u_m$ is such that $x \in \tilde W$. 

Since $u_k \in \tilde W$ and $\tilde W$ is a subspace, but $x \in W$ so that $W \subseteq \tilde W$, but this is a contradiction. 

Therefore $W$ must be the smallest subspace of $V$ containing $u_1, ..., u_m$. 

#### Direct Sum

When every element of $V$ has a unique expression as $x = u_1+u_2 + ... + u_m$, $x \in V$. 

For $u_1 \in U_1, u_2 \in U_2, ..., u_m \in U_m$ we write: $$V = U_1 \oplus U_2 \oplus ... \oplus U_m$$ and we say $V$ is the direct sum of $u_1, ..., u_m$ 

Suppose $U_1, U_2, ..., U_m \subset V$ be subspaces of $V$. Then $U_1 + U_2 + ... + U_m = W$ is a direct sum if and only if $u_1 + u_2 + ...+u_m =0$ Then $u_j = 0$ for each $j = 1,2,...,m$

#### Basic Examples:

Given a 2D real-number vector space ($V = \mathbb{R}^2)$, some $U \subset V$ may be some line within $V$:

![[Pasted image 20240122115641.png|400]]
But this is not a vector space, so it is only a subset of $V$:
![[Pasted image 20240122120758.png|300]]

As it violates rules (2) and (3). 


