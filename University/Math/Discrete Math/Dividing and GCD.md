#math 

## Division

	Let $a,b \in \mathbb{Z}$ with $b>0$.

There exists integers $q$ and $r$ such that $$a=qb+r$$
and $0 \leq r < b$.

Moreover, there is only one such pair of integers $(q,r)$ that satisfies these conditions.

$a \text{ div } b = q$
$a \text{ mod } b = r$



Let $a,b \in \mathbb{Z}$, $n \in \mathbb{Z}$ with $n>0$. Then

$a \equiv b (\text{mod }n)$ if and only if $a \text{ mod }n = b \text{ mod }n$.


## Greatest Common Divisor

Let $a,b \in \mathbb{Z}$. We call an integer $d$ a common divisor of $a$ and $b$ provided that $d|a$ and $d|b$.

We call $d$ the greatest common divisor (gcd) of $a$ and $b$ provided:
- $d$ is a common divisor of $a$ and $b$
- If $e$ is a common divisor of $a$ and $b$, then $d \geq e$.

Denoted as $\text{gcd}(a,b)$


Let $c= a \text{ mod }b$. Then, $\text{gcd}(a,b) = \text{gcd}(b,c)$

### Euclid's Algorithm

- Let $c = a \text{ mod }b$ 
- If $c = 0$, then $\text{gcd}(a,b) = b$. Done.
- If $c \neq 0$, then  $\text{gcd}(a,b) = \text{gcd}(b,c)$. Repeat first two steps until $c=0$. 

$a,b$ are relatively prime (coprime) if $\text{gcd}(a,b)=0$

Let $a,b \in \mathbb{Z}$, both non-zero. The smallest positive integer of the form $ax+by$ where $x,y \in \mathbb{Z}$ is $\text{gcd}(a,b)$ 

There exists integers $x,y$ such that $ax+by = 1$ iff $a,b$ are coprime. 


