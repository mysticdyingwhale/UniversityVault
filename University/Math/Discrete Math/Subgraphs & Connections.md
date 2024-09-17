# Subgraphs and Connections
#math 

## Subgraphs

Given $G$ and $H$ as graphs, we say $G$ is a subgraph of $H$ provided that all vertices in $G$ are in $H$ such that $V(G) \subseteq V(H)$ and all edges in $G$ are in $H$ such that $E(G) \subseteq E(H)$.

### Spanning Subgraphs

We call $G$ a spanning subgraph of $H$ provided that $G$ is a subgraph of $H$ and all vertices of $G$ are in $H$ such that $V(G) = V(H)$

Essentially, a subgraph with extra edges to the same vertices. 


### Induced Subgraphs

Let $H$ be a graph and let $A \subset V(H)$ be a subset of vertices of $H$. The subgraph of $H$ induced on $A$ is the graph $H[A]$ defined by:
- $V(H[A])=A$
- $E(H[A])= \{xy \in E(H) : x \in A \text{ and } y \in A \}$

Consists of some of the vertices of the original graph and all of the edges that connect them in the original. 


### Clique 

A subset of vertices $S \subseteq V(G)$ is called a clique provided any two distinct vertices in $S$ are adjacent. The clique number of $G$ is the size of the largest clique denoted by $\omega(G)$. 

A set $S \subseteq(G)$ is called a clique provided $G[S]$ is a complete graph ($S$ is an induced subgraph of $G$ )

Essentially a subset of vertices is called a clique given that any pair of vertices share an edge. 


![[Pasted image 20231217142522.png|300]]

Here, $\{c,d,h\}$ is a clique, and since it is the largest clique in $G$, $\omega(G)$ is 3. 

### Independent Set

A subset of vertices $S \subseteq V(G)$ is called an independent set provided no two vertices in $S$ are adjacent. Essentially the opposite of a clique.  

The independence number of $G$ is the size of the largest independent set denoted by $\alpha(G)$ 


![[Pasted image 20231217142522.png|300]]


Here, $\{a,c,f\}$ is an independent set. The largest independent set, however, is $\{f,d,b,i\}$, so $\alpha(G) = 4$


### Complement

The complement of a graph $G$ is a graph denoted by $\overline G$ defined by: $V(\overline G) = V(G)$ and $E(\overline G) = \{xy : x,y \in V(G), x \neq y , xy \not \in E(G)\}$.

A subset of $V(G)$ is a clique of $G$ iff it is an independent set of $\overline G$. Furthermore, 
$\omega (G) = \alpha(\overline G)$ and  $\alpha (G) = \omega (\overline G)$ .

Essentially, a complement graph is a graph that has the same vertices but all the cliques of the original graph are independent sets in the complement graph and vice versa. 

![[Pasted image 20231217150904.png|500]]

### Ramsey's Theorem

Ramsey's theorem states that for any graph on $N$ vertices, either the graph or its complement contains a clique or independent set of size $r$ or $s$. 


## Connections

### Walk

A walk on a graph $G$ is a sequence (or list) of vertices, with each vertex adjacent to the next such that:

$W = (v_0, v_1, v_2, ..., v_l)$ with $v_0 \sim v_1 \sim v_2 \sim ...\sim v_l$

- The length of a walk is the number of edges traversed
- There are $l+1$ vertices on a walk of length $l$. 
- a $(u,v)$ walk is a walk in a graph that starts at vertex $u$ and ends at vertex $v$. 
- The reversal $W^{-1}$ of a walk $W$ is also a walk
	- $W^{-1} = (v_l,v_{l-1},...,v_2,v_1,v_0)$ 

![[Pasted image 20231217160532.png]]


Valid walks: 
- $a \sim b \sim a$ 
- $i \sim h \sim c \sim b \sim a$ 
- $h \sim d \sim e \sim f$ 

Invalid walks:
- $a \sim a$
- $a \sim d \sim f$
- $i \sim i \sim b$

#### Path

A path is a walk in which no vertex is repeated. 

A path that contains all vertices in $G$ is called a Hamiltonian. 

All properties that apply to a walk apply to a path, the only difference being that it cannot contain the same vertex more than once. 

P will not traverse any edge more than once. 

Path:
- $a \sim b \sim c$

Walk but not path:
- $a \sim b \sim a$ 


A path is a subgraph with vertex set $V = \{v_1, v_2, ..., v_n\}$ and edge set $E = \{v_iv_i+1 : 1 \leq i < n\}$.

A path on $n$ vertices is denoted by $P_n$ and has a length of $n-1$.

If there is an $(x,y)$ walk in $G$, there is an $(x,y)$ path in $G$. 

- This can be proved by contradiction and well-ordering principle. 
	- Essentially, assuming there is a shortest walk in the set of all possible $(x,y)$ walks that is not a path, that means we can eliminate cycles meaning that there is a contradiction and it isn't the least. 

#### Connected

We say two vertices $u,v$ are connected provided there is a $(u,v)$-path in $G$. 

A graph is connected provided any pair of vertices in the graph is connected, essentially for all $x,y \in V(G), \exists P=\{x, ..., y\}$ .


#### Disconnection

A component is a connected subgraph. A fully connected graph has only one component, but a graph with $n$ smaller, isolated connected subgraphs contains $n$ components.

A vertex $v \in V(G)$ is called a cut-vertex provided that $G-v$ has more components than $G$. 

An edge $e \in E(G)$ is called a cut-edge provided that $G-e$ has more components than $G$. 

Below, 6 is an example of a cut-vertex, and {1,9} is an example of a cut-edge. 

![[Pasted image 20231217164514.png|400]]

Given a connected graph and a cut-edge $e \in E(G)$, $G-e$ has exactly two components.


### Cycle

A cycle is a walk of length at least 3 in which:
- the first and last vertex are the same
- No other vertices are repeated.

A cycle is a subgraph with a vertex set $V = \{v_1, v_2,...,v_n\}$ and edge set $E= \{v_1v_2,v_2v_3, v_n-1v_n, v_nv_1\}$.

Cycle of size $n$ denoted by $C_n$.

A graph that contains no cycles is called acyclic, or a forest.


### Trees

A tree is an acyclic, connected graph. 

- A forest is a set of trees
- A leaf is a vertex with degree 1
- Every tree with $n \geq 2$ has a leaf

Shares same logic as [[Rooted Binary Trees]] and [[Binary Search Trees]], just without a root. 

A spanning tree is a subgraph of $G$ that contains all vertices of $G$ and is a tree.

A graph has a spanning tree iff it is connected. 

![[Pasted image 20231217170727.png]]

To prove a graph $G$ has a spanning tree $S$:

Proving a graph is connected given that it contains a spanning tree:
- $V(G) = V(S)$, $E(S) \subseteq E(G)$ 
- $S$ is connected since it is a spanning tree. Since every path in $S$ is also in $G$, $G$ must also be connected.

Proving a graph contains a spanning tree given that it is connected:
- Use induction on edges. 
	- Base case single vertex
	- Inductive hypothesis, for all connected graphs with $n$ vertices they contain a spanning tree
	- Show for $n+1$ 


Cycles do not contain cut-edges.

Given a tree $T$ and a a leaf $v$, $T-v$ is a tree. 

Since $T$ is acyclic, removing a leaf will still allow it to be acyclic.

Given any two vertices $w,u \in V(T-v)$, we can find a path in $T-v$ connecting them. 

We first find a path in $T$ connecting them, then claim that $v$ does not appear in this path, as if $v$ does appear in the path it must be in the middle of the path, meaning that $\alpha(v) \geq 2$, which suggests its not a leaf. 

Since this is a contradiction, we can safely claim that $T-v$ is a tree. 