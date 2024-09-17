# Polynomials & Eigenvalues
#math 


Assume $P : \mathbb{C} \rightarrow \mathbb{C}$ is a polynomial with complex coefficients unless stated otherwise.


- If $p(z) = a_0+a_1z+...+a_mz^m=0$ for all $z$ then $a_0=a_1=...=a_m=0$
- If $\lambda$ is a root of $p \in P_m$ i.e. ($p(\lambda)=0$) then $p(z) = (z-\lambda)q(z)$ for some $q \in P_{m-1}$ 
- If $p \in P_m$ and $p \neq 0$ then $p$ has at most $m$ **distinct** roots
- If $p \in P_m$ then there exists a unique $c,\lambda_1,...,\lambda_m \in \mathbb{C}$ such that $$p(z) =c (z-\lambda_1)(z-\lambda_2)...(z-\lambda_m)$$
- If $p$ has real coefficients then any root $\lambda$ is either real or $\overline \lambda$ is also a root of $p$
	- Recall $\overline \lambda$ is the complex conjugate ($\lambda = a+bi, \overline \lambda = a-bi$) 
- If $p$ has real coefficients then there exists unique numbers $c,\lambda_1,...,\lambda_m \in \mathbb{R}$ and $(\alpha_k,\beta_k) \in \mathbb{R}^2$ for $k=1,...,m$ with $\alpha_k^2 < 4\beta_k$ for all $k$ and $$p(x)=c(x-\lambda_1)(x-\lambda_2)...(x-\lambda_m)(x^2+\alpha_1x+\beta_1)...(x^2+\alpha_mx+\beta_m)$$

## Fundamental Theorem of Algebra

**Definition:** If $p \in P(\mathbb{C})$ is a non-constant polynomial, then $p$ has a unique factorization (except for the order of the factors) of the form $$p(z) = c(z - \lambda_1)...(z-\lambda_m)$$
where  $c,\lambda_1,...,\lambda_m \in \mathbb{C}$

**Proof:** is long...


### Zeros of Polynomials

**Definition:** A number $\lambda \in \mathbb{F}$ is called a zero (or root) of a polynomial $p \in \mathcal{P}(\mathbb{F})$ if $$p(\lambda)=0$$

**Claim:** Suppose $m$ is a positive integer and $p \in \mathcal{P}(\mathbb{F})$ is a poly of degree $m$.  Suppose $\lambda \in \mathbb{F}$. Then $p(\lambda)=0$ iff there exists a poly $q \in \mathcal{P}(\mathbb{F})$ of degree $m-1$ such that $$p(z)= (z-\lambda)q(z)$$ for all $z \in \mathbb{F}$ 

## Operators and Invariant Subspaces 

#### Operator

**Definition:** A linear map from a vector space to itself is called an operator.

#### Invariant Subspace

**Definition:** Suppose $T \in \mathcal{L}(V)$. A subspace $U$ of $V$ is called invariant under $T$ if $Tu \in U$ for every $u \in U$.

Thus $U$ is invariant under $T$ if $T|_U$ is an operator on $U$, where an operator is a linear map from a vector space to itself. 

## Eigenvalues

**Definition:** Suppose $T \in \mathcal{L}(V)$. A number $\lambda \in \mathbb{F}$ is called an eigenvalue of $T$ if there exists $v \in V$ such that $v \neq 0$ and $Tv = \lambda v$. 

We call $v$ an eigenvector. 

Together, $(\lambda,v)$ is an eigenpair.

**Example:** Define $T \in \mathcal{L}(\mathbb{F}^3)$ by $$T(x,y,z) = (7x+3z,3x+6y+9z, -6y)$$
for $(x,y,z) \in \mathbb{F^3}$. Then $T(3,1,-1) = (18,6,-6) = 6(3,1,-1)$. Thus 6 is an eigenvalue of $T$. 


#### Conditions to be an eigenvalue

**Claim:** Suppose $V$ is finite-dimensional, $T \in \mathcal{L}(V)$ and $\lambda \in \mathbb{F}$. Then the following are equivalent:

1. $\lambda$ is an eigenvalue of $T$ 
2. $T - \lambda I$ is not injective
3. $T - \lambda I$ is not surjective
4. $T - \lambda I$ is not invertible


**Proof:** Conditions 1, 2 are equivalent because $Tv = \lambda v$ is equivalent to $(T-\lambda I)v = 0$. 

Conditions 2,3,4 are equivalent as Injectivity is equivalent to surjectivity and invertibility if dim are equal.  


The eigenvectors of $T$ associated with $\lambda$ form the null space $E_{\lambda} = \text{null }(T - \lambda I)$. We call this the eigenspace associated with $\lambda$.


**Theorem:** Let $T \in \mathcal{L}(V)$. Suppose $\lambda_1,..., \lambda_m$ are distinct eigenvalues of $T$ with corresponding eigenvectors $v_1,...,v_m$. Then the list of eigenvectors are linearly independent.

**Proof:** Suppose for the sake of contradiction that $v_1,...,v_m$ are linearly dependent. Let $k$ be the smallest index such that $v_k \in \text{span}\{v_1,...,v_{k-1}\}$. 

Then, $v_k = a_1v_1+ ...+a_{k-1}v_{k-1}$ for $a_i \in \mathbb{F}$ where at least one $a_i \neq 0$. 

Applying $T$ to both sides we get $\lambda v_k = Tv_k = T(a_1v_1+...+a_{k-1}v_{k-1}) = \lambda_1a_1v_1+...+\lambda_{k-1}a_{k-1}v_{k-1}$.

Multiplying the previous equality by $\lambda_k$ on both sides we get $$\lambda v_k = \lambda_k(a_1v_1+...+a_{k-1}v_{k-1})= \lambda_ka_1v_1+...+\lambda_ka_{k-1}v_{k-1}$$

Subtracting these two from each other gives $0 = a_1(\lambda_1-\lambda_k)v_1 + ... + a_{k-1}(\lambda_{k-1}-\lambda_k)v_{k-1}$. 

By our initial choice of $k$, $v_1,...,v_{k-1}$ are linearly independent such that $a_i(\lambda_i-\lambda_k)=0$ for all $i=1,...,k-1$ 

Then $a_i=0$ for all $i$ since $\lambda_i \neq \lambda_k$ (as they are distinct). 

This is a contradiction, and thus the list is linearly independent. 

**Corollary:** If $\text{dim }V = n$ and $T$ has $n$ distinct eigenvalues with associated eigenvectors $v_1,...,v_n$ then $\{v_1,...,v_n\}$ is a basis for $V$. 

**Corollary:** If $\text{dim }V = n$ then each $T \in \mathcal{L}(V)$ has at most $n$ eigenvalues.

>[!NOTE]
>Many $T \in \mathcal{L}(V)$ won't have $n$ distinct eigenvalues


#### Example

$Iv =v, Iv = \lambda v \implies \lambda = 1$

$E_1 = V$. Any basis for $V$ is a basis of eigenvectors of $I$. 


## Operator Polynomials

**Definition:** Let $T \in \mathcal{L}(V)$. Then $TT = T^2$ makes sense and $T^2 \in \mathcal{L}(V)$. More generally we define $$T^m = T \circ T \circ ... \circ T = TT...T$$(m times) and note that $T^m \in \mathcal{L}(V)$. Note also that $(T^m)^{-1} = (T^{-1})^m$ which can be written as $T^{-m}$ (assuming $T$ is invertible).

For any polynomial $P$ we define $P(T) \in \mathcal{L}(V)$ by $$P(T)= a_0 I + a_1 T+...+a_mT^m$$ Where $I$ is the identity operator.

While it is not always true that if $T,S \in \mathcal{L}(V)$ that $TS = ST$, it is always true that if $p,q$ are polynomial that: $$(pq)(T)= p(T)\circ q(T) = q(T) \circ p(T) = (qp)(T)$$


**Theorem:** Every operator on a fin-dim non-zero, complex vector space has an eigenvalue.

**Proof:** Let $v \in V$ such that $v \neq 0$. Then $\{v,Tv,...,T^nv\}$ is not linearly independent since $\text{dim }V = n$ and the list contains $n+1$ elements, so there exists $a_0,a_1,...,a_n \in \mathbb{F}$ such that  $$0= a_0v+a_1Tv+...+a_mT^nv$$ such that not all $a_j =0$. Note that $a_1,...,a_n$ cannot all be zero since otherwise $a_0v = 0$ and $v \neq 0$. 

By the fundamental theorem of algebra we have that $p(z) = a_0+a_1z+...+a_nz^n$ can be factored as $$p(z)= c(z-\lambda_1)(z-\lambda_2)...(z-\lambda_m)$$ For $c,\lambda_1,...,\lambda_m \in \mathbb{C}$. 

Therefore, $$0= a_0v+a_1Tv+...+a_nT^nv = (a_0I+a_1T+...+a_nT^n)v$$$$= c(T-\lambda_1 I)...(T- \lambda_mI)v$$
It follows that at least one of the terms $T - \lambda_i I$ must have $\text{null }(T - \lambda_i I) \neq \{0\}$. 

In other words, $T$ has an eigenvalue for $\mathbb{F} = \mathbb{C}$ and $\text{dim }V = n < \infty$. 


## Minimal Polynomial

We say that $p$ is a **monic** polynomial if the highest degree coefficient is $1$. 

Example: $(1)x^2+5x$, $(1)x^5 + 4x^3 +1$


**Theorem:** Let $V$ be fin-dim and $T \in \mathcal{L}(V)$. Then there is a unique monic polynomial $p \in P(\mathbb{F})$ of smallest degree such that  $p(T)=0$. Furthermore, $\text{deg }(p) \leq \text{dim }V$. 

**Proof:** (long but easy)

We call this the minimal polynomial. 

**Example:** Let $V = \mathbb{R}^2$ and let $T \in \mathcal{L}(\mathbb{R}^2)$ be such that $$\mathcal{M}(T) = \begin{pmatrix}1 & 0 \\0 & 3\end{pmatrix}$$
We seek $C_0,C_1,C_2$ such that $$p(z)= C_0+C_1z + z^2$$ and $p(T) =0$. We have two unknowns so we need two equations.

$Te_1 = e_1$, $T^2e_1 = e-1$ so that $$p(T)e_1 = C_0e_1+C_1e_1+e_1 = 0$$ $\implies C_0+C_1 = -1$

Similarly, $$Te_2 = 3e_2, T^2e_2 = T(3e_2) = 9e_2$$  $\implies C_0e_2+C_1(3e_2)+9e_2 = 0 \implies C_0+3C_1 = -9$.

We solve to get $C_0 = 3, C_1 = -4$

Then $p(T) = 3I - 4T+T^2 = 0$

### Properties

**Theorem:** Let $V$ be fin-dim and $T \in  \mathcal{L}(V)$. 

1. The zeros of the minimal polynomial of $T$ are the eigenvalues of $T$.
2. If $V$ is a complex vector space then the minimal polynomial has the form $$(z-\lambda_1)(z-\lambda_2)...(z-\lambda_m)$$ where $\lambda_1,...,\lambda_m$ are eigenvalues of $T$ (with possible repetitions)

**Proof:** Let $p$ be the minimal polynomial of $T$.

 (1) Suppose $\lambda \in \mathbb{F}$ such that $p(\lambda)=0$. Then $$p(z) = (z-\lambda)q(z)$$ where $q$ is a monic poly with coefficients $\in \mathbb{F}$.

Since $p(T) = 0$, $$0 = p(T) = (T - \lambda I)(q(T)v)$$
for all $v \in V$. Since $\text{deg }q < \text{deg }p$, there exists at least one $v \in V$ such that $q(T)v \neq 0$. 

We have then $\text{null }(T-\lambda I)\neq \{0\}$ so that $\lambda$ is an eigenvalue. 

Now let $\lambda \in \mathbb{F}$ be an eigenvalue of $T$.  Then $Tv = \lambda v$ for some $v \in V, v \neq 0$

Note that $T^kv = \lambda^k v$ for all $k = 1,2,...$ 

Then, $p(T)v = C_0v + C_1Tv+...+T^nv = (C_0+C_1\lambda + ...+\lambda^n)v = p(\lambda)v = 0$


Since $p$ is the minimal poly  $p(\lambda) = 0$, so $\lambda$ is a root of $p$

(2) Follows from (1) and the fundamental theorem of algebra.



**Theorem:** Let $V$ be fin-dim, $T \in \mathcal{L}(V)$, and $q \in P(\mathbb{F})$. Then $q(T)=0 \iff q$ is a polynomial multiple of the minimal poly of $T$.

**Proof:** ($\implies$) Suppose $q(T)=0$, and suppose that $p$ is the minimal polynomial of $T$ such that $p(T) =0$.  

We take some $s \in P(\mathbb{F})$ as and have $$p(T)s(T) = 0 \cdot s(T) = 0 = q(T)$$
as desired.
 
($\impliedby$) Suppose $q$ is a poly multiple of $p$. Then $q = ps$ for some $s \in P(\mathbb{F})$. We have $$q(T) = p(T)s(T) = 0 \cdot s(T) = 0$$ as desired.


