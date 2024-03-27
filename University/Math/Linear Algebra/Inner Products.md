# Inner Products
#math 


### Dot product

For $x,y \in \mathbb{R}^n$, the dot product of $x,y$ is denoted by $x \cdot y$, and defined by $$x \cdot y = x_1y_1+...+x_ny_n,$$ where $x = (x_1+...+x_n), y = (y_1+...+y_n)$.

##### Properties

- $x \cdot x \geq 0$ for all $x \in \mathbb{R}^n$
- $x \cdot x = 0$ iff $x = 0$
- For $y \in \mathbb{R}^n$ fixed, the map from $\mathbb{R}^n$ to $\mathbb{R}$ that sends $x \in \mathbb{R}^n$ to $x \cdot y$ is linear
- $x \cdot y = y \cdot x$ for all $x,y \in \mathbb{R}^n$


### Inner Product

Recall that if $\lambda = a+bi, a,b \in \mathbb{R}$ then:
- $|\lambda| = \sqrt{a^2+b^2}$
- $\overline \lambda = a-bi$ 
- $|\lambda|^2 = \lambda \overline \lambda$ 

**Definition:** An inner product on $V$ is a function that takes each ordered pair $(u,v)$ of elements of $V$ to a number $\langle u,v \rangle \in \mathbb{F}$ and has the following properties:

- Positivity: $\langle v,v \rangle \geq 0$ for all $v \in V$
- Definiteness: $\langle v, v\rangle =0$ iff $v = 0$
- Additivity in first slot: $\langle u+v,w \rangle = \langle u,w \rangle + \langle v,w \rangle$ for all $u,v,w \in V$ 
- Homogeneity in the first slot: $\langle \lambda u,v \rangle = \lambda \langle u,v \rangle$ for all $\lambda \in \mathbb{F}, u,v \in V$ 
- Conjugate symmetry: $\langle u,v \rangle = \overline{\langle v,u \rangle}$ for all $u,v \in V$ 


Basic properties of the inner product:

 1. For each fixed $v \in V$, the function that takes $u \in V$ to $\langle u,v \rangle$ is a linear map $V \rightarrow \mathbb{F}$ 
2. $\langle 0,v\rangle = 0$ for all $v \in V$
3. $\langle v,0 \rangle=0$ for all $v \in V$
4. $\langle u,v+w\rangle = \langle u,v\rangle + \langle u,w \rangle$ for all $u,v,w \in V$
5. $\langle u, \lambda v \rangle = \langle \overline \lambda u,v \rangle$ for all $\lambda \in \mathbb{F}, u,v \in V$

**Proof:** 

1. For every $v \in V$, the linearity of $u \rightarrow \langle u,v \rangle$ follows from the conditions of additivity and homogeneity in the first slot in the definition of the inner product
2. Every linear map takes 0 to 0, thus 2 follows from 1
3. If $v \in V$, then the conjugate symmetry property in the definition of an inner product and 2 shows that $\langle v,0 \rangle = \overline{\langle 0,v \rangle} = \overline 0 = 0$ 
4. Suppose $u,v,w \in V$. Then, $$\langle u,v+w \rangle = \overline{\langle v+w,u \rangle}$$$$=  \overline{\langle v,u\rangle + \langle w,u\rangle} = \overline{\langle v,u \rangle}+ \overline{\langle w,u\rangle} = \langle u,v\rangle + \langle  u,w\rangle $$
5. Suppose $\lambda \in \mathbb{F}$ and $u,v \in V$. Then $$\langle u, \lambda v \rangle = \overline{ \langle \lambda v, u\rangle}$$ $$ = \overline{\lambda \langle v,u \rangle} = \overline{\lambda} \overline{\langle v, u \rangle} = \overline{\lambda} \langle u,v \rangle$$

### Norm 

Think of vectors in $\mathbb{R}^2$ or $\mathbb{R}^3$ as arrows pointing from origin. 

The length of a vector $v \in  \mathbb{R}^2$ or $\mathbb{R}^3$ is called the **norm** of $v$ and is denoted by $||v||$.

Thus, for $v  = (a,b) \in \mathbb{R}^2$, we have $$||v|| = \sqrt{a^2+b^2}$$ Similarly, if $v = (a,b,c) \in \mathbb{R}^3$, then $||v|| = \sqrt{a^2+b^2+c^2}$ .


**Definition:** For $v \in V$, the norm $||v||$ is defined by $$||v|| = \sqrt{\langle v,v\rangle}$$

Basic Properties:

1.  $||v|| = 0$ iff $v=0$
2. $||\lambda v|| = {|\lambda|} \text{ } ||v||$ for all $\lambda \in \mathbb{F}$ 


**Proof:** 

1. The desired result holds because $\langle v,v \rangle=0$ iff $v=0$ 
2. Suppose $\lambda \in \mathbb{F}$. Then, $$||\lambda v||^2 = \langle \lambda v, \lambda v\rangle= \lambda \langle v, \lambda v\rangle = \lambda \overline{\lambda} \langle v,v \rangle = |\lambda|^2 \text{ }||v||^2$$
Take the sqrt to find the desired inequality

Working with norms squared is usually easier than working with norms.

### Orthogonality

**Definition:** Two vectors $u,v \in V$ are called orthogonal if $\langle u,v \rangle=0$

#### Orthogonality of 0

**Theorem:** 0 is orthogonal to every vector in $V$, and 0 is the only vector in $V$ that is orthogonal to itself.

**Proof:** Recall that $\langle 0,v \rangle = 0$ for all $v \in V$, and that if $v \in V$ and $\langle v,v \rangle=0$, then $v = 0$ by definition of inner product.

#### Pythagorean Theorem

**Theorem:** Suppose $u,v \in V$. If $u,v$ are orthogonal vectors, then $$||u+v||^2 = ||u||^2+||v||^2.$$
**Proof:** Suppose $\langle u,v \rangle = 0$. Then $||u+v||^2 = \langle u+v,u+v \rangle = \langle u,u \rangle + \langle u,v\rangle + \langle v,u\rangle + \langle v,v \rangle = ||u||^2 + ||v||^2$


##### Orthogonal Decomposition

**Claim:** Suppose $u,v \in V, v \neq 0$. Set $$c = \frac{\langle u,v \rangle}{||v||^2}, w = u - \frac{\langle u,v \rangle}{||v||^2}v$$
Then $u = cv + w$, $\langle w,v \rangle = 0$. 


### Cauchy-Schwarz Inequality

**Claim:** Suppose $u,v \in V$. Then $$|\langle u,v \rangle | \leq ||u||\text{ }||v||.$$ This holds iff $u$ or $v$ is a scalar multiple of the other.

**Proof:** If $v = 0$, then both sides of the inequality equal 0. Thus we can assume that $v \neq 0$. Consider orthogonal decomposition: $$u = \frac{\langle u,v \rangle}{||v||^2}v+w$$ Where $w$ is orthogonal to $v$. By Pythagorean Theorem: $$||u||^2 = \left|\left|\frac{\langle u,v \rangle}{||v||^2}v \right|\right|^2+||w||^2 $$$$= \frac{|\langle u,v \rangle|^2}{||v||^2}v+||w||^2$$ $$\geq \frac{|\langle u,v \rangle|^2}{||v||^2}$$
Multiply both sides by $||v||^2$ to get $$||u||^2 \space ||v||^2 \geq |\langle u,v \rangle|^2$$

We take the square root to get $$|\langle u,v \rangle | \leq ||u||\text{ }||v||.$$

#### Triangle Inequality

**Claim:** Suppose $u,v \in V$. Then $$||u+v|| \leq ||u||+||v||$$
This inequality holds iff one of $u,v$ is a non-negative real multiple of another.

**Proof:** We have $$||u+v||^2 = \langle u+v,u+v \rangle = \langle u,u \rangle + \langle v,v\rangle  + \langle u,v \rangle + \langle v,u \rangle$$
$$$$

#### Parallelogram Inequality

**Claim:** Suppose $u,v \in V$. Then $$||u+v|| \leq ||u|| + ||v||$$

**Proof:** 
## Orthonormality

A list of vectors is called orthonormal if each vector in the list has norm 1 and is orthogonal to all other vectors in the list.

In other words, a list $e_1,...,e_m$ of vectors in $V$ is orthonormal if:

 $$\langle e_j, e_k \rangle = \begin{cases} 1 & j=k \\ 0 & j \neq k \end{cases}$$

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

**Definition:** Suppose $U \subseteq V$ is finite-dimensional. The orthogonal projection of $V$ onto $U$ is $P_u \in \mathcal{L}(V)$ such that for all $v \in V$ where $v = u+w, u \in U, w \in U^\perp$ then $$P_u(v)=u$$

$P_u(v) = \langle v, \frac{u}{||u||}\rangle \cdot \frac{u}{||u||} = \frac{\langle v,u \rangle}{||u||}u = tu$


Here, $P_u(v)$ minimizes $||v-tu||$ over $t \in \mathbb{F}$ 


Basic properties of $P_u$:

1. $P_u \in \mathcal{L}(V,U)$
2. $P_u (u) = u$ for all $u \in U$
3. $P_u (w) = 0$ for all $w \in U^\perp$
4. $\text{range }(P_u ) = U$
5. $\text{null }(P_u ) = U^\perp$
6. $(v - P_u (v)) \in U^\perp$ for all $v \in V$
7. $P_u^2 = P_u$
8. $||P_u (v)|| \leq ||v||$ for all $v \in V$
9. If $\{e_1,...,e_m\}$ is an orthonormal basis for $U$ and $v \in V$ then $P_u (v) = \langle v,e_1\rangle e_1 + ... + \langle v,e_m \rangle e_m$ 

**Proof:**

1. Routine proof, addition, scalar multiplication
   
2. Let $u \in U$. Then $u=u+0$ where $0 \in U^\perp$ . So $P_u(u)=u$ 
   
3. Let $w \in U^\perp$. Then $w = 0+w$ where $0 \in U$. By definition $P_u(w) =0$
   
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