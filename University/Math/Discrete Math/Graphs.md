#math 


## Graphs

A graph is a pair $G = (V,E)$, where $V=V(G)$ is a nonempty finite set of objects and $E=E(G)$ is a set of two-element subsets of $V$. 

- Elements of $V$ are called vertices
- Elements of $E$ are called edges
- The order of $G$ is the number of vertices, $|V| = |V(G)| =n$
- The size of $G$ is the number of edges, $|E| = |E(G)| = m$


![[Pasted image 20231213230041.png]]

In this graph $G$, $|E| =8, |V| = 5$.


Given a graph $G = (\{1,2,3,4,5,6,7\},\{\{1,2\}\{1,3\}\{2,3\}\{3,4\},\{5,6\}\})$, we can plot it visually as:
![[Pasted image 20231213230808.png|450]]

We say two nodes $a,b$ are adjacent provided that $\{a,b\} \in E$, noted by $a\sim b$ 

if $\{a,b\}$ is an edge of $G$:
- $a$ and $b$ are endpoints of the edge
- can be written as $ab$ 
- $a$ and $b$ are neighbours
	- The neighbourhood of $b$ is $N(b) = \{a \in B: a \sim b\}$
	- $a$ is joined to $b$

The neighbourhood of node $3$ our above $G$ is $N(3)= \{1,2,4\}$



We say that for a vertex $v$ that is an endpoint of an edge $e$ such that $v \in e$, $v$ is incident with $e$.

The degree of $v$ is the number of edges with which $v$ is incident. Degree denoted by $d_G(v)$ or $d(v)$. 
- $d(v)$ = $|N(v)|$
- $\Delta (G)$ is the maximum degree of a vertex in $G$
- $\delta (G)$ is the minimum degree of a vertex in $G$
- G is $r$-regular provided all vertices have a degree $r$ 
