# Invertibility
#math 

**Definition:** Let $T \in \mathcal{L}(V,W)$. We say that $T$ is invertible if there exists an $S \in \mathcal{L}(V,W)$ such that $$S(T(v))= v$$ for all $v \in V$, and $$S(T(w))=w$$ for all $w \in W$. 

I.E,  $ST = I$ on $V$, $TS = I$ on $W$. We call $S$ the **inverse** of $T$, $I$ is the identity operator. 

#### Unique Inverse
**Claim:** The inverse is unique.

**Proof:** Let $S_1 , S_2 \in \mathcal{L}(W,V)$ be inverses of $T$. Then, $$S_1 = S_1 I = S_1 (TS_2) = (S_1T)S_2 = IS_2 = S_2$$
Thus, $S_1 = S_2$.

>[!NOTE] 
>We typically write $T^{-1}$ to note the inverse of $T$. 

#### Invertible iff bijective

**Claim:** A linear map is invertible if and only if it is injective (one-to-one) and surjective (onto).

**Proof:** ($\implies$) Let $T \in \mathcal{L}(V,W)$ be invertible. 

**Injectivity:** Let $u,v \in V$ such that $Tu = Tv$. 

$$u  = I(u) = T^{-1}(T(u)) = T^{-1}(T(v))=I(v)=v$$

Therefore, $T$ is one-to-one.

**Surjectivity:** Let $w \in W$. Then $w = I(w) = T(T^{-1}(w))$ so that $w \in \text{range }T$. 

Since $T^{-1}(w) \in V$ such that $T(T^{-1}(w))=w$. Therefore $\text{range }T = W$ and $T$ is onto. 


$(\impliedby)$ Let $T \in \mathcal{L}(V,W)$ be bijective. For $T$ to be invertible, it must satisfy the inverse property and be a linear.

**Invertible:** For each $w \in W$, define $S(w)$ to be the unique element such that $T(S(W))=w$, as $T$ is bijective. This implies that $T \circ S= I$ on $W$. 

To prove that $S \circ T = I$ on $V$, let $v \in V$. Then $$T((S \circ T)v) = (T \circ S)(Tv)= I (Tv) = Tv.$$
This implies that $(S \circ T)v = v$ since $T$ is injective. Thus, $S \circ T = I$ on $V$.

**Linear Map:** We must show that $S$ is a linear map.

**Additivity:** Suppose $w_1,w_2 \in W$. Then $$T(S(w_1)+S(w_2))=T(S(w_1)) + T(S(w_2)) = w_1+w_2.$$ Thus, $S(w_1)+S(w_2)$ is the unique element of $V$ that $T$ maps to $w_1+w_2$. By the definition of $S$, this implies that $S(w_1+w_2) = S(w_1)+S(w_2)$. Hence, $S$ satisfies the additive property.

**Homogeneity:** Given $w \in W, \lambda \in \mathbb{F}$, $$T(\lambda S(w)) = \lambda T(S(w)) = \lambda w.$$ Thus, $\lambda S(w)$ is the unique element of $V$ that $T$ maps to $\lambda w$. By definition of $S$, this would imply that $S(\lambda w) = \lambda S(w)$. Hence, $S$ is a linear map.


### Isomorphic Vector Spaces

**Definition:** An isomorphism is an invertible linear map. Two vector spaces are called isomorphic if there is an isomorphism from one vector space onto the other one.

We say that $T \in \mathcal{L}(V,W)$ is an isomorphism if it is invertible. If there exists an isomorphism between $V$ and $W$ we say that they are isomorphic.

**Examples:** 

$V = \text{span }\{x,x^2\}$, $W = \text{span }\{1,x\}$. $T(f(x)) = f'(x)$. 

$T$ is invertible, since $T^{-1}f = \int f(x) dx$ ($\text{dim }V = \text{dim }W$). 

If $V=\text{span }\{1,x,x^2\}$ , then $T$ is no longer invertible, since the map is no longer injective. The same goes for $W$, if it was higher dimension it would no longer be surjective, so it wouldn't be invertible.


#### Isomorphic then equal dim

**Claim:** If $V,W$ are isomorphic, then $\text{dim }V = \text{dim }W$.

**Proof:** Let $V,W$ be isomorphic, with $\text{dim }V= n < \infty$. 

Then, for all $T \in \mathcal{L}(V,W)$ that is surjective and injective, $T$ being surjective implies that $\text{range }T = W$, and $T$ being injective implies that $\text{null } T = \{0\}$.

By the dimension theorem, $\text{dim range }T + \text{dim null }T = \text{dim }V$. 
Since $\text{dim range }T + \text{dim null }T = \text{dim }W$, then $\text{dim }V = \text{dim }W$ 


#### Equal (fin) dim then isomorphic


**Claim:** If $V$ and $W$ are finite dimensional and $\text{dim }V = \text{dim }W$, then they are isomorphic.

**Proof:** Let $\{v_1,...v_n\}$ be a basis for $V$ and $\{w_1,...,w_n\}$ be basis for $W$. Define $T \in \mathcal{L}(V,W)$ via $T(v_j) =w_j$ for all $j$. 

Clearly, $\text{span }\{w_1,...,w_n\} \subset \text{range }T$, and $\text{range }T \subset \text{span }\{w_1,...,w_n\}$ . Since $\{w_1,...,w_n\}$ is a basis, $\text{range }T= W$. 

Since $\text{dim }V = \text{dim }W$, $T$ being surjective implies that $T$ is injective. Since $T$ is surjective and injective, $T$ is an isomorphism. 


This means that each finite dimensional space is isomorphic to $\mathbb{F}^n$ where $n = \text{dim }V$.


**Claim:** Let $\mathbb{F}^{m,n} =\mathbb{F}^{m \times n}$ be the vector space of $m \times n$ matrices. Note that $\text{dim }(\mathbb{F}^{m,n}) = mn$. 

If $\text{dim }(V) = n, \text{dim }(W) = m$, then $\mathcal{L}(V,W)$ is isomorphic to $\mathbb{F}^{m,n}$.


**Proof:** Let $\{v_1,...,v_n\}$ be a basis for $V$, $\{w_1,...,w_m\}$ be a basis for $W$. We know the mapping $T \in \mathcal{L}(V,W)$ to its matrix is linear. We call this mapping $\mathcal{M}(T)$ and show it is 1-1 and onto:

(Injective) If $\mathcal{M}(T) =0$ then $T(v_j) = 0$ for all $j$, so $T=0$ since $v_j$ is a basis. Then $\text{null }(\mathcal{M}) =\{0\}$ and $\mathcal{M}$ is injective.

(Surjective) Let $A \in \mathbb{F}^{m,n}$ and define $T \in \mathcal{L}(V,W)$ via $$T(v_k) = \sum_{i=1}^m A_{jk}w_j$$ for all $k$. Then $A = \mathcal{M}(T)$ and so $\mathcal{M}$ is onto.

Since $\text{dim }(\mathbb{F}^{m,n})=mn < \infty$ and $\mathcal{M}$ is one-to-one and onto, $\mathcal{M}$ is an isomorphism.
### Column–Row Factorization and Rank of a Matrix

#### Matrix Rank

**Definition:** The rank of a matrix $A \in \mathbb{F}^{m,n}$ $\text{rank }A = \text{dim range }T$ 

Think of matrix multiplication as forming linear combinations of columns or rows of $A$.

- Column Rank of $A = \text{dim span (cols of A)}$ 
- Row Rank of $A \text{dim span(rows of A)}$  

Turns out, col rank = row rank so just say rank.


**Claim:** If $A \in \mathbb{F}^{m,n}$ is the matrix of $T \in \mathcal{L}(V,W)$ and $A_j \in \mathbb{F}^m$ is the $j$-th column of $A$, then $$\text{dim (span }\{A_1,...,A_n\}) = \text{dim (}R(T) = \text{rank}$$
**Proof:** 