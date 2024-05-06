# Upper Triangular Matrices
#math 

Since we're interested in operators $T \in \mathcal{L}(V)$, we'll often use the same basis for the image + preimage

$$\mathcal{M}(T) = \begin{pmatrix}A_{1,1} & A_{1,2} & ... & A_{1,n} \\ A_{2,1} & & & A_{2,n} \\ \vdots & & & \vdots \\ A_{n,1} & ... & ... & A_{n,n}\end{pmatrix}$$

where $Tv_k = A_{1,k}v_1 + ... + A_{n,k}v_n$. 

Note that these are square matrices $\mathcal{M}(T) \in \mathbb{F}^{n \times n}$ .


We want to know if there is a basis so that $\mathcal{M}(T)$ is as simple as possible.


**Definition:** The diagonal of a square matrix consists of entries on the line from the upper left corner to the lower right corner. ($A_{i,i} \space \forall \space i$) 

### Upper Triangular 

**Definition:** A square matrix is upper triangular if all its entries below the diagonal are zero $(A_{i,j} = 0, i >j)$

Example:

$\mathcal{M}(T) = \begin{pmatrix}2 & 1 & 0 \\ 0 & 5 & 3 \\ 0 & 0 & 8\end{pmatrix}$


#### Properties of UT matrices

**Theorem:** Suppose $T \in \mathcal{L}(V)$ and $v_1,...,v_n$ is a basis for $V$. Then the following are equivalent:

1. The matrix of $T$ with respect to $v_1,...,v_n$ is upper triangular
2. $\text{span }\{v_1,...,v_k\}$ is invariant under $T$ for each $k=1,...,n$
3. $Tv_k \in \text{span }\{v_1,...,v_k\}$ for all $k=1,...,n$

**Proof:** Cyclical proof (a implies b implies c implies a)

($a \implies b$) Suppose a holds and let $k \in \{1,...,n\}$. 

If $j \in \{1,...,n\}$ then $$Tv_j = A_{1,j}v_1 + A_{2,j}v_2+... + A_{j,j}v_j \in \text{span }\{v_1,...,v_j\}$$
since $\mathcal{M}(T)$ is upper triangular.

Since $\text{span }\{v_1,...,v_j\} \leq \text{span }\{v_1,...,v_k\}$ if $j \leq k$ then $Tv_j \in \text{span }\{v_1,...,v_k\}$ for all $k$. 

Then $\text{span }\{v_1,...,v_k\}$ is invariant under $T$.


($b \implies c$) Suppose b holds so that $\text{span }\{v_1,...,v_k\}$ is invariant under $T$ for all $k$. Then $Tv_k \in \text{span }\{v_1,...,v_k\}$, so b implies c


($c \implies a$) Suppose c holds. Then $Tv_k \in \text{span }\{v_1,...,v_k\}$ so that $Tv_k = A_{1,k}v_1 + ... + A_{k,k}v_k+0v_{k+1}+...+0v_n$ for all $k$ so that $\mathcal{M}(T)$ is upper triangular.


**Claim:** Suppose $T \in \mathcal{L}(V)$ and $V$ has a basis such that $T$ has an upper triangular matrix with diagonal entries $\lambda_1,...,\lambda_n$. Then $(T-\lambda_1 I)(T-\lambda_2 I)...(T - \lambda_n I) =0$

**Note:** $\prod_{k=1}^n(T - \lambda_kI)$ commutes (works in any order).

**Proof:** Let $v_1,...,v_n$ be a basis such that $\mathcal{M}(T)$ is an upper triangular matrix with diagonal entries $\lambda_1,...,\lambda_n$. Clearly $Tv_1 = \lambda_1v_1$ so that $$(T - \lambda_1I)v_1=0 \implies (T - \lambda_1I)...(T-\lambda_mI)v_1 = 0$$ for $m = 1,2,...,n$. 

Note that $$Tv_2 = A_{1,2}v_1+ \lambda_2v_2 \implies (T - \lambda_2 I)v_2 \in \text{span }\{v_1\}$$ then $(T - \lambda_1 I)(T -\lambda_2I)v_2 = 0 \implies (T - \lambda_1 I)...(T- \lambda_mI)v_2 = 0$ for all $m$.

Repeating this argument shows that $(T  - \lambda_1 I)...(T - \lambda_nI)v_k = 0$ for all $k$. This implies that $(T - \lambda_1 I)...(T - \lambda_nI)= 0$.

This polynomial should remind us of the [[Polynomials, Invariant Subspaces#Minimal Polynomial|Minimal Polynomial]]. Recall that the minimal poly are eigenvalues of $T$. And indeed, one can show:


#### UT diagonal entries are eigenvalues

**Claim:** Suppose $T \in \mathcal{L}(V)$ such that $\mathcal{M}(T)$ is an upper triangular matrix. Then the eigenvalues of $T$ are the entries of the diagonal. 

**Proof:** Suppose $T \in \mathcal{L}(V)$ has an UT matrix with diagonal $\lambda_1,...,\lambda_n$. 

Since $Tv_1 = \lambda_1v_1$ we see that $\lambda_1$ is an eigenvalue of $T$. 

Suppose $k \in \{2,...,n\}$. Then $(T - \lambda_kI)v_k \in \text{span }(v_1,...,v_{k-1})$. 

Thus $T  - \lambda_kI$ maps $\text{span }(v_1,...,v_k)$ into $\text{span }(v_1,...,v_{k-1})$ because


**Lemma:** Suppose $V$ is fin-dim and $T \in \mathcal{L}(V)$. 

Then $T$ has an upper triangular matrix with respect to some basis of $V$ if and only if the minimal polynomial of $T$ is $(z-\lambda_1)...(z-\lambda_m)$ for some $\lambda_1,...,\lambda_m \in \mathbb{F}$

**Proof:**



**Theorem:** Suppose $V$ is a fin-dim complex vector space and $T \in \mathcal{L}(V)$. Then $T$ has an upper-triangular matrix with respect to some basis of $V$. 

That is, if $\mathbb{F} = \mathbb{C}$, then every operator on $V$ has an upper triangular matrix.


## Diagonal Matrices

**Definition:** A diagonal matrix is a square matrix that is zero everywhere except on the diagonal ($A_{i,j} = 0$ if $i \neq j$) 

Since this is a special case of the Upper Triangular Matrix the eigenvalues of a diagonal matrix are the diagonal entries

**Definition:**  $T \in \mathcal{L}(V)$ is diagonizable if $\mathcal{M}(T)$ is diagonal for some basis of $V$.

Recall that $E(\lambda, T) = E_\lambda$ denotes the eigenspace of $T$ corresponding to the eigenvalue $\lambda$. IE: $$E(\lambda,T) = \text{null }(T - \lambda I)$$


**Claim:** Suppose $T \in \mathcal{L}(V)$ and $\lambda_1,...,\lambda_m$ are distinct eigenvalues of $T$. Then $$E(\lambda_1,T)+...+E(\lambda_m,T) = E$$ is a direct sum. Furthermore, if $\text{dim }V = n < \infty$ then: $$\text{dim }E(\lambda_1,T)+...+\text{dim }E(\lambda_m,T) \leq \text{dim }V$$

**Proof:**



**Theorem:** Let $T \in \mathcal{L}(V)$ and $\lambda_1,..., \lambda_m$ denote distinct eigenvalues of $T$. The following are equivalent:

1. $T$ is diagonizable
2. $V$ has a basis consisting of eigenvectors
3. $V = E(\lambda_1,T) \oplus ...\oplus E(\lambda_m,T)$ 
4. $\text{dim }V = \sum_{k=1}^m \text{dim }(E(\lambda_k,T))$

**Proof:**