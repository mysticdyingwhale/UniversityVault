#math 

# Linear Combinations

A linear combination of a list $v_1, v_2, ..., v_m \in V$ of vectors is a vector of the form $$a_1v_1+a_2v_2+...+a_mv_m \in V$$
for $a_1,a_2,...,a_m \in \mathbb{F}$.


For example, from a linear combination of $\{1,x,x^2\}$, $$f(x) = a_0 \cdot 1 + a_1 \cdot x + a_2 \cdot x^2$$
where $a_0, a_1, a_2 \in \mathbb{F}$. That is any quadratic polynomial. We say $\{1,x,x^2\}$ "span". 
$P_2 = \{\text{set of all polys degree} \leq 2 \}$ 

The set of all linear combinations of $v_1, v_2, ..., v_m \in V$ is called the span of $v_1, v_2, ..., v_m$, and is denoted 

$$\text{span}(v_1, v_2, ..., v_m) = \{a_1v_1+a_2v_2+...+a_mv_m|a_1,a_2,...,a_m \in \mathbb{F}\}$$
sometimes also written as $\text{span}\{v_1,...,v_m\}$

Given any $U \subset V$ (not necessarily a subspace), we have $$\text{span}(U)= \text{the set of all linear combinations of elements of U}$$
>[!NOTE]
>$\text{span}(U) \subset V$


**Claim:** $\text{span}(U)$ is a subspace of $V$.

**Proof:** $\text{span}(U)$ is closed under addition and scalar multiplication by definition. For any $x \in U$, $0 = 0 \cdot x \in \text{span}(U)$ so that $0 \in \text{span}(U)$. Therefore $\text{span}(U)$ is a subspace of $V$.


#### Example

Let $e_1 = (1,0,0,...,0), e_2 = (0,1,0,...,0)$. Where $e_1,e_2$ have $n$ entries.

And $e_k$ is the vector containing a single non-zero element with value 1 at the $k$th position for $k=1,2,...,n$ and $e_k \in \mathbb{R}^n$. Consider $$\text{span}(e_1,e_2,...,e_n)$$
and let $x \in \mathbb{R}^n$, then $X = (x_1,x_2,...,x_n)$ where $x_k \in \mathbb{R}$.

Then, $X = x_1e_1 + x_2e_2 + x_3e_3+...+x_ne_n$ so that $x \in \text{span}(e_1,e_2,...,e_n)$ by definition. Then $e_1,e_2,...,e_n$ spans $\mathbb{R}^n$.


#### Finite Dimensional

Definition: A vector space $V$ is finite-dimensional if there exists a finite set of vectors $\{u_1,u_2,...,u_m\}$ that spans $V$ ($\text{span}(u_1,u_2,...u_m) = V$)

Otherwise, we say $V$ is infinite-dimensional.

For example:

$P_3 = \{ \text{set of all polys degree} \leq 3 \}$ is finite dimensional as $\text{span}(1,x,x^2,x^3)$ is $P_3$ 

Let $P$ be the space of all polynomials of any degree. Then $P$ is infinite-dimensional. 


$\text{span}(1,x,x^2,x^2-1) = P_2$. 

$x^2-1$ is redundant as it is a linear combination of $\{1,x,x^2\}$:

$x^2-1 = (-1) \cdot 1 + 0 \cdot x + 1 \cdot x^2$

## Linearly Independent

A list $v_1, v_2,...,v_m \in V$ is linearly independent if the **only choice** of $a_1,a_2,...a_m \in \mathbb{F}$ such that $a_1v_1+a_2v_2+...+a_mv_m = 0$ is $a_k = 0$  $\forall k$.  
(you can only obtain 0 in any linear combination by making all scalars 0)

we say $v_1,v_2,...v_m$ is linearly dependent if they are not linearly independent.

Example: 

Rearranging $x^2-1 = (-1) \cdot 1 + 0 \cdot x + 1 \cdot x^2$ such that: 

$x^2-1 = (-1) \cdot 1 + 0 \cdot x + 1 \cdot x^2 + (-1)\cdot (x^2-1) = 0$ 

then {$1,x,x^2,x^2-1\}$ is linearly dependent. 

However, $\{1,x,x^2\}$ is linearly independent. 

#### Linear Dependence Lemma

The Linear Dependence Lemma tells us that given a linear dependent set of vectors $V$, removing a dependent vector will not change the span of $V$. 

>[!Define]
> $U \backslash W  =\{v \in V| v \in U| v \not \in W\}$ ($U$ without elements from $W$ essentially)

Suppose $U = \{u_1,u_2,u_3,...,u_m\} \subset V$ is a linearly dependent list in $V$. Then there exists $j \in \{1,2,...,m\}$ such that $u_j \in U$ and:
- (a) $u_j \in \text{span}(U \backslash  \{u_j\})$  ($u_j$ is an element of the span of $U$ without $u_j$)
- (b) $\text{span}(U \backslash \{u_j\}) = \text{span} (U)$ (The span of $U$ excluding $u_j$ is the same as the span of $U$)

Proof: Since $U$ is linearly dependent there exists $a_1, a_2,...,a_m \in F$ such that $a_1u_1+a_2u_2+...+a_mu_m = 0$ and at least one $a_j \neq 0$. We can rewrite this as $$u_ja_j = -(a_1u_1+a_2u_2+...+u_{j-1}a_{j-1}+u_{j+1}a_{j+1}+...+a_mu_m)$$Then,
 $$u_j = -\frac{a_1}{a_j}u_1 - ... - \frac{a_{j-1}}{a_j}u_{j-1}- \frac{a_{j+1}}{a_j}u_{j+1} - ... - \frac{a_{m}}{a_j}u_{m}$$
That is, $u_j$ can be written as a linear combination of vectors $\{u_1,u_2,...,u_{j-1}, u_{j+1},...,u_m\}$, so $u_j \in \text{span}(U \backslash \{u_j\})$, proving (a). 


To prove (b) we must prove two sets $(A,B)$ are equal/the same by showing $A \subseteq B$ and $B \subseteq A$. 

It is straightforward to show $\text{span}\{U \backslash \{u_j\}\}$ is a subset of $\text{span}\{U\}$. This means that $\text{span}\{U \backslash \{u_j\}\} \subseteq \text{span}\{U\}$. 

We now show  $\text{span}\{U\} \subseteq \text{span}\{U \backslash \{u_j\}\}$. To that end, let $v \in \text{span}\{U\}$. Then there exists $b_1,b_2,...,b_m \in F$ such that $V = b_1u_1+b_2u_2+...+b_{j-1}u_{j-1}+b_ju_j+b_{j+1}u_{j+1}+...+b_mu_m$ . 

Substituting $u_j = -\frac{a_1}{a_j}u_1 - ... - \frac{a_{j-1}}{a_j}u_{j-1}- \frac{a_{j+1}}{a_j}u_{j+1} - ... - \frac{a_{m}}{a_j}u_{m}$ into this expression gives $V = (b_1-\frac{b_1a_1}{a_j}u_1+...+(b_{j-1}-\frac{b_{j-1}a_{j-1}}{a_j}u_{j-1})++(b_{j+1}-\frac{b_{j+1}a_{j+1}}{a_j}u_{j+1}) + ... +(b_m-\frac{b_ma_m}{a_j}u_m)$  
Then $v \in \text{span}\{U \backslash \{u_j\}\}$ by definition. This gives us $\text{span}\{U\} \subseteq \text{span}\{U \backslash \{u_j\}\}$. 

Finally, $\text{span}\{U\} = \text{span}\{U\backslash\{u_j\}\}$