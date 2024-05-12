# Solutions of Linear Systems
#math 


## Elementary Operations

Given $$A = \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{pmatrix}$$


Type 1: Exchanging first and second row of $A$ to get 

$$B = \begin{pmatrix} 4 & 5 &6 \\ 1 & 2 & 3 \\ 7 & 8 & 9 \end{pmatrix}$$


Type 2: Multiply second row of $A$ by $\frac 1 4$ gives

$$C = \begin{pmatrix} 1 & 2 & 3 \\ 1& \frac5 9 & \frac 3 2  \\ 7 & 8 & 9 \end{pmatrix}$$




Type 3: Add twice the first column to the second column of $A$ to get 

$$D = \begin{pmatrix} 1 & 4 & 3 \\ 4& 13& 6  \\ 7 & 22 & 9 \end{pmatrix}$$


### Elementary Matrix

**Definition:** an $n \times n$ elementary matrix is a matrix obtained by performing an elementary operation on $I \in \mathbb{F}^{n \times n}$. 

As before, we say an elementary matrix of type 1,2, or 3 depending on the kind of elementary operation used. 

Let $E_M$ denote the elementary matrix of some matrix $M$:

$$E_A =\begin{pmatrix} 1 & 0 &  0\\ 0 & 1 &0\\ 0 & 0 & 1 \end{pmatrix}$$

Type 1:

$$E_B =\begin{pmatrix} 0& 1 &  0\\ 1& 0 &0\\ 0 & 0 & 1 \end{pmatrix}$$


Type 2:

$$E_C =\begin{pmatrix} 1 & 0 &  0\\ 0 & \frac 1 4&0\\ 0 & 0 & 1 \end{pmatrix}$$

Type 3: 

$$E_D =\begin{pmatrix} 1 & 2 &  0\\ 0 & 1 &0\\ 0 & 0 & 2 \end{pmatrix}$$


Note that $B = E_B \times A$:

$$B = \begin{pmatrix} 0& 1 &  0\\ 1& 0 &0\\ 0 & 0 & 1 \end{pmatrix} \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{pmatrix} = \begin{pmatrix} 4 & 5 &6 \\ 1 & 2 & 3 \\ 7 & 8 & 9 \end{pmatrix}$$


Therefore $E_B$ when multiplied on the left encodes the 'action' of swapping rows 1 and 2.

Similarly, $C = E_C \times A$. However, we have $D = A \times E_D$. That is, row operations are done via elementary matrix mu;tliplication on the left.

Note that $$(E_B)^2 = \begin{pmatrix} 0& 1 &  0\\ 1& 0 &0\\ 0 & 0 & 1 \end{pmatrix}\begin{pmatrix} 0& 1 &  0\\ 1& 0 &0\\ 0 & 0 & 1 \end{pmatrix} = \begin{pmatrix} 1 & 0 &  0\\ 0 & 1 &0\\ 0 & 0 & 1 \end{pmatrix}$$

Thus $E_B$ is its own inverse.

**Theorem:** Elementary matrices are invertible, and the inverse is an elementary matrix of the same type. 


**Proof:** (sketch) We go case-by-case and its straightforward to design the inverse of an arbitrary elementary matrix of each type.

Recall that the [[Invertibility, Isomorphisms#Matrix Rank |rank]] of a linear map $T$ is $\text{dim range }T$. We can associate with each matrix $A \in \mathbb{F}^{m \times n}$ a linear map $L_A \in \mathcal{L}(\mathbb{F}^n, \mathbb{F}^n)$ via $L_Ay = Ay$ for ever $y \in \mathbb{F}^n$ 


We can show:

**Theorem:** Let $A \in \mathbb{F}^{m \times n}$. If $P \in \mathbb{F}^{m \times m}, Q \in \mathbb{F}^{n \times n}$ are invertible then:

1. $\text{rank }(AQ) = \text{rank }A$
2. $\text{rank }(PA) = \text{rank }A$
3. $\text{rank }(PAQ) = \text{rank }A$

**Proof:** We'll prove (1) only.  (2) is similar to (1) and (1)+(2) = (3). We will show that $\text{range }A = \text{range }(AQ)$

Let $w \in \text{range }(AQ)$. Then there exists a $v \in \mathbb{F}^n$ such that $AQv = w$. Then $$w = AQv = Az, z =Qv \in \mathbb{F}^n$$So that $w \in \text{range }A$. Then $\text{range }(AQ) \subseteq \text{range }A$.

For the other direction, let $w \in \text{range }A$. Then there exists $v \in \mathbb{F}^n$ such that $w = Av$. Since $Q$ is invertible $$w = Av = A(Iv) = A(Q Q^{-1})v = AQ(Q^{-1}v)$$Then if $z = Q^{-1} v$ we have $AQz = w$ so that $w \in \text{range }(AQ)$. Therefore $\text{range }(AQ) \subseteq \text{range }A$.

We then have $\text{range }A = \text{range }(AQ) \implies \text{rank }(AQ) = \text{rank }(A)$.

(2) and (3) are similar.


**Corollary:** Elementary row and column operations are rank-preserving.

**Proof:** If $B$ is obtained from $A$ by an elementary row operation, then there exists an elementary matrix $E$ such that $B = EA$. 

By previous theorem $E$ is invertible and thus $\text{rank }B = \text{rank }(EA) = \text{rank }A$. 

A similar argument holds for column operations.


### Gaussian Elimination

you know how to do this...


May not be feasible for larger systems. We will rewrite in matrix form:

$$A = \begin{pmatrix}1 & 1 \\ 1 & -1 \end{pmatrix}, B = \begin{pmatrix}3 \\ 1 \end{pmatrix}$$

We then write $$ \begin{pmatrix}1 & 1 \\ 1 & -1 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \end{pmatrix} = \begin{pmatrix} 3 \\ 1 \end{pmatrix} \implies Ax = b$$

We'll seek to transform this system into one that is easier to solve.

**Definition:** Two systems of linear equations are equivalent if they have the same solutions set $$\{x \in V | Ax = b\}$$
**Theorem:** Let $Ax = b$ be a system of $m$ linear equations in $n$ unknowns ($A \in \mathbb{F}^{m \times n}$). Let $C \in \mathbb{F}^{m \times m}$ be invertible. The system $(CA)x = Cb$ is equivalent to $Ax = b$

**Proof:** Let $K$ be the solution set of $Ax = b$, $\tilde K$ the solutions set of $(CA)x = Cb$. We'll seek to show that $K \subseteq \tilde K$ and $\tilde K \subseteq  K$


($K \subseteq \tilde K$) Let $s \in K$. Then $As=b$. By definition, multiplying on the left by $C$ gives $$C(As) = Cb \implies (CA)s = Cb$$
 so that $s \in \tilde K$. Thus $k \subseteq \tilde K$


($\tilde K \subseteq  K$) Let $s \in \tilde K$. Then $(CA)s = Cb$  Since $C$ is invertible there exists a $C^{-1}$ such that $C^{-1}C = CC^{-1} = I$. Then multiplying on the left by $C^{-1}$ gives $$C^{-1}(CAs) = C^{-1}CAs = As = C^{-1}Cb = b$$

By definition $s \in K$ so that $\tilde K \subseteq  K$. Therefore $K = \tilde K$.


That is, multiplying the equation $Ax = b$ by an invertible matrix does not change the solution. 

Asa  result, multiplying by elementary matrices preserves the solution. We now defined the augmented system $$(A|b)$$

which is the $mx(n+1)$ matrix obtained by appending the vector $b$ as a further column in $A$.

**Example:** We define the augmented system for our prev example:

$$ \begin{pmatrix}1 & 1 \\ 1 & -1 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \end{pmatrix} = \begin{pmatrix} 3 \\ 1 \end{pmatrix} \rightarrow \left( 
    \begin{array}{cc|c}
        1 & 1 & 3 \\
        1 & -1 & 1 \\
    \end{array}
\right)$$


 We'll see elementary matrices/operations to turn this into an [[UT, Diagonal Matrices#Upper Triangular Matrices|upper triangular matrix]] with 1s on the diagonal.


By type 3:
$$\left( 
    \begin{array}{cc|c}
        1 & 1 & 3 \\
        1 & -1 & 1 \\
    \end{array}
\right) \rightarrow \left( 
    \begin{array}{cc|c}
        1 & 1 & 3 \\
        0 & -2 & -2 \\
    \end{array}
\right)$$We now have a UT matrix.


### RREF

**Definition:** A matrix is said to be in reduced row echelon form (RREF) if the following 3 conditions are satisfied:

1. Any row containing a non-zero entry precedes any row in which all entries are zero (if any)
2. The first non-zero entry in each row is the only non-zero entry in its column
3. The first non-zero entry in each row is 1 and it occurs in a column to the right of the first non-zero entry in the preceding row


### Homogeneity

**Definition:** A system $Ax = b$ of $m$ linear equations in $n$ unknowns is said to be homogeneous if $b = 0$. 

Otherwise the system is said to be inhomogeneous.

#### Homogeneous Systems

**Theorem:** Let $Ax = 0$ be a homogeneous system of $m$ linear equations in $n$ unknowns over a field $\mathbb F$. Let $K$ denote the set of all solutions to $Ax = 0$. 

Then $K = \text{null }L_A$. Hence, $K$ is a subspace of $\mathbb F^n$ of dimension $n - \text{rank }L_A = n -\text{rank }A$. Note that $L_A$ denotes the linear transformation represented by the matrix $A$

**Proof:** Clearly $K = \{s \in \mathbb F ^n \space | As = 0\} = \text{null }L_A$. Second part follows from dimension theorem.


**Corollary:** If $m < n$, the system $Ax= 0$ has a non-zero solution.

**Proof:** Suppose $m < n$. Then $\text{rank }A = \text{rank }L_A \leq m$. Hence
$$\text{dim }K = n - \text{rank }L_A \geq n-m > 0$$
where $K = \text{null }L_A$. Since $\text{dim }K > 0, K \neq \{0\}$. Thus there exists a non-zero vector $s \in K$ such that $s$ is a non-zero solution to $Ax=0$

**Example:** Consider the system $x_1-2x_2+x_3 = 0$ of one equation in three unknowns. If $A = (1-21)$ is the coefficient matrix then $\text{rank }A =1$. 

Hence if $K$ is the solution set, then by dimension theorem $\text{dim }K = 3-1 = 2$. Note that $(2,1,0)$ and $(-1,0,1)$ are linearly independent vectors in $K$. Thus they constitute a basis for $K$ so that $K = \text{span}\{(2,1,0),(-1,0,1)\}$

#### Inhomogeneous Systems

**Theorem:** Let $K$ be the solution set of a system of linear equations $Ax=b$. Let $K_H$ be the solution set corresponding to the homogeneous system $Ax=0$. 

Then for any solution $s$ to $Ax=b$ $$K = \{s\} + K_H = \{s+k \space | \space k \in K_H\}$$
**Proof:** Let $s$ be any solution to $Ax=b$. We must show that $K = \{s\} + K_H$. If $w \in K$, then $Aw =b$. Hence $$A(w-s) = Aw-As= b-b = 0$$
So $w-s \in K_H$. Thus there exists $k \in K_H$ such that $w-s =k$. 

It follows that $w = s+k \in \{s\}+K_H$ and therefore $K \subseteq \{s\}+K_H$.

Conversely, suppose that $w \in \{s\}+K_H$. Then $w = s+k$ for some $k \in K_H$. But then $Aw = A(s+k) = As + Ak = b+0 = b$ so $w \in K$. Therefore $\{s\} + K_H \subseteq K$ and thus $K =\{s\}+K_H.$


In other words, for an inhomogeneous system we can always add a vector in the null space to a solution and get another valid solution. 

This implies that we do not have unique solutions if the null space is non-trivial. We can thus show the following:

**Theorem:** Let $Ax=b$ be a system of linear equations in $n$ unknowns. If $A$ is invertible then the system has exactly one solution, namely $A^{-1}b$. 

Conversely, if the system has exactly one solution then $A$ is invertible.