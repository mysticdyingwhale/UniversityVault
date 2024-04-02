# Orthonormality
#math 

A list of vectors is called orthonormal if each vector in the list has norm 1 and is orthogonal to all other vectors in the list.

In other words, a list $e_1,...,e_m$ of vectors in $V$ is orthonormal if:

 $$\langle e_j, e_k \rangle = \begin{cases} 1 & j=k \\ 0 & j \neq k \end{cases}$$


### Norm of orthonormal linear combination

**Claim:** Suppose $e_1,...,e_m$ is an orthonormal list of vectors in $V$. Then $$||a_1e_1+...+a_me_m||^2 = |a_1|^2+...+|a_m|^2$$
for all $a_1,...,a_m \in \mathbb{F}$ 

(6.24)

**Proof:** Since each $e_k$ has norm 1, this follows from application of the Pythagorean theorem.


#### Orthonormal lists are linearly independent 

**Claim:** every orthonormal list is linearly independent

**Proof:** Suppose $e_1,...,e_m$ is an orthonormal list of vectors in $V$ and $a_1,...,a_m \in \mathbb{F}$ are such that $$a_1e_1+...+a_me_m = 0.$$ Then, $|a_1|^2+...+|a_m|^2=0$ by 6.24


#### Bessel's Inequality

**Claim:** Suppose $e_1,...,e_m$ is an orthonormal list of vectors in $V$. If $v \in V$ then $$|\langle v,e_1 \rangle |^2+...+|\langle v,e_m \rangle |^2 \leq ||v||^2$$

**Proof:** Suppose $v \in V$. Then $$v = \langle v,e_1\rangle e_1+...+\langle v,e_m \rangle e_m + v-  \langle v,e_1 \rangle e_1 - ... - \langle v,e_m \rangle e_m$$
Let $u = \langle v,e_1\rangle e_1+...+\langle v,e_m \rangle e_m, w = v-  \langle v,e_1 \rangle e_1 - ... - \langle v,e_m \rangle e_m$ such that $v = u+w$. 

If $k \in \{1,...,m\}$ then $\langle w,e_k \rangle = \langle v,e_k \rangle -\langle v,e_k \rangle \langle e_k, e_k \rangle = 0.$ 

This implies that $\langle w,u \rangle= 0$.  Since $w,u$ are orthogonal we can now apply the Pythagorean theorem to find:

$$||v||^2 = ||u||^2 + ||w||^2\geq ||u||^2$$
So $$||u||^2 = |\langle v,e_1 \rangle|^2+...+|\langle v,e_m \rangle |^2$$ by 6.24.

#### Writing a vector as a linear combination of an orthonormal basis

Suppose $e_1,...,e_n$ is an orthonormal basis of $V$ and $u,v \in V$. Then:

1. $v = \langle v,e_1 \rangle e_1+...+\langle v,e_m \rangle e_m$
2. $||v||^2 = |\langle v,e_1 \rangle |^2 + ... + |\langle v,e_m \rangle |^2$
3. $\langle u,v \rangle = \langle u,e_1 \rangle \overline{\langle v,e_1 \rangle} +... + \langle u,e_m \rangle \overline{\langle v,e_m \rangle}$


**Proof:**

### Orthonormal Basis

**Definition:** An orthonormal basis of $V$ is an orthonormal list of vectors in $V$ that is also a basis of $V$.


#### Orthonormal lists of right length are orthonormal bases

**Claim:** Suppose $V$ is fin-dim. Then every orthonormal list of vectors in $V$ of length $\text{dim }V$ is an orthonormal basis of $V$.

**Proof:** Every orthonormal list of vectors is linearly independent .

### Inner Product Space

An Inner product space is a vector space $V$ along with an inner product on $V$. 

We say a vector space $V$ equipped with an inner product $\langle .,. \rangle : V \times V \rightarrow \mathbb{F}$ is an inner product space. This lets us generalize a notion of analysis between vectors.

In particular, we say $x,y \in V$ are orthogonal if $\langle x,y \rangle=0$. Inner products produce a norm: $$||x||= \sqrt{\langle x,x \rangle}$$
#### Orthogonal Complement
**Definition:** If $U \subseteq V$ is a subspace of $V$, we say $U^{\perp}$ is the orthogonal complement of $U$.

$$U^{\perp} = \{v \in V | \langle u,v \rangle = 0 \space \forall \space  u \in U \}$$

Basic Properties:

1. $U^{\perp} \subseteq V$ is a subspace of $V$
2. $\{0\}^\perp = V$
3. $V^\perp = \{0\}$
4. $U \cap U^\perp = \{0\}$
5. If $U \subset W$ then $W^\perp \subseteq U^\perp$


**Proof:**

1. Since $\langle 0,v \rangle =0$ for every $v \in V$, $0 \in U^\perp$. 

	If $v,w \in U^\perp$, $\alpha \in \mathbb{F}, u \in U$, then $\langle \alpha v+w, u \rangle = \alpha \langle v,u \rangle + \langle w,u \rangle = \alpha \cdot 0 + 0 = 0$. So, $(\alpha v+w) \in U^\perp$ 

2. .
3. If $\langle u,v \rangle = 0$ for every $v \in V$ then $u=0$.
4. Suppose $u \in U \cap U^\perp$, then $\langle u,u^\perp \rangle = 0 = ||u||$, which implies that $u \equiv 0$  
5. Suppose $v \in W^\perp, \langle v,w \rangle = 0$ for every $w \in W$. Then $\langle v,u \rangle = 0$ for every $u \in U$. Since $U \subset W$, then $v \in U^\perp$. 



#### V is direct sum of subspace and its orthogonal complement

**Theorem:** Suppose $U$ is a fin-dim subspace of $V$. Then $V = U \oplus U^\perp$ 

**Proof:** Let $v \in V$ and $\{e_1,...,e_m\}$ be an orthonormal basis of $U$. Then $$V = \langle v,e_1\rangle e_1+...+\langle v,e_m \rangle e_m + (v-\langle v,e_1\rangle e_1 - ... - \langle v,e_m \rangle e_m)$$
Set $w =  (v-\langle v,e_1\rangle e_1 - ... - \langle v,e_m \rangle e_m)$ and $u = \langle v,e_1\rangle e_1+...+\langle v,e_m \rangle e_m$ 

Clearly $u  \in U$. Now, $$\langle w,e_k \rangle = \langle (v-\langle v,e_1\rangle e_1 - ... - \langle v,e_m \rangle e_m), e_k$$$$= \langle v, e_k \rangle - \langle \langle v,e_1 \rangle e_1, e_k \rangle - ... - \langle \langle v, e_m \rangle e_m, e_k \rangle$$ $$ = \langle v,e_k \rangle - \langle v,e_1 \rangle \langle e_1, e_k \rangle -...-\langle v,e_m \rangle \langle e_m, e_k \rangle$$ $$ = \langle v,e_k \rangle - \langle v,e_k \rangle \langle e_k, e_k \rangle$$
$$ = \langle v,e_k \rangle - \langle v,e_k \rangle = 0$$

So that $w$ is orthogonal to every vector in $\text{span }\{e_1,...,e_m\} = U$. by definition, $w \in U^\perp$. Since $v = u+w$ where $u \in U$ and $w \in U^\perp$ we have $V = U+U^\perp$. 

Since $U \cap U^\perp =\{0\}$ we have $V = U \oplus U^\perp$ as desired. 

**Corollary:** $\text{dim }U^\perp = \text{dim }V - \text{dim }U$


#### Orthogonal Complement of Orthogonal Complement

**Lemma:** If $U$ is finite dimensional, $(U^\perp)^\perp = U$. 

**Proof:** Let $u \in U$. Then $\langle u,w \rangle = 0$ for every $w \in U^\perp$. Since $u$ is orthogonal to $U^\perp$, $u \in (U^\perp)^\perp$, which implies that $U \subseteq (U^\perp)^\perp$. 

Now suppose $v \in (U^\perp)^\perp$. We can write $v = u+w, u \in U, w \in U^\perp$. 

Then, $w = v - u \in U^\perp$. Since $v,u \in (U^\perp)^\perp$  we have $w \in (U^\perp)^\perp$. 

Then $w \in U^\perp \cap (U^\perp)^\perp = \{0\}$ so that $w = 0$. Then $v = u$ implies that $v \in U$. 

Then $v \in (U^\perp)^\perp \subseteq U$. So $U = (U^\perp)^\perp$ 




#### No orthogonal complement means U=V

**Theorem:** Suppose $U$ is a fin-dim subspace of $V$. Then $U^\perp = \{0\}$ if and only if $U=V$

**Proof:** ($\implies$) Suppose $U^\perp = \{0\}$. Then $U = (U^\perp)^\perp = (\{0\})^\perp = V$ 

($\impliedby$) If $U = V$ then $U^\perp = V^\perp = \{0\}$ 


### Orthogonal Projection

**Definition:** Suppose $U \subseteq V$ is finite-dimensional. The orthogonal projection of $V$ onto $U$ is $P_U \in \mathcal{L}(V)$ such that for all $v \in V$ where $v = u+w, u \in U, w \in U^\perp$ then $$P_U(v)=u$$

$P_U(v) = \langle v, \frac{u}{||u||}\rangle \cdot \frac{u}{||u||} = \frac{\langle v,u \rangle}{||u||}u = tu$


Here, $P_U(v)$ minimizes $||v-tu||$ over $t \in \mathbb{F}$ 


Basic properties of $P_u$:

1. $P_U \in \mathcal{L}(V,U)$
2. $P_U (u) = u$ for all $u \in U$
3. $P_U (w) = 0$ for all $w \in U^\perp$
4. $\text{range }(P_U) = U$
5. $\text{null }(P_U) = U^\perp$
6. $(v - P_U(v)) \in U^\perp$ for all $v \in V$
7. $(P_U)^2 = P_U$
8. $||P_U (v)|| \leq ||v||$ for all $v \in V$
9. If $\{e_1,...,e_m\}$ is an orthonormal basis for $U$ and $v \in V$ then $P_U (v) = \langle v,e_1\rangle e_1 + ... + \langle v,e_m \rangle e_m$ 

**Proof:**

1. Routine proof, addition, scalar multiplication
   
2. Let $u \in U$. Then $u=u+0$ where $0 \in U^\perp$ . So $P_U(u)=u$ 
   
3. Let $w \in U^\perp$. Then $w = 0+w$ where $0 \in U$. By definition $P_U(w) =0$
   
4. By definition $\text{range }(P_u) \subseteq U$. Since $u = P_u(u)$ for all $u \in U$ we also have $u \in \text{range }(P_u)$ so that $u \in \text{range }(P_u)$.
   
5. We have $U^\perp \subseteq \text{null }(P_u)$ by 3. If $v \in \text{null }(P_u)$ then $v = 0+v$ where $0 \in U, v \in U^\perp$ so that  $\text{null }(P_u) \subseteq U^\perp$
   
6. If $v \in V$ and $v = u+w$ where $u \in U, w \in U^\perp$ then $v - P_u(v) = v-u=w \in U^\perp$ 
   
7. If $v \in V$ and $v = u+w$ ($u \in U, w \in U^\perp$) then $P_u^2(v) = P_u(P_u(v)) = P_u(u) = u = P_u(v)$ for every $v \in V$. Then $P_u^2 = P_u$
   
8. If $v \in V, v = u+w$ ($u \in U, w \in U^\perp$)
   
    $||P_u(v)||^2 = ||u||^2 \leq ||u||^2 + ||w||^2 = ||u+w||^2 = ||v||^2$ (Pythagorean Theorem). 
    
    Taking square roots gives $||P_u(v)|| \leq ||v||$ for all $v \in V$
    
9. We have for any $v \in V$ $v = u+w = (\langle v,e_1 \rangle e_1 + ...+ \langle v,e_m \rangle e_m) + (v- \langle v,e_1 \rangle e_1 - ... - \langle v, e_m \rangle e_m)$. Then $P_u(v) = u = \langle v,e_1 \rangle e_1 + ...+ \langle v,e_m \rangle e_m$



**Theorem:** Suppose $U \subseteq V$ is fin-dim. Let $v\in V, u \in U$. Then $$||v - P_u(v)|| \leq ||v-u||,$$
with equality if and only if $u = P_u(v)$. 

In other words, the closest point in $U$ to $v$ is $P_u(v)$

**Proof:** $$||v-P_u(v)||^2 \leq ||v - P_u(v)||^2 + ||P_u(v) -u||^2$$ $$= ||v - P_u(v)+P_u(v)-u||^2$$ (By Pythagorean Theorem)
 $$= ||v-u||^2$$


With equality if and only if $P_u(v)=u$




