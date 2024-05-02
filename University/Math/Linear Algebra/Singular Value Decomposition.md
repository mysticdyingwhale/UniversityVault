# Singular Value Decomposition
#math 


### Properties of $T^*T$ 

**Claim:** Suppose $T \in \mathcal{L}(V,W)$, then

1. $T^*T$ is a positive operator on $V$
2. $\text{null}(T^*T) = \text{null }T$
3. $\text{range}(T^*T) = \text{range }T^*$
4. $\text{dim range }T = \text{dim range }T^* = \text{dim range}(T^*T)$

**Proof:** $\text{dim range }T = \text{dim null}((T^*))^\perp = \text{dim }W - \text{dim null}(T^*) = \text{dim range }T^*$

Since $\text{range }T^* = \text{range }T^*T \implies \text{dim range }T^* = \text{dim range}(T^*T)$

## Singular Values


**Definition:** Let $T \in \mathcal{L}(V,W)$. The singular values of $T$ are the non-negative square roots of eigenvalues of $T^*T$, listed in decreasing order. 

Each singular value is listed as many times as the dimension of the corresponding eigenspace of $T^*T$. 

**Example:** $T(z_1,z_2,z_3,z_4) = (0,3z_1,2z_2,-3z_4)$

We have $T^*T(z_1,z_2,z_3,z_4) = (9z_1,4z_2,0,9z_4)$

Then $\{e_1,...,e_n\}$ diagonalizes $T^*T \implies$ eigenvalues are $9,4,0$.

$\text{dim}(E_9)=2, \text{dim}(E_4)=1, \text{dim }(E_0)=1$


Then singular values are $\sigma_1 = 3, \sigma_2 = 3, \sigma_3 = 1, \sigma_4 = 0$

However $T$ only has eigenvalues $-3, 0$


#### Role of Singular Values


**Claim:** Suppose $T \in \mathcal{L}(V,W)$. Then:

1. $T$ is injective $\iff$ 0 is not a singular value of $T$
2. Number of positive singular values  = $\text{dim range }T$
3. $T$ is surjective $\iff$ $\text{dim }W =$ number of singular values

**Proof:** 

1. $T$ is injective $\iff$ $\text{null }T = \{0\}$
	$\iff \text{null }T^*T = \{0\}$
	$\iff$ 0 is not an eigenvalue of $T^*T$


2. Since $T^*T$ is positive, [[Spectral Theorem, Positive Operators|spectral theorem]] gives $\text{dim range}(T^*T) =$ number of positive eigenvalues of $T^*T$ (counting repetitions). Since $\text{dim range }T= \text{dim range}(T^*T)$ we get the result

3. $T$ is surjective $\iff$ $\text{dim range }T = \text{dim }W$
	$\iff \text{dim range }(T^*T) = \text{dim }W$
	$\iff \text{dim }W =$ number of positive singular values


**Claims:** Suppose $S \in \mathcal{L}(V,W)$. Then $S$ is an [[Isometries, Unitary Operators|isometry]] if and only if all singular values of $S$ are 1.


**Proof:** $S$ is an isometry $\iff S^*S = I$
	$\iff$ all eigenvalues of $S = I$
	$\iff$ all singular values of $S$ 

## Singular Value Decomposition

**Definition:** Suppose $T \in \mathcal{L}(V,W)$ and the positive singular values of $T$ are $\sigma_1,...,\sigma_m$. Then there exists orthonormal lists $e_1,..,e_m \in V, f_1,...,f_m \in W$ such that $$Tv = \sigma_1 \langle e_1,v \rangle f_1 + ... + \sigma_m \langle e_m, v \rangle f_m$$

**Proof:** Let $\sigma_1,...,\sigma_n$ be the singular values of $T$. Since $T^*T$ is positive, spectral theorem implies that there exists some orthonormal basis $\{e_1,...,e_n\}$ such that $$T^*Te_k = \sigma_k^2e_k.$$

Let $f_k= \frac {Te_k} {\sigma_k}$ . Then if $1 \leq $

## Consequences and Geometry


### Unit Ball

### Determinants

$\text{det }T =$ product of singular values. 

That is, $\text{det }T$ measures how you magnify the volume of the unit ball under $T$.

If any singular value is 0, then $T$ is not invertible so the area goes to zero.