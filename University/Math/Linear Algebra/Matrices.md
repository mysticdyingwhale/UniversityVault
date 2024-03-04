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

#### Standard Basis

The standard basis is the simplest basis of the space of all $k$ dimensional vectors. It is made up of vectors that have one entry equal to 1 and the remaining $k-1$ entries equal to 0.

$$
I =

\left[ {\begin{array}{cc}

1 & 0 & ... &0 \\
0 & 1& ...&0\\
 & & \vdots & \\
0 & 0 &... &1\\

\end{array} } \right]
$$


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
Thus, the entry in row $j$, column $k$ of $AB$ is computed by taking row $j$ of $A$ and column $k$ of $B,$ multiplying together corresponding entries, and then summing. 

#### Example

Given a 3-by-2 matrix multiplied by a 2 by 4 matrix:

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
The resulting matrix is 3 by 4. 

>[!NOTE]
>Matrix multiplication is **not** commutative. $AB$ doesn't necessarily equal $BA$. It is, still distributive and associative.
>$A(B+C)= AB+AC$
>$A(BC) =(AB)C$


#### Examples

$V = P_2 = \text{span}(1,x,x^2)$ , $W = P_1 = \text{span}(1,x^2)$ . 

Let $T \in \mathcal{L}(V,W)$ be $T(f(x))= f'(x)$. We'll represent a polynomial $a+bx+cx^2$ as the vector: $$a \cdot v_1 + b \cdot v_2 + c \cdot v_3 = a \cdot 1 + b \cdot x + c \cdot x^2 \implies
\begin{pmatrix} a\\ b\\ c \end{pmatrix}
$$

### Matrix of product of linear maps

**Definition:** If $T \in \mathcal{L}(U,V)$ and $S \in \mathcal{L}(V,W)$, then $\mathcal{M}(ST) = \mathcal{M}(S)+\mathcal{M}(T)$. 

**Proof:** Suppose $\mathcal{M}(S)=A$ and $\mathcal{M}(T)=B$. For $1 \leq k \leq p$, we have $$(ST)u_k= S(\sum_{r=1}^nB_{r,k}v_r)$$$$=\sum_{r=1}^nB_{r,k}Sv_r$$$$=\sum_{r=1}^nB_{r,k} \sum_{j=1}^nA_{j,r}w_j$$$$=\sum_{j=1}^n(\sum_{r=1}^nB_{r,k} A_{j,r})w_j$$
Thus, $\mathcal{M}(ST)$ is the $m$ by $p$ matrix whose entry in row $j$, column $k$ equals $$\sum_{r=1}^nB_{r,k} A_{j,r} = \mathcal{M}(S)\mathcal{M}(T)$$

>[!NOTE] Notation
>Suppose $A$ is an $m$ by $n$ matrix
> - If $1 \leq j \leq m$, then $A_{j,.}$ denotes the 1 by $n$ matrix consisting of row $j$ of $A$
> - If $1 \leq k \leq n$, then $A_{.,k}$ denotes the $m$ by 1 matrix consisting of column $k$ of $A$

For example,  $A_{2,.}$ denotes the second row of $A$ and $A_{.,2}$ denotes the second column of $A$. So, if $$A =\left[ {\begin{array}{cc}

8 & 4 & 5  \\
1 & 9 &7 \\


\end{array} } \right] $$then $A_{2,.} = \begin{pmatrix} 1,9,7 \end{pmatrix}$ and $A_{.,2} = \begin{pmatrix}4 \\ 9 \end{pmatrix}$ 

#### Entry of matrix product equals row times column

**Claim:** Suppose $A$ is an $m$ by $n$ matrix and $B$ is an $n$ by $p$ matrix. Then $$(AB)_{j,k}=A_{j,.}B_{.,k}$$
If $1 \leq j \leq m$ and $1 \leq k \leq p$. 

In other words, the entry in row $j$, column $k$, of $AB$ equals (row $j$ of $A$) times (column $k$ of $B$).

**Proof:** Suppose $1\ \leq j \leq m$ and $1 \leq k \leq p$. The definition of matrix multiplication states that $$(AB)_{j,k}= A_{j,1}B_{1,k}+...+A_{j,n}B_{n,k}$$
The definition of matrix multiplication also implies that the product of the 1-by-$n$ matrix $A_{j,.}$ and the $n$-by-1 matrix $B_{.,k}$ is the 1-by-1 matrix whose entry is the number on the right side of the equation above.

Thus the entry in row $j$, column $k$ of $AB$ equals (row $j$ of $A$) times (column $k$ of $B$).

The next result gives yet another way to think of matrix multiplication. In the result below $(AB)_{.,k}$ is column $k$ of the $m$-by-$p$ matrix $AB$. Thus, $(AB)_{.,k}$ is an $m$-by-1 matrix. 

Also, $(AB)_{.,k}$ is an $m$-by-1 matrix. Thus the two sides of the equation in the result below have the same size, making it reasonable that they might be equal.

#### Column of matrix product equals matrix times column

**Claim:** Suppose $A$ is an $m$-by-$n$ matrix and $B$ is an $n$-by-$p$ matrix. Then $$(AB)_{.,k}= AB_{.,k}$$ if $1 \leq k \leq p$.

In other words, column $k$ of $AB$ equals $A$ times column $k$ of $B$.

**Proof:**


#### Linear combination of columns

**Claim:** Suppose $A$ is an $m$-by-$n$ matrix and $b = \begin{pmatrix} b_1 \\ \vdots \\ b_n \end{pmatrix}$  is an $n$-by-$1$ matrix. Then $$Ab = b_1A_{.,1}+...+b_nA_{.,n}$$ In other words, $Ab$ is a linear combination of the columns of $A$, with the scalars that multiply the columns coming from $b$.

**Proof:**

#### Matrix multiplication as linear combinations of columns

**Claim:** Suppose $C$ is an $m$-by-$c$ matrix and $R$ is a $c$-by-$n$ matrix. 

1. If $k \in \{1,...,n\}$, then column $k$ of $CR$ is a linear combination of the columns of $C$, with the coefficients of this linear combination coming from column $k$ of $R$.
2. If $j  \in \{1,...,m\}$ then row $j$ of $CR$ is a linear combination of the rows of $R$, with the coefficients of this linear combination coming from row $j$ of $C$

**Proof:**

