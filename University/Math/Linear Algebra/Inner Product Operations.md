# Inner Product Operations
#math 


## Self-Adjoint/Normal Operators


### Adjoint

**Definition:** Suppose $T \in \mathcal{L}(V,W)$. The adjoint of $T$ is the function $T^*: W \rightarrow V$ such that $$\langle Tv,w \rangle = \langle v, T^* w \rangle$$
for every $v \in V$ and every $w \in W$

### Linear Functionals

**Definition:** A linear functional on $V$ is a linear map from $V$ to $\mathbb{F}$. The dual space of $V$, denoted by $V'$, is the vector space of all linear functionals on $V$.

In other words, $V' = \mathcal{L}(V,\mathbb{F})$



### Riesz-Representation Theorem

**Definition:** Suppose $V$ is finite-dimensional and $\varphi$ is a linear functional on $V$. Then there exists a unique $v \in V$ such that $\varphi(u) = \langle u,v \rangle$  for all $u \in V$  

In other words, in an inner product space any functional can be identified with a vector in $V$. 


**Example:** Let $T : \mathbb{R}^3 \rightarrow \mathbb{R}^2$ be defined by $$T(x_1,x_2,x_3) = (x_2+3x_3,2x_1)$$

Suppose $(y_1,y_2) \in \mathbb{R}^2$. Then $$\langle T(x_1,x_2,x_3),(y_1,y_2)\rangle = \langle (x_2+3x_3,2x_1),(y_1,y_2)\rangle$$$$= (x_2+3x_3)y_1+2x_1y_2 = 2x_1y_2+x_2y_1+3x_3y_1$$
$$ = \langle (x_1,x_2,x_3),(2y_2,y_1,3y_1)\rangle$$

Then $T^*(y_1,y_2) = (2y_2,y_1,3y_1)$.

Note $T^* \in \mathcal{L}(W,V)$

#### Adjoint of a linear map is a linear map

**Claim:** If $T \in \mathcal{L}(V,W)$, then $T^* \in \mathcal{L}(V,W)$.

**Proof:** Suppose $T \in \mathcal{L}(V,W)$. If $v \in V$ and $w_1,w_2 \in W$ then:
$$\langle Tv,w_1+w_2 \rangle = \langle Tv,w_1 \rangle + \langle Tv, w_2 \rangle$$$$= \langle v, T^*w_1 \rangle + \langle v, T^*w_2 \rangle = \langle v, T^*w_1 + T^*w_2 \rangle$$ 
Which shows that $T^*(w_1+w_2) = T^*w_1 + T^*w_2$ (additivity).

If $v \in V, \lambda \in \mathbb{F}, w \in W$, then: 
$$\langle Tv, \lambda w \rangle = \overline \lambda \langle Tv,w \rangle$$
$$\overline \lambda \langle v, T^*w \rangle = \langle v, \lambda T^* w \rangle$$
Which shows that $T^*(\lambda w) = \lambda T^*(w)$ (homogeneity).

Thus $T^* \in \mathcal{L}(V,W)$

#### Properties of Adjoint


Suppose $T \in \mathcal{L}(V,W)$. Then:

1. $(S+T)^* = S^* + T^*$ for all $S \in \mathcal{V,W}$
2. $(\lambda T)^* = \overline \lambda T^*$ for all $\lambda \in \mathbb{F}$ 
3. $(T^*)^* = T$
4. $(ST)^* = T^*S^*$ for all $S \in \mathcal{L}(W,U)$, where $U$ is a fin-dim inner product space over $\mathbb{F}$
5. $I^* = I$, $I$ is identity operator
6. If $T$ is invertible, then $T^*$ is invertible and $(T^*)^{-1} = (T^{-1})^*$



**Proof:**

1. If $S \in \mathcal{L}(V,W)$ then $\langle (S+T)v,w \rangle = \langle Sv,w \rangle + \langle Tv,w \rangle = \langle v,(S^*+T^*)w \rangle$
2. If $\lambda \in \mathbb F$ then $\langle (\lambda T)v,w \rangle = \lambda \langle Tv,w \rangle = \lambda \langle v, T^*w \rangle  = \langle v , \overline \lambda T^*w \rangle$ 
3. $\langle T^* w, v \rangle = \overline{\langle v, T^*w\rangle} = \overline{\langle Tv,w \rangle} = \langle w, Tv \rangle$
4. Let $S \in \mathcal{L}(W,U)$ and $u\in U$. Then $\langle (ST)v,w \rangle = \langle Tv,S^*w \rangle  = \langle v, T^*S^*w \rangle$
5. Let $u \in U$. Then $\langle Iu,v \rangle =\langle u,I^*v \rangle= \langle u,v \rangle$ So $I^*v = Iv = v$ for all $v$.
6. Let $T$ be invertible. Then $TT^{-1}  = I = T^{-1}T$. We have $(T^{-1}T)^* = I^* = I$ and (4) gives $T^*(T^{-1})^*=I$. Similarly, $TT^{-1}=I$ gives $(T^{-1})^*T^* = I \implies (T^{-1})^* = (T^*)^{-1}$



#### Null space and range of adjoint

**Claim:** Suppose $T \in \mathcal{}(V,W)$. Then:

1. $\text{null }T^* = (\text{range }T)^\perp$ 
2. $\text{range }T^* = (\text{null }T)^\perp$
3. $\text{null }T = (\text{range }T^*)^\perp$
4. $\text{range }T = (\text{null }T^*)^\perp$

**Proof:** Let $w \in W$. Then $w \in \text{null }T^* \iff T^*w = 0$
$\iff \langle v, T^*w \rangle =0$ for all $v$
$\iff \langle Tv,w \rangle  =0$ for all $v$
$\iff w \in (\text{range }T)^\perp$ 

Thus $\text{null }T^* = (\text{range }T)^\perp$. We also have $(\text{null }T^*)^\perp = ((\text{range }T)^\perp)^\perp = \text{range }T$ proving (4). Replacing $T$ with $T^*$ in (1) and (4) gives (2) and (3) respectively.

### Conjugate Transpose

**Definition:** Let $A \in \mathbb{F}^{m \times n}$. We say the conjugate transpose of $A$, denoted by $A^*$ is $$(A^*)_{jk} = A_{kj}$$
**Example:** Given $A = \begin{pmatrix} 2 & 3+4i & 7 \\ 6 & 5 & 8i \end{pmatrix}$ 

$A^* = \begin{pmatrix} 2 & 6 \\ 3 - 4i & 5 \\ 7 & -8i \end{pmatrix}$ 


**Theorem:** Suppose $A \in \mathbb{F}^{m \times n}$ is the matrix of $T$ with [[Orthonormality|orthonormal]] bases $\{v_1,...,v_n\}$ for $V$ and $\{w_1,...,w_m\}$ for $W$. Then the matrix of $T^*$ in these bases is $A^* \in \mathbb{F}^{n \times m}$ 


### Self-Adjoint

**Definition:** We say $T \in \mathcal{L}(V)$ is self adjoint if $T^* = T$. In other words, $\langle Tv,w \rangle = \langle v, Tw \rangle$ for all $v,w \in V$


#### Self adjoint eigenvalues are real

**Claim:** Every eigenvalue of a self-adjoint operator is real.

**Proof:** Let $\lambda,v$ be an eigenpair of $T \in \mathcal{L}(V)$, then $$\lambda ||v||^2 = \lambda \langle v,v\rangle  = \langle \lambda v, v \rangle = \langle Tv, v \rangle = \langle v, Tv \rangle = \langle v, \lambda v \rangle = \overline \lambda \langle v, v \rangle = \overline \lambda ||v||^2$$

Since $v \neq 0$, this means that $\lambda = \overline \lambda$ so $\lambda \in \mathbb{R}$. 


#### Tv orthogonal to v for all v iff T=0

**Claim:** If $\mathbb{F} = \mathbb{C}$ OR ($\mathbb{F} = \mathbb{R}$ and $T = T^*$) and $\langle Tv, v \rangle =0$ for all $v \in V$ then $T= 0$.

**Example:** $T(x,y) = (-y,x)$ and $(x,y) \in \mathbb{R}^2$. Then $\langle Tv, v \rangle = 0$ for all $v \in V$ but $T \neq 0$ when $\mathbb{F} = \mathbb{R}$ 


### Normal

**Definition:** If $T \in \mathcal{L}(V)$ such that $TT^* = T^* T$  ($T$ commutes with its adjoint $T^*$) we say $T$ is normal.


>[!NOTE] 
>Note that $T = T^*$ implies that $T$ is normal
>Self adjoint $\implies$ normal
>Converse is NOT true



**Example:** $T(x_1,x_2) = \begin{bmatrix} 1 & i \\ 1 & 1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}$ 

Then $T^*(x_1,x_2) = \begin{bmatrix}1 & 1 \\ -i & 1 \end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} \neq T(x_1,x_2)$ 

$T$ is not self-adjoint, but $$TT^*(x_1,x_2) = \begin{bmatrix}1 & i \\ 1 & 1 \end{bmatrix} \begin{bmatrix} 1 & 1 \\ -i & 1\end{bmatrix} = \begin{bmatrix} 2 & 1+i \\1-i & 2\end{bmatrix} \begin{bmatrix}x_1 \\ x_2\end{bmatrix}$$

$$T^*T(x_1,x_2) = \begin{bmatrix}1 & 1 \\ -i & 1 \end{bmatrix} \begin{bmatrix} 1 & i \\ 1 & 1\end{bmatrix} = \begin{bmatrix} 2 & 1+i \\1-i & 2\end{bmatrix} \begin{bmatrix}x_1 \\ x_2\end{bmatrix}$$
Since $TT^* = T^*T$,  $T$ is normal.

**Claim:** An operator is normal iff $||Tv||^2 = ||T^*v||^2$

**Proof:** $T$ is normal iff for all $v \in V$ $$TT^* -T^*T = 0 \iff \langle (TT^* - T^*T)v,v)=0$$
Since $TT^* - T^*T$ is self adjoint, this is true.

$$\iff \langle TT^*v,v \rangle = \langle T^*Tv,v \rangle \space \forall v$$
$$\iff \langle T^*v,T^*v \rangle = \langle Tv,Tv \rangle \space \forall v$$
$$\iff ||T^*v||^2 = ||Tv||^2 \space \forall \space v \in V $$

**Theorem:** Suppose $T \in \mathcal{L}(V)$ is normal. 

1. $\text{null }T = \text{null }T^*$
2. $\text{range }T = \text{range }T^*$
3. $V = \text{null }T \oplus \text{range }T$
4. $T - \lambda I$ is normal for all $\lambda \in \mathbb{F}$ 
5. If $v \in V, \lambda \in \mathbb{F}$ then $Tv = \lambda v \iff T^*v = \overline \lambda T^*v$


**Proof:** 

1. Suppose $v \in V$. Then $v \in \text{null }T \iff ||Tv|| = 0 \iff ||T^*v || = 0 \iff v \in \text{null }T^*$
2. $\text{range }T = (\text{null }T^*)^\perp = (\text{null }T)^\perp = \text{range }T^*$
3. $V = \text{null }T \oplus (\text{null }T)^\perp = \text{null }T \oplus \text{range }T^* = \text{null }T \oplus \text{range }T$
4. Suppose $\lambda \in \mathbb F$. Then $(T - \lambda I)(T - \lambda I)^* = (T - \lambda I)(T^* - \lambda I) = TT^* - \overline \lambda T -\lambda T^* + |\lambda|^2 I = T^*T - \overline \lambda T -\lambda T^* + |\lambda|^2 I = (T^* - \overline \lambda I)(T - \lambda I) = (T - \lambda I)^*(T - \lambda I)$ So that $T - \lambda I$ is normal
5. Suppose $v \in V, \lambda \in \mathbb F$. Then $||(T - \lambda I)v|| = ||(T - \lambda I)^*v|| =  ||(T^* - \overline \lambda I)v||$ So that $||(T - \lambda I)v|| = 0 \iff ||(T^* - \overline \lambda I)v|| = 0$ so that $Tv = \lambda v \iff T^*v = \overline \lambda v$ 


Note normality is essential for (5).


**Theorem:** Suppose $T \in \mathcal{L}(V)$ is normal. Then the eigenvectors corresponding to distinct  eigenvalues are orthogonal.

**Proof:** Let $\alpha, \beta \in \mathbb F$ be distinct eigenvalues of $T$ with eigenvectors $u,v \in V$. Then $Tu= \alpha v, Tv = \beta v$ and also $T^*v = \overline \beta v$. Then
$$(\alpha - \beta)\langle u,v \rangle = \langle \alpha u,v \rangle - \langle u, \overline \beta v \rangle = \langle Tu,v \rangle - \langle u, T^*v \rangle = 0$$

Since $\alpha \neq \beta$ we have $\langle u,v \rangle = 0$.


