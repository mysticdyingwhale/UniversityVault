# Math
#cs #math 


## Barycentric Coordinates

The centre of mass of 3 masses

$p(t_1,t_2,t_3) = t_1A_1 + t_2A_2 + t_3A_3$
$t_1+t_2+t_3 = 1$
![[Pasted image 20240917103417.png]]

- A point $p$ is inside the triangle formed by $A_1,A_2,A_3$ if and only if $0 < t_{1,2,3} < 1$
- If one of the coordinates is zero and the other two are between zero and one, then you are on an edge
- If two of the coordinates are zero, then the other is one, and you are at a vertex
- Fast rejection while coding


