#math 

Suppose $V,W$ are finite dimensional, where $\text{dim }V \geq \text{dim }W \geq 2$.  Show that $A = \{T \in \mathcal{L}(V,W) : \text{T is not surjective}\}$ is not a subspace of $\mathcal{L}(V,W)$

Take some $T_1,T_2 \in A$ such that $T_1+T_2$ is surjective.

$T_1(x,y,z,w) = (x,y,0,0), T_2(x,y,z,w) = (0,0,z,w)$.  

$(T_1+T_2)(x,y,z,w) = (x,y,z,w)$


Given $T,S \in \mathcal{L}(V,W)$ 

Take $\text{range }T, \text{range }S$.

$\text{range }(T+S) = \{(T+S)v : v \in V\}=\{Tv + Sv : v \in V \} \neq \text{range } (T) + \text{range }(S)$   


$T_1 v + T_2 v = (T_1 + T_2)v$, $T : V \rightarrow W$ 






$$(AB)_{j,k} = \sum_l A_{j,l} B_{l,k}$$

Suppose $V$ is fin dim, $T \in \mathcal{L} (V,W)$. Prove there exists a subspace $U \subset V$ such that $U  \cap \text{null}(T) = \{0\}$ and $\text{range }T = \{Tu : u \in U\}$    

Let $w_1,...,w_l$ be a basis of $\text{null }T$.  Extending this basis gives the basis of $V$  $w_1,...,w_l,v_1,...,v_r$. 

Let $U=\text{span}(v_1,...,v_r)$. So, $U \cap \text{null }T = \{0\}$. 

Take $Tu = Ta_1w_1+...+Ta_lw_l+Tb_1v_1+...+Tb_rv_r$

$Ta_1w_1+...+Ta_lw_l = 0$ as these elements are in the null space so each element is 0 when multiplied by $T$, so $Tu = 0 + T(b_1v_1+...+b_rv_r) = T(b_1v_1+...+b_rv_r)  = \text{range }T$. 

So, $\text{range }T = \{Tu : u \in U\}$.   