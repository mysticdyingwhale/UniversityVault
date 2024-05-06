# Singular Value Decomposition
#math 


### Properties of $T^*T$ 

**Claim:** Suppose $T \in \mathcal{L}(V,W)$, then

1. $T^*T$ is a positive operator on $V$
2. $\text{null}(T^*T) = \text{null }T$
3. $\text{range}(T^*T) = \text{range }T^*$
4. $\text{dim range }T = \text{dim range }T^* = \text{dim range}(T^*T)$

**Proof:** $\text{dim range }T = \text{dim null}((T^*))^\perp = \text{dim }W - \text{dim null}(T^*) = \text{dim range }T^*$

Since $\text{range }T^* = \text{range }T^*T \implies \text{dim range }T^* = \text{dim range}(T^*T)$

## Singular Values


**Definition:** Let $T \in \mathcal{L}(V,W)$. The singular values of $T$ are the non-negative square roots of eigenvalues of $T^*T$, listed in decreasing order. 

Each singular value is listed as many times as the dimension of the corresponding eigenspace of $T^*T$. 

**Example:** $T(z_1,z_2,z_3,z_4) = (0,3z_1,2z_2,-3z_4)$

We have $T^*T(z_1,z_2,z_3,z_4) = (9z_1,4z_2,0,9z_4)$

Then $\{e_1,...,e_n\}$ diagonalizes $T^*T \implies$ eigenvalues are $9,4,0$.

$\text{dim}(E_9)=2, \text{dim}(E_4)=1, \text{dim }(E_0)=1$


Then singular values are $\sigma_1 = 3, \sigma_2 = 3, \sigma_3 = 1, \sigma_4 = 0$

However $T$ only has eigenvalues $-3, 0$


#### Role of Singular Values


**Claim:** Suppose $T \in \mathcal{L}(V,W)$. Then:

1. $T$ is injective $\iff$ 0 is not a singular value of $T$
2. Number of positive singular values  = $\text{dim range }T$
3. $T$ is surjective $\iff$ $\text{dim }W =$ number of singular values

**Proof:** 

1. $T$ is injective $\iff$ $\text{null }T = \{0\}$
	$\iff \text{null }T^*T = \{0\}$
	$\iff$ 0 is not an eigenvalue of $T^*T$


2. Since $T^*T$ is positive, [[Spectral Theorem, Positive Operators|spectral theorem]] gives $\text{dim range}(T^*T) =$ number of positive eigenvalues of $T^*T$ (counting repetitions). Since $\text{dim range }T= \text{dim range}(T^*T)$ we get the result

3. $T$ is surjective $\iff$ $\text{dim range }T = \text{dim }W$
	$\iff \text{dim range }(T^*T) = \text{dim }W$
	$\iff \text{dim }W =$ number of positive singular values


**Claims:** Suppose $S \in \mathcal{L}(V,W)$. Then $S$ is an [[Isometries, Unitary Operators|isometry]] if and only if all singular values of $S$ are 1.


**Proof:** $S$ is an isometry $\iff S^*S = I$
	$\iff$ all eigenvalues of $S = I$
	$\iff$ all singular values of $S$ 

## Singular Value Decomposition

**Definition:** Suppose $T \in \mathcal{L}(V,W)$ and the positive singular values of $T$ are $\sigma_1,...,\sigma_m$. Then there exists orthonormal lists $e_1,..,e_m \in V, f_1,...,f_m \in W$ such that $$Tv = \sigma_1 \langle e_1,v \rangle f_1 + ... + \sigma_m \langle e_m, v \rangle f_m$$

**Proof:** Let $\sigma_1,...,\sigma_n$ be the singular values of $T$. Since $T^*T$ is positive, spectral theorem implies that there exists some orthonormal basis $\{e_1,...,e_n\}$ such that $$T^*Te_k = \sigma_k^2e_k.$$

Let $f_k= \frac {Te_k} {\sigma_k}$ . Then if $1 \leq j, k \leq m$ $$\langle f_j,f_k \rangle = \frac{1}{\sigma_j\sigma_k} \langle Te_j,Te_k \rangle = \begin{cases} 1 & j=k \\ 0 & j \neq k \end{cases}$$
Then $f_1,...,f_m$ is an orthonormal list in $W$. If $k > m$ then $\sigma_k = 0$ and $T^*Te_k = 0 \implies Te_k = 0$ Since $\text{null}(T^*T) = \text{null }T$


For $v \in V$ we have $$Tv = T(\langle v,e_1 \rangle e_1 +...+\langle v, e_n \rangle e_n )$$
$$= \sum_{k=1}^n \langle v,e_k \rangle Te_k = \sum_{k=1}^m \sigma_k \langle v,e_k\ \rangle e_k$$
If $\text{dim }W = \text{dim }V$ then $\mathcal{M}(T)$ is square. Choosing the basis $\{e_1,...,e_n,f_1,...,f_n\}$ for $V,W$ gives us a diagonal matrix. 


Note some of the differences between SVD and Spectral Theorem:

| Spectral Theorem                                                   | SVD                                                           |
| ------------------------------------------------------------------ | ------------------------------------------------------------- |
| Only self-adjoint ($\mathbb{R}$) or normal $(\mathbb C)$ operators | Arbitrary linear maps from one inner product space to another |
| 1 Orthonormal Basis                                                | 2 Orthonormal Lists, not necessarily the same                 |
| Different proofs based on $\mathbb F = \mathbb C, \mathbb R$       | Same proof regardless of field                                |
With an SVD of $T \in \mathcal L(V)$ we immediately get an SVD for $T^*$

### SVD of Adjoint

Suppose $T \in \mathcal{L}(V,W)$ and the positive singular values of $T$ are $\sigma_1,...,\sigma_m$. Let $e_1,...,e_m \in V$ and $f_1,...,f_m \in W$ be orthonormal lists such that for all $v \in V$ $$Tv = \sigma_1 \langle v,e_1 \rangle f_1 + ... + \sigma_m \langle v,e_m \rangle f_m.$$ Then, $$T^*w= \sigma_1 \langle w,f_1 \rangle e_1 + ... + \sigma_m \langle w, f_m \rangle e_m$$In other words, we swap the roles of $f_j$ and $e_j$. 

**Proof:** Let $v \in V, w \in W$. Then 
$$\langle Tv,w \rangle = \langle \sum_{k=1}^m \sigma_k \langle v,e_k \rangle f_k, w \rangle$$
$$ = \sum_{k=1}^m \sigma_k \langle v,e_k \rangle \langle f_k, w \rangle$$
$$ = \sum_{k=1}^m \langle v, \sigma_k  \overline{\langle f_k, w \rangle} e_k \rangle$$
$$ = \langle  v, \sum_{k=1}^m \sigma_k  \langle w, f_k \rangle e_k \rangle$$


### Matrices

**Theorem:** Any matrix $A \in \mathbb{R}^{m \times n}$ can be written $$A = U \Sigma V^*$$
Where $U \in \mathbb C ^{m \times n}, V \in \mathbb C^{n \times n}$ are unitary and $\Sigma \in \mathbb R^{m \times n}$ is a diagonal matrix where $\Sigma_{j,j} = \sigma_j$
 and $$\sigma_1 \geq \sigma_2\geq ... \geq \sigma_{min(m,n)}\geq 0$$
**Examples:** 

Let $T \in \mathcal{L}(\mathbb{F}^4, \mathbb{F}^3)$ be 

$$T(x_1,x_2,x_3,x_4) = (-5x_4,0,x_1,+x_2)$$

$$\mathcal{M}(T) = \begin{pmatrix} 0 & 0 & 0 & -5 \\ 0 & 0 & 0 & 0 \\ 1 & 1 & 0 & 0\end{pmatrix} = A$$
$$A^*A = \begin{pmatrix} 1 & 1 & 0 & 0 \\ 1 & 1 & 0 & 0  \\ 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 25 \end{pmatrix} $$
Here $(0,l_3), (25,l_4)$ are eigenpairs of $T^*T$. 

Any vector of the form $\alpha e_1 + \beta e_2$ is perpendicular to $e_3,e_4$. Now $$A^*A(\alpha e_1 + \beta e_2) = (\alpha + \beta)e_1 + (\alpha+\beta)e_2 = \lambda(\alpha e_1 + \beta e_2)$$
If $\alpha  = -\beta$ the we have an eigenvalue of $\lambda = 0$, if $\alpha = \beta$ then we have an eigenvalue of $\lambda = 2$.

So $$\text{dim E}(25, T^*T) = 1,\text{dim E}(2, T^*T) = 1, \text{dim E}(0, T^*T) = 2$$
We then have $\sigma_1 = 5, \sigma_2  = \sqrt 2$ as our only positive singular values. We now select an orthonormal list $g_1,g_2 \in \mathbb{F}^4$ and $f_1,f_2 \in \mathbb{F}^3$ such that $$Tv = 5 \langle v,g_1 \rangle f_1 + \sqrt2 \langle v,g_2 \rangle f_2$$
An orthonormal basis for $E(25,T^*T)$ is $e_4$ and for $E(2,T^*T)$ we have $f_2(e_1+e_2)$. Then taking $$g_1 = (0,0,0,1),g_2 = \frac 1 {\sqrt2}(1,1,0,0)$$ and $$f_1 = \frac{Tg_1}{5} = (-1,0,0), f_2 = \frac{Tg_2}{\sqrt 2} = (0,0,1)$$ gives us the SVD of $T$. 

In matrix form we have $A = U \Sigma V^*$ where

$$U = \begin{bmatrix} -1 & 0 \\ 0 & 0 \\ 0 & 1 \end{bmatrix}, V = \begin{bmatrix} 0 & \frac{1}{\sqrt2} \\ 0 &  \frac{1}{\sqrt2} \\ 0 & 0 \\ 1 & 0 \end{bmatrix}, \Sigma = \begin{pmatrix} 5 & 0 \\ 0 & \sqrt 2 \end{pmatrix}$$

This is sometimes called the economic SVD. 

Note that the columns of $U$ form the basis for $\text{range } A, and the columns of $V$ form the basis for $\text{range }A^*$. 

We can pad the bases of $\text{null }A, \text{null }A^*$ to get the full SVD.

### Bessel's Inequality

**Claim:**

**Proof:**
## Consequences and Geometry

**Claim:**

**Proof:**


### Norm

**Definition:**

**Examples:**


#### Unit Ball

**Definition:**

#### Ellipsoid

### Determinants

$\text{det }T =$ product of singular values. 

That is, $\text{det }T$ measures how you magnify the volume of the unit ball under $T$.

If any singular value is 0, then $T$ is not invertible so the area goes to zero.