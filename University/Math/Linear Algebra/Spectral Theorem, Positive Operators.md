# Spectral Theorem
#math 


Recall that for any $T \in \mathcal{L}(V)$, if $\mathbb{F} = \mathbb{C}$ there exists an [[Orthonormality#Orthonormal Basis|orthonormal basis]] such that $\mathcal{M}(T)$ is [[UT, Diagonal Matrices#Upper Triangular|upper triangular]]. 

We say that $T$ is diagonizable if $\mathcal{M}(T)$ is diagonal for some basis of $V$, which occurs if and only if we have a basis consisting of eigenvectors.


Consider the polynomial $x^2+bx+c$, $b,c \in \mathbb{R}$. Completing the square gives $$x^2+bx+c = (x+\frac b2)^2+ (c-\frac {b^2}4) \geq c - \frac{b^2}4$$
If $b^2 < 4c$ then $$x^2+bx+c \geq c - \frac{b^2}4 > 0$$
So that $(x^2+bx+c)$ is an invertible real number. We can generalize:


**Lemma:** Suppose $T \in \mathcal{L}(V)$ is self-adjoint and $b,c \in \mathbb{R}$ such that $b^2 < 4c$. Then $T^2+bT+cI$ is an invertible operator.

**Proof:** Let $v \in V, v \neq 0$. Then $$\langle (T^2+bT+cI)v,v\rangle  = \langle T^2 v,v \rangle + b\langle Tv,v \rangle + c \langle v, v\rangle $$$$ = \langle Tv,Tv \rangle +   b\langle Tv,v \rangle + c ||v||^2 = ||Tv||^2 +  b\langle Tv,v \rangle + c ||v||^2 $$
By [[Inner Products#Cauchy-Schwarz Inequality|Cauchy Schwarz]],  $|b \langle Tv,v \rangle | = |b| \cdot |\langle Tv,v \rangle| \leq |b| \cdot ||Tv|| \cdot ||v||$

It follows:
	$$|b \langle Tv,v \rangle | \geq -|b \langle Tv,v \rangle | \geq |-b| \cdot ||Tv|| \cdot ||v||$$

And using the previous inequality we get $$\langle (T^2 +bT+cI)v,v \rangle \geq ||Tv||^2 - |b| \cdot ||Tv|| \cdot ||v|| + c||v||^2$$$$= (||Tv|| - \frac{|b|\cdot ||v||}{2})^2 + (c -\frac{b^2}{4})||v||^2 > 0$$
This means that $(T^2 +bT + cI)v \neq 0$, so $(T^2 +bT + cI)$ is injective, implying invertibility. 


**Lemma:** Suppose $T \in \mathcal{L}(V)$ is self-adjoint. The [[Polynomials, Invariant Subspaces#Minimal Polynomial|minimal polynomial]] of $T$ equals $(z - \lambda_1)...(z - \lambda_m)$ for all $\lambda_k \in \mathbb{R}$

**Proof:** Suppose $\mathbb{F} = \mathbb{C}$. The zeros of the minimal polynomial are eigenvalues of $T$. Since $T$ is self-adjoint,  all eigenvalues of $T$ are real.  

The Fundamental Theory of Algebra tells us that the poly is the desired form

Suppose $\mathbb{F} = \mathbb{R}$. By factorization of a poly over $\mathbb{R}$ we have $$p(z) = (z - \lambda_1)...(z - \lambda_m)(z^2+b_1z+c_1) ...z^2+b_nz+c_n) $$ for $\lambda_k, b_j,c_j  \in \mathbb{R}$ and $b_j^2< 4cj$ for all $j$. 

here either $m,n$ may be 0, indicating no terms of corresponding form in $p(z)$.

Now $$p(T) = (T-\lambda_1I)...(T - \lambda_mI)(T^2+b_1T+c_1I)...(T^2+b_nT+c_nI)=0.$$ Assuming $n>0$ we could multiply on the right by $(T^2 +b_nT + c_nI)^{-1}$ (which exists by previous lemma, $T^* = T$) to get $$(T-\lambda_1I)...(T - \lambda_mI)(T^2+b_1T+c_1I)...(T^2+b_{n-1}T+c_{n-1}I)=0$$
This is a polynomial of $T$ that is zero when degree is $\text{deg }(p(z))-2< \text{deg}(p)$ which contradicts our assumption that $p$ is the minimal polynomial. 

We must then have $n=0$, and so we would have $p(z)$ in the desired form.


## Real Spectral Theorem

**Claim:** Suppose $F = \mathbb{R}$ and $T \in \mathcal{L}(V)$. The following are equivalent:

- $T$ is self-adjoint
- $T$ has a diagonal matrix with some orthornomal basis of $V$
- $V$ has an orthonormal basis consisting of eigenvectors of $T$

**Proof:**



## Complex Spectral Theorem


**Claim:** Suppose $F = \mathbb{C}$ and $T \in \mathcal{L}(V)$. The following are equivalent:

- $T$ is normal
- $T$ has a diagonal matrix with some orthornomal basis of $V$
- $V$ has an orthonormal basis consisting of eigenvectors of $T$

**Proof:**


**Examples:**



## Positive Operators

**Definition:** $T \in \mathcal{L}(V)$ is positive if $T$ is self-adjoint and $\langle Tv,T \rangle > 0$ for all $v \in V$. 

If $\mathbb F = \mathbb C$ we don't require self-adjoint.


Positive operators have square roots. $S \in \mathcal{L}(V)$ is a square root of $T$ if $S^2 = T$.


The following are equivalent:

- $T$ is positive
- $T$ is self-adjoint + all eigenvalues of $T$ are $\geq$ 0
- With respect to some orthonormal basis of $V$ $\mathcal{M}(T)$ is diagonal with non-negative entries
- $T$ has a positive square root
- $T$ has a self-adjoint square root
- $T = R^*R$ for some $R \in \mathcal{L}(V)$ 

**Proof:** 

