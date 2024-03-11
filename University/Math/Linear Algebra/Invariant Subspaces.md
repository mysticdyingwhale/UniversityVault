# Invariant Subspaces
#math 

### Invariant Subspaces 

**Definition:** Suppose $T \in \mathcal{L}(V)$. A subspace $U$ of $V$ is called invariant under $T$ if $Tu \in U$ for every $u \in U$.

Thus $U$ is invariant under $T$ if $T|_U$ is an operator on $U$, where an operator is a linear map from a vector space to itself. 

**Examples:** 

### Eigenvalues

**Definition:** Suppose $T \in \mathcal{L}(V)$. A number $\lambda \in \mathbb{F}$ is called an eigenvalue of $T$ if there exists $v \in V$ such that $v \neq 0$ and $Tv = \lambda v$. We call $v$ an eigenvector. $(\lambda,v)$ is an eigenpair

**Example:** Define $T \in \mathcal{L}(\mathbb{F}^3)$ by $$T(x,y,z) = (7x+3z,3x+6y+9z, -6y)$$
for $(x,y,z) \in \mathbb{F^3}$. Then $T(3,1,-1) = (18,6,-6) = 6(3,1,-1)$. Thus 6 is an eigenvalue of $T$. 
