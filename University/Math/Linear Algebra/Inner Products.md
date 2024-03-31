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

#### Parallelogram Equality

**Claim:** Suppose $u,v \in V$. Then $$||u+v||^2 + ||u-v||^2  = 2(||u||^2 + ||v||^2)$$

**Proof:** 
