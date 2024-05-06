# Sample Space and Uniform Probability
#math 


## Sample Space


A sample space is a pair $(S,P)$ where $S$ is a finite, nonempty set and $P$ is a function $P:S \rightarrow \mathbb{R}$ such that $P(s)$ for all $s \in S$ and $$\sum_{s\in S} P(s) =1$$


It is defined as the set of all possible outcomes of a random experiment or process.

### Uniform Probability

If $S$ is any finite set, the uniform probability on $S$ is the probability function $$P(s) = \frac1{|S|}$$ for all $s \in S$.

Let $A$ and $B$ be events in a sample space $S$. 

- $A \cap B$ is the probability that both $A$ and $B$ occur
- $A \cup B$ is the probability that either $A$ or $B$ occur
- $A-B$ (set difference) is the event that $A$ occurs and $B$ doesn't
- $\overline A = S-A$ (set complement) is the event that $A$ doesn't occur

- $P(A) + P(B) = P(A \cup B) + P(A \cap B)$
- If $A \cap B = \emptyset$ , then $P(A \cup B) = P(A)+P(B)$
- $P(A \cup B) \leq P(A) + P(B)$
- $P(S) = 1$
- $P(\emptyset) = 0$
- $P(\overline A)=1-P(A)$ 

#### Discrete Outcomes

In a discrete sample space, the outcomes are countable and distinct. 
 
This means that each outcome is separate and identifiable, and there is a finite or countably infinite number of outcomes. 

For example, the possible outcomes of rolling a six-sided die are discrete and can be listed as {1, 2, 3, 4, 5, 6}.

#### Exhaustive

The sample space must include every possible outcome that can occur in the experiment. 

It should be comprehensive, ensuring that no potential outcome is omitted.

#### Mutually Exclusive

Each outcome in the sample space is distinct and cannot occur simultaneously with another outcome. 

For example, when flipping a coin, you cannot get both heads and tails at the same time; the outcomes 'heads' and 'tails' are mutually exclusive.