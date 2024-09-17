
# Rec 5
#math 



Suppose $U,W$ fin dim subspaces of $V$. 

Prove $P_u P_w = 0$ iff $\forall \space u \in U,\forall \space w \in W, \langle u,w \rangle =0$ 


$(\implies)$ Let $w \in W$. Then $P_u P_w w = P_u w = 0$ 

This implies that $w \in U^\perp$, which implies that for all $w \in W, u \in U, \langle u,w \rangle =0$


$(\impliedby)$ $\langle u,w \rangle =0$ implies that $w \in U^\perp$, implying that $W \subseteq U^\perp$. 

Take any $v \in V$ such that $P_uP_w v = P_u(P_w v)$. 

This gives us $P_u \tilde{w}$  where $\tilde w \in W$. 

Since $W \subseteq U^\perp$, $\tilde w \in U^\perp$ so $P_u \tilde w =0$ 

 Therefore $P_uP_w = 0$ .



Suppose $P \in \mathcal{L}(V)$ and $P^2 = P$. Prove $V = \text{null }P \oplus \text{range }P$.


Let $v \in V$. $v = Pv + (v-Pv)$

$Pv \in \text{range P}$. We want to prove that $(v - Pv) \in \text{null }P$ 


$P(v-Pv) = Pv - P^2 v = Pv - Pv = 0$

Therefore $(v-Pv) \in \text{null }P$.

This has shown that $V = \text{range }P + \text{null }P$.

We now must show that $\text{null }P \cap \text{range }P = \{0\}$ 

Let $v \in \text{null }P \cap \text{range }P$. If $v \in \text{null }P$ then $Pv = 0$.

If $v \in \text{range }P$ then for some $w \in V$ $Pw = v, P^2w = Pv, Pw = Pv = 0$

$Pw = v, P^2w = v, P(Pw) = v, P(v) = v$

So $0 = v = Pv$ therefore $\text{null }P \cap \text{range }P = \{0\}$ and $V = \text{range }P \oplus \text{null }P$




Suppose $V$ is fin-dim. $P \in \mathcal{L}(V), P^2 = P$. For all $w \in \text{null }P, u \in \text{range }P$, $\langle w,u \rangle = 0$ 

Prove there exists a subspace $U$ such that $P = P_u$. (LHS is map, RHS is proj onto u)

Assume that $U = \text{range }P$.

We first want to show that for all $u \in U$, $P_u = u$:

There exists $v \in V$ s.t $u = Pv = P^2 v = P(Pv) = P_u$. 

If $v \in V$ then by previous proof $v = n + r$, $n \in \text{null }P, r \in \text{range }P$. Also note that $\text{null }P \subseteq U^\perp$  

This means that $v$ is equal to something in $U$  +  something in $U^\perp$ 

$Pv = P(n+r) = Pn+Pr = r$

Which implies that $P = P_u$



Suppose $u,v \in V$. Prove that $\langle u,v \rangle = 0$ iff for all $a \in \mathbb{F}$, $||u||^2 \leq ||u +av||^2$ 

($\implies$) $\langle u,v \rangle =0 \implies \langle u,av \rangle = 0$. 

his implies that $||u+av||^2 = ||u||^2 + |a|^2||v||^2 \geq ||u||^2$ 

$\impliedby$ Suppose $||u||^2 \leq ||u+av||^2$ 

So $0 \leq ||u+av||^2 - ||u||^2$

$0 \leq \langle u+av, u+av \rangle - \langle u,u \rangle$

$0 \leq \langle u,u \rangle + \langle av,u \rangle + \langle u,av \rangle + |a|^2 \langle v,v \rangle - \langle u,u \rangle$ 


$0 \leq \langle av,u \rangle + \langle u,av \rangle + |a|^2 \langle v,v \rangle$ 

$0 \leq a \overline{\langle u,v \rangle} + \overline a \langle u,v \rangle + |a|^2 \langle v,v \rangle$

By way of contradiction suppose that $\langle u,v \rangle \neq 0$ 


Ansatz: $a = - \frac{\langle u,v \rangle}{\langle v,v \rangle}$ and $v \neq 0$

$-\frac{\langle u,v \rangle \overline {\langle u,v \rangle}}{||v||^2} - \frac{\overline {\langle u,v \rangle}\langle u,v \rangle }{||v||^2} + \frac{|\langle u,v \rangle | ^2}{||v||^2}||v||^2$

$= \frac{- |\langle u,v \rangle |^2}{||v||^2}$ 
