# Isometries & Unitary Operators
#math 



## Isometries

**Definition:** $S \in \mathcal{L}(V,W)$ is an isometry if $||Sv|| = ||v||$ for all $v \in V$.

Note that if $Sv = 0$ and $S$ is an isometry then $||v|| = ||Sv|| = 0 \implies v = 0 \implies S$ is injective


**Examples:**


#### Charecterization of Isometries

**Claim**: Let $S \in \mathcal{L}(V,W)$, $\{e_1,...,e_n\}$ an ON basis of $V$, $\{f_1,...,f_m\}$ an ON basis of $W$. The following are equivalent:

1. $S$ is an isometry
2. $S^*S = I$
3. $\langle Su,Sv \rangle = \langle u,v \rangle$ for all $u,v \in V$
4. $Se_1,...,Se_n$ is an ON list in $W$
5. The columns of $\mathcal{M}(S, \{e_1,...,e_n\}, \{f_1,...,f_m\})$ form an ON list in $\mathbb{F}^m$ with Euclidean Inner Product

**Proof:** 




## Unitary

**Definition:** $S \in \mathcal{L}(V)$ is unitary if $S$ is an invertible isometry.


**Note:** The distinction between isometry and unitary is that a unitary operator maps a vector space to itself.

**Remark:** If $T$ positive analogous to a positive real number, then $U$ unitary is such that $U^*U = I$ which is analogous to $z \in \mathbb{C}$ such that $|z| = 1$  (i.e unit circle in $\mathbb{C}$) 


### Properties

Many of the properties of Isometries carry over to unitary matrices. 