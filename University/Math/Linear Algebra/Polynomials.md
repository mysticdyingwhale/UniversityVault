# Polynomials
#math 


Assume $P : \mathbb{C} \rightarrow \mathbb{C}$ is a polynomial with complex coefficients unless stated otherwise.


- If $p(z) = a_0+a_1z+...+a_mz^m=0$ for all $z$ then $a_0=a_1=...=a_m=0$
- If $\lambda$ is a root of $p \in P_m$ i.e. ($p(\lambda)=0$) then $p(z) = (z-\lambda)q(z)$ for some $q \in P_{m-1}$ 
- If $p \in P_m$ and $p \neq 0$ then $p$ has at most $m$ **distinct** roots
- If $p \in P_m$ then there exists a unique $c,\lambda_1,...,\lambda_m \in \mathbb{C}$ such that $$p(z) =c (z-\lambda_1)(z-\lambda_2)...(z-\lambda_m)$$
- If $p$ has real coefficients then any root $\lambda$ is either real or $\overline \lambda$ is also a root of $p$
	- Recall $\overline \lambda$ is the complex conjugate ($\lambda = a+bi, \overline \lambda = a-bi$) 
- If $p$ has real coefficients then there exists unique numbers $c,\lambda_1,...,\lambda_m \in \mathbb{R}$ and $(\alpha_k,\beta_k) \in \mathbb{R}^2$ for $k=1,...,m$ with $\alpha_k^2 < 4\beta_k$ for all $k$ and $$p(x)=c(x-\lambda_1)(x-\lambda_2)...(x-\lambda_m)(x^2+\alpha_1x+\beta_1)...(x^2+\alpha_mx+\beta_m)$$
