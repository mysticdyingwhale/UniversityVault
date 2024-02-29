#math 
# Invertibility

**Definition:** Let $T \in \mathcal{L}(V,W)$. We say that $T$ is invertible if there exists an $S \in \mathcal{L}(V,W)$ such that $$S(T(v))= v$$ for all $v \in V$, and $$S(T(w))=w$$ for all $w \in W$. 

I.E,  $ST = I$ on $V$, $TS = I$ on $W$. We call $S$ the **inverse** of $T$


**Claim:** The inverse is unique.

**Proof:** Let $S, \tilde{S} \in \mathcal{L}(W,V)$ be inverses of $T$. Then for $w \in W$, $S(w)=S \circ (T \circ \tilde{S}(w)) = (S \circ T)(\tilde{S}(w))$ .

This indicates $S = \tilde{S}$, since $S(w) = \tilde{S}(w)$ for all $w \in W$. 


>[!NOTE] 
>We typically write $T^{-1}$ to note the inverse of $T$. 

**Claim:** A linear map is invertible if and only if it is injective (one-to-one) and surjective (onto).

**Proof:** ($\implies$) Let $T \in \mathcal{L}(V,W)$ be invertible. 

**Injectivity:** Let $u,v \in V$ such that $T(u) = T(v)$. 

$u  = I(u) = T^{-1}(T(u)) = T^{-1}(T(v))=I(v)=v$  

Therefore, $T$ is one-to-one.

**Surjectivity:** Let $w \in W$. Then $w = I(w) = T(T^{-1}(w))$ so that $w \in \mathcal{R}(T)$. 

Since $T^{-1}(w) \in V$ such that $T(T^{-1}(w))=w$. Therefore $\mathcal{R}(T)= W$ and $T$ is onto. 