# Characteristic Polynomials
#math 


Recall that for a linear operator $T \in \mathcal{L}(V)$ we have that $v \neq 0$ is an eigenvector of $T$ if $Tv = \lambda v$ for some $\lambda \in \mathbb{F}$. We saw that this is the equivalent to saying that $(T - \lambda I)$ is not invertible and thus has a non-trivial nullspace. 

The following theorem lets us obtain a new method for computing eigenvalues:

**Theorem:** Let $A \in \mathbb{F}^{n \times n}.$ Then a scalar $\lambda$ is an eigenvalue of $A$ if and only if $\text{det}(A - \lambda I) =0$. 

**Proof:** A scalar $\lambda$ is an eigenvalue of $A$ if and only if there exists a non-zero vector $v \in \mathbb{F}^n$ such that $Av = \lambda v$, that is $(A-\lambda I)v = 0$. This is true if and only $A - \lambda I$ is not invertible. However, this result is equivalent to the statement $\text{det}(A - \lambda I) =0$


**Definition:** Let $A \in \mathbb{F}^{n \times n}.$ The polynomial $f(t) = \text{det}(A - \lambda I)$ is called the characteristic polynomial of $A$.

**Examples:**

To find the eigenvalues of $A = \begin{pmatrix}1  &1 \\ 4 & 1 \end{pmatrix}$
we compute its characteristic polynomial

$\text{det}(A - t I) = \text{det} \begin{pmatrix}1-t &1 \\ 4 & 1-t \end{pmatrix} = t^2-2t-3 = (t-3)(t+1)$

Follows from our first theorem that the eigenvalues of $A$ are 3 and -1.

So what separates characteristic poly from minimal poly?


Consider $A \in \mathbb{R}^{3 \times 3}$ such that $A =  \begin{pmatrix}0  &1 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}$

The characteristic polynomial of $A$ is $f(t) = t^3$, but since $A^2 =0$ we have that the [[Polynomials, Invariant Subspaces#Minimal Polynomial|minimal polynomial]] is $p(t)=t^2$.


In a more general case, let $n \geq 2$ be an integer and consider $A = aI_n$ for some $a \neq 0$ such that $a \in \mathbb F$. 

Then clearly the characteristic polynomial of $A$ is $f(t)= (a-t)^n$. 

However, we have $A - aI_n=0$ so that the minimal polynomial of $A$ is $p(t)= t-a$


In general we see that the characteristic poly will be a poly with degree $n$ if $\text{dim }V = n$, whereas the minimal poly can have a smaller degree than $n$.

In fact:
#### Cayley-Hamilton Theorem

**Theorem**: Suppose $T \in \mathcal{L}(V)$ and $f$ is the characteristic poly of $T$. Then $f(T) = 0$.

This immediately implies that the characteristic poly is a polynomial multiple of the minimal poly.

It is often the case, however, that the minimal and characteristic poly are the same.


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



