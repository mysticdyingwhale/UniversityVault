# Conditional Probability

#math  

Conditional Probability is a measure of the probability of an event occurring, given that another event has already occurred. You could say that it means that we have more available information.


>[!note]
>Probability of A intersect B:
$$P(A \cap B) = P(B) \times P(A|B)$$
Probability of A Union B:
$$ P(A \cup B) = P(A) + P(B) - P(A \cap B) $$
Probability of A Given B:
$$P(A|B) = \frac{P(A \cap B)}{P(B)}$$


You can think of UNION and INTERSECT as Logic Gate operators:
- $\cup$ as the OR operator 
- $\cap$ as the AND operator.

## Independent Probability


>[!note]
Two events are considered independent when:
$$P(A \cap B) = P(A)P(B)$$



## Bayes' Theorem

Bayes' Theorem describes the probability of an event, based on prior knowledge of conditions that might be related to the event.


>[!note]
>Bayes' Theorem states:
$$P(A|B) = \frac{ P(B|A)P(A)}{P(B)}$$


## Markov Chains & Transition Matrices
A Markov Chain is a **stochastic** (random) model for describing a sequence of possible events.


>[!note]
Think of it as a finite state machine with n states and random state transitions at each timestep.


![|350](https://deparkes.co.uk/wp-content/uploads/2020/08/GraphView.png)

A Markov chain has 𝑁 states and an 𝑁×𝑁 transitional probability matrix P. 

For each step in the Markov process, all values are in exactly one of these states. 

### Probability Matrices

A probability matrix essentially indicates the probability of each state change given the current state. 

Rows in the matrix indicate the current state and columns the potential state.

For example, when given a probability matrix P:

ㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤ$\begin{matrix} n_1 & n_2 & n_3\\ \end{matrix}$

$$ P = \begin{matrix}

n_1\\
n_2\\
n_3\\
\end{matrix}
\begin{bmatrix}

0 &  1 & 0\\
0.8 & 0 & 0.2\\
0 & 1 & 0\\
\end{bmatrix}$$

We would produce a Markov Chain:
![[Pasted image 20231201212039.png]]


### Adjacency Matrices
An adjacency matrix is a square matrix used to represent a finite graph (in our case the Markov Chain).

It indicates which pairs are adjacent or not in a graph. 

Below is the adjacency matrix of the Markov Chain:

ㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤㅤ
$$\begin{matrix} n_1 & n_2 & n_3\\ \end{matrix}$$
$$ A = \begin{matrix}

n_1\\
n_2\\
n_3\\
\end{matrix}
\begin{bmatrix}

0 &  1 & 0\\
1 & 0 & 1\\
0 & 1 & 0\\
\end{bmatrix}$$

