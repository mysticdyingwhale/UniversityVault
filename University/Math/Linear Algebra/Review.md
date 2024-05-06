# Review
#math 


### Solutions of Linear Systems

- Elementary Operations/Matrices
	- Preserve rank $\text{rank}(PAQ) = \text{rank }A$
	- Preserve solutions of $Ax = b$


### Diagonalizability vs Invertibility

| Diagonizability                                                                                  | Invertibility                                                                                                                |
| ------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| There exists an ON basis of $V$ such that $\mathcal{M}(T)$ is diagonal                           | $V$ is finite dimensional, $T \in \mathcal{L}(V)$. Domain and codomain dimensions are equal.                                 |
| Real Spectral Theorem - If $\mathbb F = \mathbb R$ and $T = T^*$ then $T$ is diagonizable        | $T$ is surjective and injective, domain and codomain must have equal dim                                                     |
| Complex Spectral Theorem - If $\mathbb F = \mathbb C$ and $TT^* = T^*T$ then $T$ is diagonizable | $\text{null }T = \{0\}$, $\text{dim range }T = \text{dim }V$ via dimension theorem                                           |
| There exists an ON basis of eigenvectors of $T$ that is a basis for $V$                          | $\sigma_k \neq 0$ for any $k \in \{1,...,n\}$,$\text{dim}(\mathcal{M}(T))\neq 0$, and $\lambda = 0$ not an eigenvalue of $T$ |

If $T$ has $n$ distinct eigenvalues (none are zero) then $T$ is diagonizable.

Since $(\lambda_1,v_1), (\lambda_2,v_2)$ with $\lambda_1 \neq \lambda_2$ is such that $\langle v_1,v_2 \rangle = 0$. 

### Determinants

- $\text{det }A \neq 0$ iff $A$ is invertible.
- Cofactor Expansion can be done along any row or column
- Characteristic Poly $\text{det}(A - \lambda I) = f(\lambda)$
- Roots of $f(\lambda)$ are eigenvalues of $A$
- Characteristic poly and minimal poly may not be the same




### Practice Problems

Q1)

$V  = \mathbb C^3, T \in \mathcal{L}(V)$

$Tv = (0,-v_1,2v_2)$ for $v = (v_1,v_2,v_3)$ 

a) Find $T^*$

Approach 1: Find $T^*$ such that $\langle Tv,w \rangle = \langle v, T^* w\rangle$ 

Approach 2: Look at $\mathcal{M}(T), \mathcal{M}(T^*) = \mathcal{M}(T)^*$ 

Pick std basis:

$T(1,0,0) = (0,-1,0)$ 
$T(0,1,0) = (0,0,2)$
$T(0,0,1) = 0$

$\mathcal{M}(T) = \begin{pmatrix} 0 & 0 & 0 \\ -1 & 0 & 0 \\ 0 & 2 & 0 \end{pmatrix} \implies \mathcal{M}(T^*) = \begin{pmatrix} 0 & -1 & 0 \\ 0 & 0 & 2 \\ 0 & 0 & 0 \end{pmatrix}$

$T^*(v_1,v_2,v_3) = (-v_2, 2v_3, 0)$


b) Find singular values of $T$

$$\mathcal{M}(T^*T) =\mathcal{M}(T^*)\mathcal{M}(T) = \begin{pmatrix} 0 & -1 & 0 \\ 0 & 0 & 2 \\ 0 & 0 & 0 \end{pmatrix} \begin{pmatrix} 0 & 0 & 0 \\ -1 & 0 & 0 \\ 0 & 2 & 0 \end{pmatrix} = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 4 & 0 \\ 0 & 0 & 0 \end{pmatrix}$$
It is diagonal, so the eigenvalues of $T^*T$ are 1,4,0

We take the square roots to get the singular values

$\sigma_1 = \sqrt 4 = 2, \sigma_2 =1, \sigma_3 = 0$


c) Find SVD of $T$


We find the eigenvectors of $T^*T$:

$e_1 = (0,1,0)$ since $\mathcal{M}(T^*T)(0,1,0) = 4(0,1,0)$
$e_2 = (1,0,0)$ since $\mathcal{M}(T^*T)(1,0,0) = 1 (1,0,0)$

Finally,

$f_1 = \frac 1 {\sigma_1}Te_1 = \frac 12 T(0,1,0) = \frac 12 (0,0,2) = (0,0,1)$

$f_2 = \frac{1}{\sigma_2}Te_2 = \frac 11 T(1,0,0) = (0,-1,0)$

Check that $\langle f_1,f_2 \rangle = 0$ and $||f_1|| = 1 = ||f_2||$ (all vectors are orthogonal and have norm of 1)

We now write out the SVD:

$$Tv = \sigma_1 \langle v,e_1 \rangle f_1 + \sigma_2 \langle v,e_2 \rangle f_2 = 2\langle v, (0,1,0) \rangle \begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix} + \langle v,(1,0,0) \rangle \begin{pmatrix} 0 \\ -1 \\ 0 \end{pmatrix}$$

For any $v \in V$


Q2) Let $T \in \mathcal{L}(V)$ where $V = \mathbb F^3$

$\mathcal{M}(T) = A = \begin{pmatrix} 1 & 0 & 1 \\ 1 & 1 & 0 \\ 0 & 1 & 1 \end{pmatrix}$ 


a) If $\mathbb F = \mathbb R$ is $T$ diagonizable?

Approach: Real Spectral Theorem, compute adjoint of $T$


$\mathcal{M}(T^*) = A^T = \begin{pmatrix} 1 & 1 & 0 \\ 0 & 1 & 1 \\ 1 & 0 & 1 \end{pmatrix}$

We see that $T$ is not self-adjoint so that $T$ is not diagonizable by Real Spectral Theorem. 

b) If $\mathbb F = \mathbb C$, does $V$ have an ON basis consisting of eigenvectors of $T$?

Approach: Complex Spectral Theorem, check if $T$ commutes with its adjoint


$$\mathcal{M}(TT^*) =\begin{pmatrix} 1 & 0 & 1 \\ 1 & 1 & 0 \\ 0 & 1 & 1 \end{pmatrix}\begin{pmatrix} 1 & 1 & 0 \\ 0 & 1 & 1 \\ 1 & 0 & 1 \end{pmatrix} = \begin{pmatrix} 2 & 1 & 1 \\ 1 & 2 & 1 \\ 1 & 1 & 2 \end{pmatrix}$$

$$\mathcal{M}(T^*T) =\begin{pmatrix} 1 & 1 & 0 \\ 0 & 1 & 1 \\ 1 & 0 & 1 \end{pmatrix} \begin{pmatrix} 1 & 0 & 1 \\ 1 & 1 & 0 \\ 0 & 1 & 1 \end{pmatrix}= \begin{pmatrix} 2 & 1 & 1 \\ 1 & 2 & 1 \\ 1 & 1 & 2 \end{pmatrix}$$

Since $\mathcal{M}(TT^*) = \mathcal{M}(T^*T)$ we know that $T$ is normal, and thus by Complex Spectral Theorem $T$ is diagonizable. 