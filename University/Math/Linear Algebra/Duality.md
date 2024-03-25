# Dual Spaces
#math 

**Definition:** The dual space of $V$, denoted by $V'$, is the vector space of all linear transformations $\phi \in \mathcal{L}(V,\mathbb{F})$.

>[!NOTE]
Note that $\text{dim }V' = \text{dim }(\mathcal{L}(V,\mathbb{F})) = \text{dim }V \cdot \text{dim }\mathbb{F} = \text{dim }V$ 


#### Dual Basis

**Claim:** Suppose $\{v_1,...,v_n\}$ is a basis for $V$. For each $j$ define $\phi_j \in \mathcal{L}(V,\mathbb{F})$ by $$\phi_j(v_i) = \begin{cases} 1 & \text{if } i=j \\ 0 & \text{otherwise}\end{cases}$$ Then $\{\phi_1,...,\phi_n\}$ is a basis for $V'$

This is known as the dual basis.

**Proof:** Since $\text{dim }V = \text{dim }V'$ we only need to show that $\phi_j$ are linearly independent.

Suppose $a_1 \phi_1 +...+a_n \phi_n =0$, hen for $v \in V$ we have 
$$(a_1\phi_1 + ... + a_n \phi_n)(v_j) = a_1\phi_1 (v_j) + ... + a_n \phi_n(v_j)$$

$= a_j \phi_j (v_j) = a_j = 0$

For each $j$. Thus $\phi_j$ are linearly independent.


### Dual Map

**Definition:** Suppose $T \in \mathcal{L}(V,W)$. The dual map of $T$ is $T' \in \mathcal{L}(W',V')$ defined for each $\phi \in W'$ by $$T'(\phi) = \phi \cdot T$$
That is, $(T' \phi) v = \phi (Tv)$.