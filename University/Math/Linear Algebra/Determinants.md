# Determinants
#math 



**Definition:** If $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix} \in \mathbb{F}^{2 \times 2}$, we define $$\text{det}(A) = |A| = ad-bc$$
Where $\text{det}(A)$ is the determinant of $A$.

### Examples

$A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}$ 

Then $\text{det}(A) = 1 \cdot 4 - 2 \cdot 3 = 4-6 = -2$



$B = \begin{pmatrix} 3 & 2 \\ 6 & 4 \end{pmatrix}$


Then $\text{det}(B) = 3 \cdot 4 - 2 \cdot 6 = 12-12 = 0$

If $A$ is upper-triangular, then $\text{det}(A)$ is the product of diagonal entries.

$C = A+B = \begin{pmatrix} 4 & 4 \\ 9 & 8 \end{pmatrix}$


$\text{det}(PAQ) = \text{det}(P) \cdot \text{det}(A)  \cdot \text{det}(Q) = \text{det}(P)$, If $P,Q$ are unitary.

$\text{det} A + \text{det} B = -2 + 0 \neq -4 = \text{det}(A+C)$


The determinant is not linear (in general), we can also check that $A$ is invertible but $B$ is not.

Note that $B \begin{pmatrix} 1 \\ -{\frac{3}{2}} \end{pmatrix} = \begin{pmatrix} 3 & 2 \\ 6 & 4 \end{pmatrix} \begin{pmatrix} 1 \\ -{\frac{3}{2}} \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}$ 


Thus $\text{dim null }B \geq 1$ so that $B$ is not injective which implies that $B$ is not invertible. 

It turns out the determinant gives us an easy check for invertibility:

**Theorem:** Let $A \in \mathbb{F}^{2 \times 2}$. The determinant of $A$ is non-zero if and only if $A$ is invertible. 

If $A$ is invertible, then $$A^{-1} = \frac1{\text{det}A} \begin{pmatrix} a_{2,2} & -a_{1,2} \\ -a_{2,1} & a_{1,1} \end{pmatrix}$$

Assuming $A = \begin{pmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \end{pmatrix}$


**Proof:** ($\implies$) If $\text{det} A \neq 0$ then we can define $M = \frac{1}{\text{det}A} \begin{pmatrix} a_{2,2} & -a_{1,2} \\ -a_{2,1} & a_{1,1} \end{pmatrix}$


Then $$MA =\frac{1}{\text{det}A} \begin{pmatrix} a_{2,2} & -a_{1,2} \\ -a_{2,1} & a_{1,1} \end{pmatrix} \begin{pmatrix} a_{1,1} & a_{1,2} \\ a_{2,1} & a_{2,2} \end{pmatrix}$$
$$ = \frac{1}{\text{det}A}\begin{pmatrix} a_{2,2}a_{1,1} - a_{1,2}a_{2,1} & 0\\ 0 & a_{1,1}a_{2,2}  - a_{2,1}a_{1,2} \end{pmatrix}$$
$$ = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$$
Then $MA = I$. A similar calculation shows that $AM = I$. Then $A$ is invertible and $M = A^{-1}$


($\impliedby$) Conversely, suppose $A$ is invertible. By dimension theorem we must have $\text{rank }A = \text{dim range }A = 2$. Hence $a_{1,1} \neq 0$ or $a_{2,1} \neq 0$ (since otherwise $A$ would have a zero column which would imply dim null less than or equal to 1)

If $a_{1,1} \neq 0$ add $\frac{-a_{2,1}}{a_{1,1}}$ times row 1 of $A$ to row 2 to obtain:

$$\begin{pmatrix} a_{1,1} & a_{1,2} \\ 0 & a_{2,2} - \frac{a_{1,1}a_{2,1}}{a_{1,1}} \end{pmatrix}$$
Because elementary row operations are rank preserving, it follows that $a_{2,2} - \frac{a_{1,1}a_{2,1}}{a_{1,1}} \neq 0$ 

Implying that $a_{1,1}a_{2,2} - a_{1,1}a_{2,1} \neq 0$

Then $\text{det }A = a_{1,1}a_{2,2} - a_{1,1}a_{2,1} \neq 0$. A similar argument is used if $a_{2,1} \neq 0$. 

In either case $\text{det }A \neq 0$. 



## Determinants of order $n$

Let's now extend our definition to $A \in \mathbb{F}^{n \times n}$ for $n \geq 3$. 

We introduce a convenient notation: Let $A \in \mathbb{F}^{n \times n}$ and let $\tilde A_{i,j} \in \mathbb{F}^{(n -1) \times (n-1)}$ be the matrix obtained from $A$ by deleting the $i-$th row and $j-$th column.


**Definition:** Let $A \in \mathbb{F}^{n \times n}$. If $n=1$ so that $A = (a_{1,1})$ we define $\text{det }A = a_{1,1}$. For $n \geq 2$ we define the determinant recursively as $$\text{det }A = \sum_{j=1}^n (-1)^{i+j}a_{i,j}\text{ det }(\tilde A_{i,j})$$
The scalar $(-1)^{i+j} \text{det }(\tilde A_{i,j})$ is called the cofactor of the entry of $A$ in row $i$, column $j$


### Examples

$A = \begin{pmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{pmatrix}$ 

Then $\tilde A_{1,1} = \begin{pmatrix} 5 & 6 \\ 8 & 9 \end{pmatrix}$ , $\tilde A_{1,3} = \begin{pmatrix} 4 & 5 \\ 7 & 8 \end{pmatrix}$ , $\tilde A_{3,2} = \begin{pmatrix} 1 & 3 \\ 4 & 6 \end{pmatrix}$ 



Let $A =  \begin{pmatrix} 1 & 3 & -3 \\ -3 & -5 & 2 \\ -4 & 4 & -6 \end{pmatrix}$

We compute $\text{det }A$ via cofactor expansion along the first row ($i=1$)

$$\text{det }A = (-1)^{2} \cdot 1  \cdot \text{det }\begin{pmatrix} -5 & 2 \\ 4 & -6 \end{pmatrix} + (-1)^{3} \cdot 3 \cdot \text{det }\begin{pmatrix}-3 & 2 \\ -4 & -6 \end{pmatrix} + (-1)^{4}\cdot (-3) \cdot \text{det }\begin{pmatrix} -3 & -5 \\ -4 & 4\end{pmatrix}$$

$\text{det }A = ((-5 \cdot -6) - 2 \cdot 4) + (-1)\cdot 3 \cdot((-3 \cdot -6)-(2 \cdot -4)) + (-3) \cdot ((-3 \cdot 4) - (-5 \cdot -4)) = 40$  



Thus $A$ is invertible. 

$\text{det }A = a_{1,1} \cdot a_{2,2} \cdot ... \cdot a_{n,n}$ if $A$ is triangular. 



We have that $\text{det }I = 1$ Where $I$ is the identity. We can prove this by induction.

Now assume the determinant of the $(n-1)\times(n-1)$ identity $I_{n-1}$ is 1 for some $n \geq 2$. 

Via cofactor expansion along the first row $$\text{det }I_n = (-1)^{1+1}\cdot 1 \cdot \text{det }I_{n-1}+ (-1)^{1+1} \cdot 0 \cdot \text{det }I_n = \text{det }I_{n-1} = 1$$
### Properties 

1. If $A \in \mathbb{F}^{n \times n}$ has a row consisting entirely of zeros, then $\text{det } A=0$, similarly with a column of zeros
2. $A \in \mathbb{F}^{n \times n}, B$ obtained by swapping the rows of $A$ then $\text{det }B= - \text{det }A$
3. $A \in \mathbb{F}^{n \times n}, B$ obtained by scaling row of $A$ by $\lambda \in \mathbb{F}$ then $\text{det }B = \lambda \text{det }A$
4. Elementary operation of type 3 (adding a multiple of a row of $A$ to another) gives $\text{det }B = \text{det }A$
5. $\text{dim range }A = \text{rank }A < n$ implies that $\text{det }A = 0$
6. determinant of a triangular matrix is the product of diagonal entries
7. $\text{det }(A \cdot B) = \text{det }A \cdot \text{det }B$
8. A is invertible $\iff$ $\text{det }A \neq 0$, if $A$ is invertible then $\text{det }A^{-1} = \frac{1}{\text{det }A}$
9. $\text{det }A^\perp = \text{det }A$
10. If $A,B$ are similar (there exists invertible $S$ s.t $B = SAS^{-1}$ ) then $\text{det }A = \text{det }B$
	1. $\text{det }B = \text{det }(SAS^{-1}) = \text{det }S \cdot \text{det }A \cdot \text{det }S^{-1} = \text{det }S \cdot \text{det }A \cdot \frac{1} {\text{det }S} = \text{det }A$ 
11. $\text{det }A = \lambda_1 \cdot ... \cdot \lambda_n$  where $\lambda_k$ is an eigenvalue of $A$ (assuming $\mathbb{F} = \mathbb{C}$), including repeat eigenvalues

#### Cayley-Hamilton Theorem

**Theorem**: Suppose $T \in \mathcal{L}(V)$ and $f$ is the characteristic poly of $T$. Then $f(T) = 0$.

This is shared feature of characteristic individual poly. But these two polys are often the same.


#### Algebraic Multiplicity

**Definition:** Let $\lambda \in \mathbb{F}$ be an eigenvalue of a linear operator or a matrix with characteristic poly $f(\lambda)$. 

The algebraic multiplicity of $\lambda$ is the largest positive integer $k$ such that $(t - \lambda)^k$ is a factor of $f(\lambda)$

**Example:** $A = \begin{pmatrix}3 & 1 & 0 \\ 0 & 3 & 4 \\ 0 & 0 & 4 \end{pmatrix}$


Then $$f(\lambda) = \text{det}(A - \lambda I) = \Bigg | \begin{pmatrix} 3 - \lambda & 1 & 0 \\ 0 & 3 - \lambda & 4 \\ 0 & 0 & 4- \lambda \end{pmatrix} \Bigg|$$ $$ = (3 - \lambda)^2 \cdot (4 - \lambda)$$

Here $\lambda = 3$ has algebraic multiplicity $2, \lambda = 4$ has a multiplicity of $1$


Word of caution: The algebraic multiplicity is distinct from the notion of the geometric multiplicity (The dimension of the eigenspace associated with an eigenvalue $\lambda$).

It can be the case that we do not have enough eigenvectors to match the algebraic multiplicity.


**Example:** Consider $$A = \begin{pmatrix}1 & 1 \\ 0 & 1 \end{pmatrix}$$
The characteristic poly of $A$ is $$f(\lambda) = \text{det}(A -\lambda I) = \Bigg | \begin{pmatrix}1 - \lambda & 1 \\ 0 & 1 - \lambda \end{pmatrix} \Bigg | = (1 - \lambda)^2$$
Then $1$ is the only eigenvalue with algebraic multiplicity. 


Suppose $v = (v_1,v_2)$ is an eigenvector of $A$, I.E $Av = \lambda v = v$


$$V = \begin{pmatrix} v_1 \\ v_2 \end{pmatrix} = Av = \begin{pmatrix}1 & 1 \\ 0 & 1 \end{pmatrix} \begin{pmatrix} v_1 \\ v_2 \end{pmatrix} = \begin{pmatrix} v_1 + v_2 \\ v_2 \end{pmatrix}$$

Implying that $v_1 = v_1+v_2, v_2 = v_2$ so $v_2 = 0$ and $v_1$ can be anything.

Then $v = \begin{pmatrix}1 \\ 0 \end{pmatrix}$ is an eigenvector of $A$. Note that we cannot have another eigenvector that is linearly independent of $\begin{pmatrix}1 \\ 0 \end{pmatrix}$ since $v_2 \equiv 0$

Then $E(\lambda =1, A) = \text{span }\Bigg \{\begin{pmatrix}1 \\ 0 \end{pmatrix} \Bigg \}$
Then $\text{dim }E(1,A) = 1 < 2$

Where $\text{dim }E(1,A)$ is the geometric multiplicity of $\lambda = 1$.


In fact, $A$ is not diagonalizable. Note:

$$A^*A = \begin{pmatrix}1 & 0 \\ 1 & 1 \end{pmatrix}\begin{pmatrix}1 & 1 \\ 0 & 1 \end{pmatrix} = \begin{pmatrix}1 & 1 \\ 1 & 2 \end{pmatrix}$$

And $$AA^* =  \begin{pmatrix}1 & 1 \\ 0 & 1 \end{pmatrix} \begin{pmatrix}1 & 0 \\ 1 & 1 \end{pmatrix}  = \begin{pmatrix}2 & 1 \\ 1 & 1 \end{pmatrix}$$

Note that $A^*A - AA^* \neq 0$ so that $A$ is not normal, $f(\lambda) = (1 - \lambda)^2,p(z)$ is $(1-\lambda)$ or $(1-\lambda)^2$



