# Vectors
#math 
 

A vector is an element of a vector space which contains two elements, both size and direction.
 
When given coordinate points (position vectors), consider them as vectors from origin unless stated otherwise.


## Vector Forms

### Vector
The vector equation of a line is:

$$L = \begin{pmatrix} a \\ b \\c \end{pmatrix} + \lambda \begin{pmatrix} k \\ m \\n \end{pmatrix}$$

Where $(a,b,c)$ is any point on the line and $(k,m,n)$ is the direction vector. 

### Parametric
The Parametric Equations of a line are: 
$$x = a + \lambda k$$
$$y = b + \lambda m$$
$$z = c + \lambda n$$

This can be used to find the position of the vector at '$\lambda$' time, if given $\lambda$ of course.

### Cartesian
The Cartesian Equation of a line is:
$$L: \frac {x - a}{k} = \frac{y - b}{m} = \frac {z-c}{n}$$

The Cartesian Equation of a plane is:
$$\Pi : Ax + By + Cz + d = 0$$
Where $(A,B,C)$ is the normal.

To find d, use the equation $n . r = a . r$ .

## Equations:

#### Vector Magnitude:

$$ \sqrt {v_1^2 + v_2^2 + v_3^2} $$

Gives the size of the vector, regardless of direction.
#### Dot Product: 

$$ v \cdot w = v_1w_1 + v_2w_2 + v_3w_3 $$

   
The dot product (scalar product) of two vectors measures how much vectors go in the same direction 

If the two vectors are scalar multiples, the two vectors are parallel. 

If the dot product is zero, the vectors are perpendicular.

The result of finding the dot product of two vectors is not a vector, but simply a real number.

#### Cross Product:

$$(v_2w_3 - v_3w_2 )i + (v_1w_3 - v_3w_1)j + (v_1w_2 - v_2w_1)k$$

![[Pasted image 20211219113115.png|250]] 

The magnitude of the cross product of two vectors measures how much vectors go in different directions

The cross product produces a normal vector to the two planes

If the value of the cross product is zero, the two vectors are parallel.


The line of intersection of two planes with normals $n_1$ and $n_2$ is $n_1 \times n_2$.

#### Angle Between two vectors:


$$ \theta = \cos^{-1}\bigg[\frac{a.b} {|a||b|}\bigg]$$

Finding the angle means the two lines cross, meaning that the direction vector is the key part of the equation.

The angle between two planes is the same as the angle between their normals


## Vector Planes

The normal of any vector plane is perpendicular to any line which lies on the plane.

The dot product of the normal and any point on the plane is equal to the dot product of the normal and any other point on the plane:

$$n . r = a . r$$
$r =$ normal
$n =$ point 1
$a =$ point 2

Use this equation to find the Cartesian Equation of a plane. 

-   The angles between two planes is the same as the angle between the normals.

- The dot product of any line on the plane and the normal of the plane is 0.

-   Planes meet at a line.


To determine a plane, we need either:
- Three points not on the same line
- A line and a point which is not on the line 
- Two Intersecting Lines

### Intersection
 
Three distinct planes may intersect at a single point, along a straight line, or have no intersection at all.
 
These cases correspond to the different possibilities for the solutions of a system of three equations. 
 
When the solution is not unique, the straight line corresponds to the general solution of the system.


 ![[Pasted image 20211219125235.png|250]]

To find the intersection between a line and a plane, express x, y and z for the line in terms of λ and substitute into the Cartesian equation of the plane.
 
To find the intersection of two lines, set the two vectors equal to each other and use two of the equations to find λ and μ. (μ in this case would just be the λ equivalent for another line). 
 
 
If these values do not satisfy the third equation, the lines are **skew lines** (two lines that do not intersect and are not parallel).
 

## Distance

### Point from a Plane

To find the distance MP:
- Write down the vector equation of the line with direction n through point M. 
- Find the intersection, P, between the line and the plane. 
- Calculate the distance MP

![[Pasted image 20211219164700.png|250]]
### Between Parallel Planes
To find the distance between two parallel planes:

- Pick a point in the first plane. 
- Write down the equation of the line in the direction of the normal passing through this point.
- Find the intersection point of this line and the second plane. 
- Find the distance between the two points

![[Pasted image 20211219164809.png|250]]
### From a point to a line
- Form the vector $MP = r -m$; it will be in terms of λ. 

- $MP$ is perpendicular to the line: $MP • d = 0$. 
-  This is an equation for λ; solve it. 
-   Use this value of λ to find $MP$ . 
-   The required distance is $MP$ .

![[Pasted image 20211219164822.png|250]]