# Isometries & Unitary Operators
#math 

## Isometries

**Definition:** $S \in \mathcal{L}(V,W)$ is an isometry if $||Sv|| = ||v||$ for all $v \in V$.

Note that if $Sv = 0$ and $S$ is an isometry then $||v|| = ||Sv|| = 0 \implies v = 0 \implies S$ is injective


**Examples:**

$A = \begin{bmatrix} sin \theta  & cos \theta  \\ -cos \theta & sin \theta \end{bmatrix}, \theta \in [0,2\pi)$ 

Then $$\bigg|\bigg|A \begin{pmatrix}x \\ y\end{pmatrix}\bigg|\bigg|^2 = ||(xsin\theta + y cos \theta, -x cos\theta + y sin \theta)||^2$$$$= (xsin\theta + ycos \theta)^2 + (-xcos\theta+ysin\theta)^2 = x^2+y^2 = ||(x,y)||^2$$
So that $T \begin{pmatrix}x \\ y\end{pmatrix} = A  \begin{pmatrix}x \\ y\end{pmatrix}$ is an isometry. 

Note that $A^*A = \begin{bmatrix} sin \theta  & -cos \theta  \\ cos \theta & sin \theta \end{bmatrix} \begin{bmatrix} sin \theta  & cos \theta  \\ -cos \theta & sin \theta \end{bmatrix} = I$.

So, columns of $A$ are orthonormal. More generally, suppose $A\in \mathbb{F}^{m \times n}$ and $A^*A =I$ ($A$ has orthonormal columns). Then $$||Av|| = \langle Av,Av \rangle = \langle A^*Av, v\rangle = ||v||^2$$

#### Characterization of Isometries

**Claim**: Let $S \in \mathcal{L}(V,W)$, $\{e_1,...,e_n\}$ an ON basis of $V$, $\{f_1,...,f_m\}$ an ON basis of $W$. The following are equivalent:

1. $S$ is an isometry
2. $S^*S = I$
3. $\langle Su,Sv \rangle = \langle u,v \rangle$ for all $u,v \in V$
4. $Se_1,...,Se_n$ is an ON list in $W$
5. The columns of $\mathcal{M}(S, \{e_1,...,e_n\}, \{f_1,...,f_m\})$ form an ON list in $\mathbb{F}^m$ with Euclidean Inner Product

**Proof:**  ($1 \implies 2$) Suppose $S$ is an isometry. If $v \in V$ then $\langle (I - S^*S)v,v \rangle = \langle v,v   \rangle - \langle S^*S v, v \rangle = ||v||^2 - ||Sv||^2 = 0$ 


Therefore since $I - S^*S$ is self-adjoint we have $I-S^*S = 0 \implies S^*S = I$ 

$(2 \implies 3)$ Suppose $S^*S = I$. If $u,v \in V$ then $\langle Su,Sv \rangle = \langle u, S^*Sv \rangle =\langle u,v \rangle$ 

$(3 \implies 4)$ Suppose $\langle Su,Sv  \rangle = \langle u,v \rangle$ for all $u,v \in V$, Then $\langle Se_j, Se_k \rangle  = \langle e_j,e_k \rangle = \begin{cases} 1 & j=k \\ 0 & j \neq k \end{cases}$
So that $\{Se_j\}_{j=1}^n$ is an orthonormal list in $W$. 

$(4 \implies 5)$ Suppose $\{Se_j\}_{j=1}^u$ is an orthonormal list in $W$. Let $A = \mathcal{M}(S, \{e_1,...,e_n\}, \{f_1,...,f_m\})$ If $k,v \in \{1,...,n\}$ then $$\sum_{j=1}^m A_{j,k}\overline {A_{j,v}} = \langle \sum_{j=1}^m A_{j,k}f_j,\sum_{j=1}^m A_{j,v}f_j \rangle = \langle Se_k, Se_j \rangle =  \begin{cases} 1 & j=k \\ 0 & j \neq k \end{cases}$$
Thus columns of $A$ are orthonormal in $\mathbb{F}^m$ 

$(5 \implies 1)$ Suppose columns of $A$ form on orthonormal list in $\mathbb{F}^n$. Previous proof shows that $Se_1, ..., Se_n$ is an orthonormal list in $W$. We can view the map $S$ as taking $e_k$ to the $k-$th column of $A$.

Let $v \in V$. then $$v = \langle v,e_1 \rangle e_1 + ... + \langle v,e_n \rangle e_n$$ and $||v||^2 = |\langle v,e_1 \rangle|^2 + ... + |\langle v,e_n \rangle|^2$. 

Applying $S$ (if $A_j$ is the $j-$th column of $A$) gives $$Sv = \langle v,e_1 \rangle Se_1 + ... + \langle v,e_n \rangle Se_n = \langle v,e_1 \rangle A_1 + ... + \langle v,e_n \rangle A_n$$
where $||Sv||^2 = |\langle v,e_1 \rangle|^2 + ... + |\langle v,e_n \rangle|^2 = ||v||^2$ so that $S$ is an isometry.


We have shown (among other things) that isometries are **normal** operators. By [[Spectral Theorem, Positive Operators#Complex Spectral Theorem|Complex Spectral Theorem]] if $\mathbb{F} = \mathbb C$ there exists a basis of eigenvectors of $T$. Suppose $Tv  = \lambda v$. Then $$\frac{||Tv||^2}{||v||^2} = \frac{\langle Tv,Tv \rangle}{||v||^2} = \frac{\lambda \overline \lambda \langle v,v\rangle}{||v||^2} = |\lambda|^2 = 1$$
## Unitary

**Definition:** $S \in \mathcal{L}(V)$ is unitary if $S$ is an invertible isometry.


**Note:** The distinction between isometry and unitary is that a unitary operator maps a vector space to itself.

**Remark:** If $T$ positive analogous to a positive real number, then $U$ unitary is such that $U^*U = I$ which is analogous to $z \in \mathbb{C}$ such that $|z| = 1$  (i.e unit circle in $\mathbb{C}$) 


### Properties

Many of the properties of Isometries carry over to unitary matrices. 