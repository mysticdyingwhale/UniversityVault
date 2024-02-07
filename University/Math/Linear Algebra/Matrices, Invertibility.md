#math 

# Matrices

**Definition:** Suppose $m$ and $n$ are non-negative integers. An $m$ by $n$ matrix $A$ is a rectangular array of elements of $\mathbb{F}$ with $m$ rows and $n$ columns.

$$
A =

\left[ {\begin{array}{cc}

a_{1,1} & ...& a_{1,n} \\
\vdots & & \vdots \\
a_{m,1} & ... &a_{m,n} \\

\end{array} } \right]
$$

### Matrix of a linear map

**Definition:** Suppose $T \in \mathcal{L}(V,W)$ and $v_1,...,v_n$ is a basis of $V$and $w_1,...,w_m$ is a basis of $W.$ The matrix of $T$ with respect to these bases is the $m$-by-$n$ matrix $\mathcal{M}(T)$ who's entries $A_{j,k}$ are defined by $$Tv_k = A_{1,k}w_1+...+A_{m,k}w_m.$$
>[!NOTE]
>If the bases $v_1,...,v_n$ and $w_1,...,w_m$ are not clear from the context, then the notation $\mathcal{M}(T,(v_1,...,v_n),(w_1,...,w_m))$ is used.


### Matrix Addition & Scalar Multiplication

#### Addition

**Definition:** The sum of two matrices of the same size is the matrix obtained by adding corresponding entries in the matrices

$$

\left[ {\begin{array}{cc}

a_{1,1} & ...& a_{1,n} \\
\vdots & & \vdots \\
a_{m,1} & ... &a_{m,n} \\

\end{array} } \right] +

\left[ {\begin{array}{cc}

c_{1,1} & ...& c_{1,n} \\
\vdots & & \vdots \\
c_{m,1} & ... &c_{m,n} \\

\end{array} } \right] = \left[ {\begin{array}{cc}

a_{1,1}+c_{1,1} & ...& a_{1,n}+c_{1,n} \\
\vdots & & \vdots \\
a_{m,1}+c_{m,1} & ... &a_{m,n}+c_{m,n} \\

\end{array} } \right]$$

Suppose $S,T \in \mathcal{L}(V,W).$ Then $\mathcal{M}(S+T) = \mathcal{M}(S)+\mathcal{M}(T)$ 



#### Scalar Multiplication

**Definition:** The product of a scalar and a matrix is the matrix obtained by multiplying each entry in the matrix by the scalar:

$$\lambda \left[ {\begin{array}{cc}

a_{1,1} & ...& a_{1,n} \\
\vdots & & \vdots \\
a_{m,1} & ... &a_{m,n} \\

\end{array} } \right] = \left[ {\begin{array}{cc}

\lambda a_{1,1} & ...& \lambda a_{1,n} \\
\vdots & & \vdots \\
\lambda a_{m,1} & ... &\lambda a_{m,n} \\

\end{array} } \right] $$


Suppose $\lambda \in \mathbb{F}$ and $T \in \mathcal{L}(V,W).$ Then $\mathcal{M}(\lambda T) = \lambda \mathcal{M}(T)$ .

>[!NOTE]
>For $m$ and $n$ positive integers, the set of all $m$-by-$n$ matrices with entries in $\mathbb{F}$ is $\mathbb{F}^{m,n}$

Suppose $m,n$ are positive integers. With addition and scalar multiplication defined as above, $\mathbb{F}^{m,n}$ is a vector space of dimension $mn$. $\text{dim }\mathbb{F}^{m,n}=mn$


### Matrix Multiplication

**Definition:** Suppose $A$ is an $m$-by-$n$ matrix and $B$ is an $n$-by-$p$ matrix. Then $AB$ is defined to be the $m$-by-$p$ matrix who's entry in row $j$, column $k$ is given by the equation $$(AB)_{j,k}= \sum_{r=1}^{n}A_{j,r}B_{r,k}.$$
Thus, the entry in row $j$, column $k$ of $AB$ is computed by taking row $j$ of $A$ and column $k$ of $B$, multiplying together corresponding entries, and then summing. 

#### Example

$$\left[ {\begin{array}{cc}

1 & 2  \\
3 & 4 \\
5 & 6 \\

\end{array} } \right] \left[ {\begin{array}{cc}

6 & 5 & 4 & 3  \\
2 & 1 & 0 & -1 \\


\end{array} } \right]  = \left[ {\begin{array}{cc}

10 & 7 & 4 & 1  \\
26 & 19 & 12 & 5 \\
42 & 31 & 20 & 9


\end{array} } \right]  $$


>[!NOTE]
>Matrix multiplication is **not** commutative. $AB$ doesn't necessarily equal $BA$. It is, still distributive and associative.


#### Examples

$V = P_2 = \text{span}(1,x,x^2)$ , $W = P_1 = \text{span}(1,x^2)$ . 

Let $T \in \mathcal{L}(V,W)$ be $T(f(x))= f'(x)$. We'll represent a polynomial $a+bx+cx^2$ as the vector: $$a \cdot v_1 + b \cdot v_2 + c \cdot v_3 = a \cdot 1 + b \cdot x + c \cdot x^2 \implies
\begin{pmatrix} a\\ b\\ c \end{pmatrix}
$$


# Invertibility

**Definition:** Let $T \in \mathcal{L}(V,W)$. We say that $T$ is invertible if there exists an $S \in \mathcal{L}(V,W)$ such that $$S(T(v))= v$$ for all $v \in V$, and $$S(T(w))=w$$ for all $w \in W$. 

I.E,  $ST = I$ on $V$, $TS = I$ on $W$. We call $S$ the **inverse** of $T$


**Claim:** The inverse is unique.

**Proof:** Let $S, \tilde{S} \in \mathcal{L}(W,V)$ be inverses of $T$. Then for $w \in W$, $S(w)=S \circ (T \circ \tilde{S}(w)) = (S \circ T)(\tilde{S}(w))$ .

This indicates $S = \tilde{S}$, since $S(w) = \tilde{S}(w)$ for all $w \in W$. 


>[!NOTE] 
>We typically write $T^{-1}$ to note the inverse of $T$. 

**Claim:** A linear map is invertible if and only if it is injective (one-to-one) and surjective (onto).

**Proof:** ($\implies$) Let $T \in \mathcal{L}(V,W)$ be invertible. 

**Injectivity:** Let $u,v \in V$ such that $T(u) = T(v)$. 

$u  = I(u) = T^{-1}(T(u)) = T^{-1}(T(v))=I(v)=v$  

Therefore, $T$ is one-to-one.

**Surjectivity:** Let $w \in W$. Then $w = I(w) = T(T^{-1}(w))$ so that $w \in \mathcal{R}(T)$. 

Since $T^{-1}(w) \in V$ such that $T(T^{-1}(w))=w$. Therefore $\mathcal{R}(T)= W$ and $T$ is onto. 