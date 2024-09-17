# Expectation and Variance
#math 

### Random Variables

A random variable, $X$, is a function defined on a sample space $(S,P)$ such that $X : S\rightarrow V$ for some set $V$ .

Example: Given a fair coin flipped 3 times, let $X$ be the number of heads shown. 

For each outcome $s$ , the values of $X(s)$ would be: 
- $s = HHH : X(s) =3$
- $s = HHT : X(s) =2$
- $s = HTT : X(s) =1$
- $s = TTH : X(s) =1$
- $s = TTT : X(s) =0$
- etc...


### Independence

Let $(S,P)$ be a sample space and let $X$ and $Y$ be random variables defined on $(S,P)$. We say that $X$, $Y$ are independent if $$P(X=a \text{ and } Y=b) =P(X=a)\cdot P(Y=b)$$ for all values of $a$ and $b$.


## Expectation

Let $X$ be a real-valued random variable defined on a sample space $(S,P$). The expectation (expected value) of $X$ is $$E(X) = \sum_{s \in S} X(s) \cdot P(s)$$
Given two real random variables $X$, $Y$ on a sample space $(S,P)$:

1. $X+Y$ is the random variable whose value at $s \in S$ is $X(s) + Y(s)$
2. $X-Y$ is the random variable whose value at $s \in S$ is $X(s) - Y(s)$
3. $XY$ is the random variable whose value at $s \in S$ is $X(s)Y(s)$


Suppose $X$ and $Y$ are real-valued random variables defined on a sample space $(S,P)$. Then $$E(X+Y) = E(X) + E(Y)$$
Suppose $X$ is a real-valued random variable defined on a sample space $(S,P)$ and let $c \in \mathbb{R}$.  Then $$E(cX) = cE(X)$$


Suppose $X$ and $Y$ are real-valued random variables defined on a sample space $(S,P)$ and $a,b \in \mathbb{R}$. Then $$E(aX+bY) = aE(X) + bE(Y)$$

Let $X$ and $Y$ be independent. Then $$E(XY) = E(X) \cdot E(Y)$$


## Variance

Let $X$ be a real-valued random variable defined on a sample space $(S,P)$ . The variance of $X$ is the number $$Var(X) = E((X- E(X))^2)$$ $$Var(X) = E(X^2) -[E(X)]^2$$