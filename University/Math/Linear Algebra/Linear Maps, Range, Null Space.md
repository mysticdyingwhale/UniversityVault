#math 

# Linear Maps


**Definition:** Let $V,W$ be vector spaces over the field $\mathbb{F}$. A function $V \rightarrow W$ is said to be a linear map if any two vectors $u,v \in V$ and any scalar $\lambda \in \mathbb{F}$ meet the following conditions:
- $T(u+v) = T(u) + T(v)$ for all $u,v \in V$ (Additivity)
- $T(\lambda v) = \lambda T(v)$ for all $\lambda \in \mathbb{F}, v \in V$ (Homogeneity)

>[!NOTE]
>For linear maps, $T(v)$ is the same as $Tv$


The set of linear maps from $V$ to $W$ is denoted by $\mathcal{L}(V,W)$.

The set of linear maps from $V$ to $V$ is denoted by $\mathcal{L}(V)$, essentially $\mathcal{L}(V) = \mathcal{L}(V,V)$

#### Examples

- Zero
	- We let the $0$ symbol denote the linear map that takes every element of some vector space to the additive identity of another (or possibly the same) vector space. 
	- To be specific, $0 \in \mathcal{L}(V,W)$ is defined by $0v = 0$.
	- $0$ on the left side is a function from $V$ to $W$, whereas the $0$ on the right side is the additive identity in $W$. 
	- Distinguish $0$ by context.
	  
- Identity Operator
	- The identity operator, denoted by $I$, is the linear map on some vector space that takes each element to itself. 
	- To be specific, $I \in \mathcal{L}(V)$ is defined by $Iv = v$.
	  
- Differentiation
	- Define $D \in \mathcal{L}(P(\mathbb{R}))$ by $Dp = p'$.
	- The assertion that this function is a linear map is another way of stating a basic result about differentiation: 
		- $(f+g)' = f' + g'$, and $(\lambda f)' = \lambda f'$ whenever $f$ and $g$ are differentiable and $\lambda$ is a constant.
	  
- Integration
	- Define $T \in \mathcal{L}(P(\mathbb{R}),\mathbb{R})$ by $Tp = \int_0^1 p$ 
	- The assertation that this function is a linear map is another way of stating a basic result about integration:
		- The integral of the sum of two functions equals the sum of the integrals 
		- The integral of a constant times a function equals the constant times the integral of the function.
		  
- Multiplication by $x^2$
	- Define a linear map $T \in \mathcal{L}(P(\mathbb{R}))$ by:
		- $(Tp)(x) = x^2p(x)$ for each $x \in \mathbb{R}$ 


### Linear Map Lemma

Suppose $v_1,...,v_n$ is a basis of $V$ and $w_1,...,w_n \in W$. 

Then there exists a unique linear map $T : V \rightarrow W$ such that $$Tv_k = w_k$$ for each $k = 1,...,n$.

**Proof:** First we show the existence of a linear map $T$ with the desired property.

Define $T : V \rightarrow W$ by $$T(c_1v_1+...+c_nv_n) = c_1w_1+...+c_nw_n,$$ where $c_1,...,c_n$ are arbitrary elements of $\mathbb{F}$. The list $v_1,...,v_n$ is a basis of $V$. 

Thus the equation above does indeed define a function $T$ from $V$ to $W$, because each element of $V$ can be uniquely written in the form $c_1v_1+...+c_nv_n$. 

For each $k$, taking $c_k=1$ and the other $c$ equal to $0$ in the equation above shows that $Tv_k = w_k$. 

If $u,v \in V$ with $u=a_1v_1+...+a_nv_n$ and $v = c_1v_1 + ... +c_nv_n$, then $$T(u+v) = T((a_1+c_1)v_1+...+(a_n+c_n)v_n)$$$$=(a_1+c_1)w_1+...+(a_n+c_n)w_n$$
$$= (a_1w_1+...+a_nw_n)+(c_1w_1+...+c_nw_n) = Tu+Tv$$

Similarly if $\lambda \in \mathbb{F}$ and $v = c_1v_1+ ... +c_nv_n$, then $$T(\lambda v) = T(\lambda c_1v_1+...+\lambda c_nv_n)$$ $$= \lambda c_1w_1+...+\lambda c_n w_n$$ $$=\lambda(c_1w_1+...+c_nw_n)$$ $$= \lambda Tv$$
Thus $T$ is a linear map from $V$ to $W$.

To prove uniqueness, we suppose that $T \in \mathcal{l}(V,W)$ and that $Tv_k = w_k$ for each $k=1,...,n$.  Let $c_1,...,c_n \in \mathbb{F}$. Then the homogeneity of $T$ implies that $T(c_kv_k) = c_kw_k$ for each $k=1,...,n$. 

The additivity of $T$ now implies that $$T(c_1v_1+...+c_nv_n)=c_1w_1+...+c_nw_n.$$
Thus, $T$ is uniquely determined on $\text{span}(v_1,...,v_n)$ by the equation above. Because $v_1,...,v_n$ is a basis of $V$, this implies that $T$ is uniquely determined on $V$, as desired.
### Addition and Scalar Multiplication

Suppose $S,T \in \mathcal{L}(V,W)$ and $\lambda \in F$. The sum $S+T$ and the product $\lambda T$ are linear maps defined from $V$ to $W$ defined by $(S+T)(v) = Sv+Tv$ and $(\lambda T)(v) = \lambda(Tv)$ for all $v \in V$. 


With the operations of addition and scalar multiplication defined above, $\mathcal{L}(V,W)$ is a vector space.


### Algebraic Properties of linear maps

**Associativity:** $(T_1 T_2)T_3 = T_1(T_2 T_3)$ whenever $T_1, T_2,T_3$ are linear maps such that their products make sense ($T_3$ maps into the domain of $T_1$, and $T_2$ maps into the domain of $T_1$)

**Identity:** $TI = IT = T$ when $T \in \mathcal{L}(V,W)$. Here, the first $I$ is the identity operator on $V$, and the second is the identity operator on $W$.

**Distributive Properties:** $(S_1 + S_2)T = S_1 T + S_2 T$ and $S(T_1+T_2) = ST_1 + ST_2$ whenever $T, T_1, T_2 \in \mathcal{L}(U,V)$ and $S,S_1,S_2 \in \mathcal{L}(V,W)$. 



#### Zero

(3.10)
**Definition:** Suppose $T$ is a linear map from $V$ to $W$. Then $T(0)=0$

**Proof:** By Additivity we have $T(0) = T(0+0) = T(0)+T(0)$. 

Adding the additive inverse to of $T(0)$ to each side we get $T(0)+(-T(0)) = T(0)+T(0)+(-T(0))$.

So $0 = T(0)+(T(0)+(-T(0)))$, $0 = T(0)$. 

 
## Null Space

**Definition:** For $T \in \mathcal{L}(V,W)$, the null space of $T$ denoted by $\text{null } T$, is the subset of $V$ consisting of those vectors that $T$ maps to 0: $\text{null }T = \{v \in V : Tv = 0\}$. 

#### Null space is subspace

3.13
**Definition**: Suppose $T \in \mathcal{L}(V,W)$. Then $\text{null }T$ is a subspace of $V$.


**Proof**: 

**Zero**: Because $T$ is a linear map, $T(0) = 0$ (by [[Linear Maps, Range, Null Space#Zero|3.10]])). Thus, $0 \in \text{null }T$. 

**Addition**: Suppose $u,v \in \text{null }T$. Then $T(u+v) = Tu + Tv = 0+0 = 0$. Hence $u+v \in \text{null } T$. Thus $\text{null }T$ is closed under addition. 

**Scalar Multiplication:** Suppose $u \in \text{null }T$ and $\lambda \in F$. Then, $T(\lambda u) = \lambda Tu = \lambda 0 = 0$.

Hence, $\lambda u \in \text{null } T$. Thus, $\text{null }T$ is closed under scalar multiplication. 

We have shown that $\text{null } T$ contains 0, and is closed under addition and scalar multiplication. Thus, $\text{null } T$ is a subspace of $V$.

#### Injective

3.14
**Definition:** A function $T: V \rightarrow W$ is injective if $Tu = Tv$ implies $u=v$. 

Basically, $T$ is injective if and only if it maps distinct inputs to distinct outputs. 

##### Zero

3.15
**Claim:** Let $T \in \mathcal{V,W}$. Then $T$ is injective if and only if $\text{null }T = \{0\}$

**Proof:** ($\implies$) First, suppose $T$ is injective. We want to prove that $\text{null }T = \{0\}$. We already know that $\{0\} \subseteq \text{null }T$ by [[Linear Maps, Range, Null Space#Zero|3.10]] . To prove the inclusion in the other direction, suppose $v \in \text{null }T$. Then $$T(v)=0=T(0).$$
Because $T$ is injective, the equation above implies $v=0$. Thus we can conclude that $\text{null }T = \{0\}$ as desired.
$(\impliedby)$ Suppose $\text{null }T=\{0\}$. We want to prove that $T$ is injective. To do this, suppose $u,v \in V$ and $Tu=Tv$. Then $0 =Tu-Tv=T(u-v)$. 

So $u-v \in \text{null }T=\{0\}$, hence $u-v=0$, which implies that $u=v$. Hence, $T$ is injective, as desired.
#### Range and Surjectivity

**Definition:** For $T \in \mathcal{L}(V,W)$, the range of $T$ is the subset of $W$ consisting of those vectors that are equal to $Tv$ for some $v \in V$:
$$\text{range }T = \{Tv : v \in V\}$$

#### Range Is a Subspace
3.18
**Claim:** if $T \in \mathcal{L}(V,W)$, then $\text{range }T$ is a subspace of $W$

**Proof:**  If $T \in \mathcal{L}(V,W)$. Then $T(0)=0$, which implies that $0 \in \text{range }T$. 

If $w_1,w_2 \in \text{range }T$, then there exists $v_1,v_2 \in V$ such that $Tv_1= w_1$ and $Tv_2=w_2$. Thus $$T(v_1+v_2)=Tv_1+Tv_2 = w_1+w_2.$$
Hence $w_1+w_2 \in \text{range }T$. Thus $\text{range }T$ is closed under addition. If $w \in \text{range }T$ and $\lambda \in \mathbb{F}$, then there exists $v \in V$ such that $Tv = w$. Thus $$T(\lambda v) = \lambda Tv = \lambda w$$
Hence $\lambda w \in \text{range }T$. Thus $\text{range }T$ is closed under scalar multiplication. Thus, $\text{range }T$ contains $0$, is closed under addition and scalar multiplication. Thus $\text{range }T$ is a subspace of $W$.  

#### Surjective

**Definition:** A function $T: V \rightarrow W$ is called surjective if its range equals $W$. 

#### Fundamental Theorem of Linear Maps

**Definition:** Suppose $V$ is finite dimensional and $T \in \mathcal{L}(V,W)$. Then $\text{range }T$ is finite-dimensional and $\text{dim }V = \text{dim null }T+\text{dim range }T$ 

**Proof:** Let $u_1,...,u_m$ be a basis of $\text{null }T$, thus $\text{dim null }T=m$. The linearly independent list $u_1,...,u_m$ can be extended to a basis $$u_1,...,u_m,v_1,...,v_n$$ of $V$ (as every linearly independent list of vectors in finite-dimensional space can be extended to a basis). Thus $\text{dim }V = m+n$. 

We must now show that $\text{range }T$ is finite dimensional and $\text{dim range }T=n$. We will do this by proving that $Tv_1,...,Tv_n$ is a basis of $\text{range }T$.

Let $v \in V$. Because $u_1,...,u_m,v_1,...,v_n$ spans $V$, we can write $$v=a_1u_1+...+a_mu_m+b_1v_1+....+b_nv_n,$$where all $a_k,b_k \in \mathbb{F}$. Applying $T$ to both sides of the equation we get $$Tv = b_1Tv_1+...+b_nTv_n,$$ where the terms of the form $Tu_k$ disappeared because each $u_k$ is in $\text{null }T$. The last equation implies that the list $Tv_1,...,Tv_n$ spans $\text{range }T$. In particular, $\text{range }T$ is finite-dimensional.

To show that $Tv_1,...,Tv_n$ is linearly independent, suppose $c_1,...,c_n \in \mathbb{F}$ and $$c_1Tv_1+...+c_nTv_n=0.$$ Then, $T(c_1v_1+...+c_nv_n)=0$. Hence $c_1v_1+...+c_nv_n \in \text{null }T$. Because $u_1,...,u_m$ spans $\text{null }T$, we write $$c_1v_1+...+c_nv_n= d_1u_1+...+d_mu_m$$ for all $d_k \in \mathbb{F}$.

This implies that all $c_k, d_k=0$ because $u_1,...,u_m,v_1,...,v_m$ is linearly independent. Thus $Tv_1,...,Tv_n$ is linearly independent and hence a basis of $\text{range }T$ as desired.


#### Linear map to a lower-dimensional space is not injective

**Claim:** Suppose $V,W$ are finite dimensional vector spaces such that $\text{dim }V > \text{dim }W$. Then no linear map from $V$ to $W$ is injective.

**Proof:** Let $T \in \mathcal{L}(V,W).$ Then $$\text{dim null }T = \text{dim }V- \text{dim range }T \text{ (by fundamental theorem)}$$$$  \geq \text{dim }V - \text{dim }W \text{ (by dimension of a subspace)}$$$$ >0$$
>[!NOTE] Recall: 
>dimension of a subspace: 
>If $U \subseteq V$ is a subspace then $\text{dim}(U) \leq \text{dim}(V)$ 
 

This means that $\text{null }T$ contains vectors other than 0. Thus, $T$ is not injective (since $T$ is injective if and only if $\text{null }T = \{0\}$)


#### Linear map to a higher dimensional space is not surjective

**Claim:** Suppose $V,W$ are finite dimensional vector spaces such that $\text{dim }V < \text{dim }W$. Then no linear map from $V$ to $W$ is surjective.

**Proof:** Let $T \in \mathcal{L}(V,W)$. Then $$\text{dim range }T = \text{dim }V - \text{dim null }T \text{ (by fundamental theorem)}$$ $$\leq \text{dim }V$$$$< \text{dim }W$$

Since $\text{dim range }T < \text{dim }W$, $\text{range }T \neq W$, thus $T$ is not surjective. 

#### Homogeneous systems of linear equations

**Homogeneous:** the constant term on the right side of each equation below is 0.

Fix positive integers $m,n$ and let $A_{j,k} \in \mathbb{F}$ for $j=1,...,m$ and $k=1,...,n$. 

Consider the homogeneous system of linear equations:

$$\sum_{k=1}^n A_{1,k}x_k=0$$ $$\vdots$$
$$\sum_{k=1}^n A_{m,k}x_k=0$$

$x_1 = ... = x_n = 0$ is a solution of the system of equations above. Lets see if there are any others.

$$T(x_1,...,x_n) = (\sum_{k=1}^n A_{1,k}x_k,...,\sum_{k=1}^n A_{m,k}x_k)$$

The equation $T(x_1,...,x_n)=0$ (0 being the additive identity of $\mathbb{F}^m$, the list of length $m$ of all 0s) is the same as the homogeneous system of linear equations above. 


We want to know if $\text{null }T$ is strictly bigger than $\{0\}$, which is equivalent to $T$ not being injective (since $T$ is injective if and only if $\text{null }T = \{0\}$).


**Claim:** A homogeneous systems of linear equations with more variables than equations has nonzero solutions.

**Proof:** By the discussion above, $T$ is a linear map from $\mathbb{F}^n$ to $\mathbb{F}^m$ , and we have a homogeneous system of $m$ linear equations with $n$ variables $x_1,...,x_n$. Since a linear map to a lower-dimensional space is not injective we see that $T$ is not injective if $n > m$.




#### Inhomogeneous systems of linear equations

**Inhomogeneous:** the constant term on the right side of at least one equation below does not equal 0.

We consider the question of whether an inhomogeneous system of linear equations has no solutions for some choice of the constant terms.

Fix positive integers $m,n$, and let $A_{j,k} \in \mathbb{F}$ for all $j=1,...,m$ and $k=1,...,n$. For $c_1,..,c_m \in \mathbb{F}$, consider the system of linear equations:

$$\sum_{k=1}^n A_{1,k}x_k=c_1$$
$$\vdots$$
$$\sum_{k=1}^n A_{m,k}x_k=c_n$$
Is there some choice of $c_1,...,c_n \in \mathbb{F}$ such that no solution exists to the above.


Define $T : \mathbb{F}^n \rightarrow \mathbb{F}^m$. $T(x_1,...,x_n) = (c_1,...,c_m)$ is the same system of equations as for the homogeneous system of equations. We want to know if $\text{range }T \neq \mathbb{F}^m$. 

So, what condition ensures that $T$ is not surjective?

**Claim:** An inhomogeneous system of linear equations with more equations than variables has no solution for some choice of the constant terms

**Proof:** Use the notation and result from above. Thus $T$ is a linear map from $\mathbb{F}^n$ to $\mathbb{F}^m$, and we have a system of $m$ equations with $n$ variables $x_1,...,x_n$. 

Since a linear map to a higher-dimensional space is not surjective we see that $T$ is not surjective if $n < m$.

 For example, take an inhomogeneous system of five linear equations with four variables. It has no solution for some choice of the constant terms.