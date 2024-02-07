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

**Proof:** 
### Algebraic Properties of linear maps

**Associativity:** $(T_1 T_2)T_3 = T_1(T_2 T_3)$ whenever $T_1, T_2,T_3$ are linear maps such that their products make sense ($T_3$ maps into the domain of $T_1$, and $T_2$ maps into the domain of $T_1$)

**Identity:** $TI = IT = T$ when $T \in \mathcal{L}(V,W)$. Here, the first $I$ is the identity operator on $V$, and the second is the identity operator on $W$.

**Distributive Properties:** $(S_1 + S_2)T = S_1 T + S_2 T$ and $S(T_1+T_2) = ST_1 + ST_2$ whenever $T, T_1, T_2 \in \mathcal{L}(U,V)$ and $S,S_1,S_2 \in \mathcal{L}(V,W)$. 

**Proof:** 

#### Zero

**Definition:** Suppose $T$ is a linear map from $V$ to $W$. Then $T(0)=0$

**Proof:** By Additivity we have $T(0) = T(0+0) = T(0)+T(0)$. 

Adding the additive inverse to of $T(0)$ to each side we get $T(0)+(-T(0)) = T(0)+T(0)+(-T(0))$.

So $0 = T(0)+(T(0)+(-T(0)))$, $0 = T(0)$. 

 
## Null Space

**Definition:** For $T \in \mathcal{L}(V,W)$, the null space of $T$ denoted by $\text{null } T$, is the subset of $V$ consisting of those vectors that $T$ maps to 0: $\text{null }T = \{v \in V : Tv = 0\}$. 

#### Null space is subspace

**Definition**: Suppose $T \in \mathcal{L}(V,W)$. Then $\text{null }T$ is a subspace of $V$.


**Proof**: 

**Zero**: Because $T$ is a linear map, $T(0) = 0$ (by[[Linear Maps#Zero| Zero]])). Thus, $0 \in \text{null }T$. 

**Addition**: Suppose $u,v \in \text{null }T$. Then $T(u+v) = Tu + Tv = 0+0 = 0$. Hence $u+v \in \text{null } T$. Thus $\text{null }T$ is closed under addition. 

**Scalar Multiplication:** Suppose $u \in \text{null }T$ and $\lambda \in F$. Then, $T(\lambda u) = \lambda Tu = \lambda 0 = 0$.

Hence, $\lambda u \in \text{null } T$. Thus, $\text{null }T$ is closed under scalar multiplication. 

We have shown that $\text{null } T$ contains 0, and is closed under addition and scalar multiplication. Thus, $\text{null } T$ is a subspace of $V$.

#### Injective


#### Range and Surjectivity


#### Fundamental Theorem of Linear Maps

#### Examples

