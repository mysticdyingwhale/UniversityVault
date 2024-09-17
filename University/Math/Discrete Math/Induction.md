# Induction
#math 

## Proof by Induction

The idea behind mathematical induction is that, supposing that the first statement is true, and the $k$th statement being true always suggests that the $k+1$th statement is also true, that the statement is true for all instances. 

The steps are as follows:

- Base Case
	- Show that for the lowest value, the statement holds true (usually $n=1$ or $n=0$)
- Inductive Hypothesis
	- Assume that for some $n=k$ the statement holds true
- Inductive Step
	- Given that the statement holds true for $n=k$, prove that it holds true for $n=k+1$
- Conclude that by induction the statement is true for all $n$ 

## Strong Induction

Strong induction, like regular induction, involves the same 3 steps. The only differences are that in the hypothesis, instead of assuming that the statement holds true for some $n=k$, you assume that its true for all $n \leq k$, and that there may be multiple base cases.

The steps are as follows:

- Base Case
	- Show that for some values, the statement holds true
	- Best to declare the base cases as you complete the proof rather than before it so ensure you cover them all
- Inductive Hypothesis
	- Assume that for all $n \leq k$ the statement holds true
- Inductive Step
	- Given that the statement holds true for $n \leq k$, prove that it holds true for $n=k+1$
- Conclude that by strong induction the statement is true for all $n$ 

Best to work backwards for strong induction to ensure you don't miss anything (start from inductive step)