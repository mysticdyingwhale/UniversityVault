#math 
# Dimension
## Replacement Theorem

**Definition:** Suppose $U = \{u_1,...,u_m\} \subset V$ are linearly independent. Let $W = \{w_1,w_2,...,w_n\} \subset V$ with $\text{span}(W)= V$ . Then $m \leq n$. 

In other words, any spanning list is as long as any linearly independent list.

**Proof:** Since $\text{span}(W) = V$, the list $\{u_1,w_1,w_2,...,w_n\} = \{u_1\} \cup W$ must be linearly dependent. 

By the linear dependence lemma there exists a $w_j$ that can be removed without changing the span. 

That is, $\text{span}(\{u_1\} \cup W \backslash \{W_j\}) = V$ 

Now consider $\{u_1,u_2\} \cup \{W \backslash \{w_j\}\}$. 

This is again a linearly dependent list, so we can remove a vector from $\{u_1,u_2\} \cup \{W \backslash \{w_j\}\}$ without changing its span (by linear dependence lemma). 

However, the $u_j$'s are linearly independent so that the chosen vector to be removed is to be one of the $w_k$'s.

$U= \{u_1,...,u_m\}, W = \{w_1,...,w_n\}$.

For the sake of contradiction, suppose $m>n$, we can proceed until all vectors in $W$ are replaced and find that $\text{span}(u_1,...,u_n)=V$. 

This is a contradiction, as $u_{n+1},...,u_m\in V$ but cannot be in $\text{span}(u_1,u_2,...,u_n)$ by the linear dependence lemma.

Thus $m \leq n$.

## Basis

**Definition:** A basis for a vector space $V$ is a linearly independent subset $U \subset V$ such that $\text{span}(U) = V$. 

#### Examples
$\{1,x,x^2\}$ is a basis for $P_2$ (set of all polynomials with a degree less than or equal to 2). 

Any 2nd-degree polynomial can be formed by some combination of those 3.

$\{1,x,x^2-1\}$ is also a basis for $P_2$. 

$\{1,x^2\}$ is not a basis for $P_2$, as you can not obtain $x \in P_2$.  $\text{span}(\{1,x^2\}) \neq P_2$ 

$\{1,x,x^2,x^2-1\}$ is also not a basis of $P_2$, as it is a linearly dependent set, even if its span is $P_2$. 

#### When is a list a basis?

**Claim:** $U =\{u_1,...,u_n\}\subset V$ is a basis for $V$ if and only if every $v \in V$ can be written uniquely as $V = a_1u_1+a_2u_2+...+a_mu_m$ for $a_k \in F$.

**Proof:** $(\implies)$ Suppose $U$ is a basis and suppose $v\in V$ can be expressed as $V  = a_1u_1+...+a_mu_m=b_1u_1+...b_nu_n$ for some $a_k,b_k \in F$ where at least one such $a_j \neq b_j$.

Then, $0 = V-V = (a_1u_1+...+a_mu_m)-(b_1u_1+...b_nu_n) = (a_1-b_1)u_1+(a_2-b_2)u_2+...+(a_n-b_n)u_n$

Since $\{u_1,...,u_n\}$ are linearly independent we must have $a_k-b_k=0$ for each $k=1,...,n$. Thus $a_k=b_k$ for each $k$ and $v \in V$ has a unique expansion in terms of $U$.

$(\impliedby)$ Suppose $v \in V$ can be uniquely written as $V = a_1u_1+...+a_nu_n$, $a_k \in F$. 

If $V=0$, then $0=a_1u_1+...+a_nu_n$ where clearly, the one choice is $a_k=0$ for each $k=1,...,n$. 

Since this is unique we have $\{u_1,...,u_n\}$ are linearly independent. 

By definition, $\text{span}(U) =V$ as each $v \in V$ can be obtained by a linear combination of elements of $U$. Therefore $U$ is a basis for $V$. 

#### Spanning Lists

Recall that a spanning list may not be a basis because it is not linearly dependent. 

**Claim:** Every spanning list can be reduced to a basis for a vector space.

**Proof:** Let $U = \{u_1,...,u_n\} \subset V$ such that $\text{span}(U) = V$. Let $B  = \{u_1,...,u_n\}$.

Step 1: If $u_1 = 0$, remove $u_1$ from $B$ . 
Step $j$: If $u_j < \text{span}\{u_1,...,u_{j-1}\}$, remove $u_j$ from $B$.

**Corollary**: Every finite dimensional space has a basis. 

On the other hand, we may sometimes fail to have "enough stuff" to get a basis.

**Claim:** Every linearly independent list of vectors in a finite dimensional space can be extended to a basis. 

**Example:** $\{1,x^2\} \rightarrow \{1,x,x^2\}$ 

**Proof:** Suppose $u_1,...,u_n \in V$ are linearly independent. By previous corollary there exists $v_1,...,v_m \in V$ such that $\{v_1,...,v_m\}$ is a basis for $V$. 

Then, $\text{span}(u_1, ...,u_n,v_1,...,v_m) =V$

We can prove this set with the claim (Every spanning list can be reduced to a basis for a vector space) to get a basis containing $u_1,...,u_n$. (These don't get removed since they are linearly independent)

**Claim:** If $V$ has a finite spanning subset, then every basis has the same length (# of elements)


#### Dimension

**Definition:** The dimension of a finite dimensional vector space is the length of any basis of the vector space. We denote this as $\text{dim}(V)$

We have many intuitive properties (proofs in book):

1. If $U \subseteq V$ is a subspace then $\text{dim}(U) \leq \text{dim}(V)$ 
2. If $U \subset V$ is a **linearly independent** list with $\text{dim}(U)=\text{dim}(V)$, then $U$ is a basis for $V$.
3. Every **spanning** list $U \subset V$ with $\text{dim}(U) = \text{dim}(V)$, then $U$ is a basis. 

