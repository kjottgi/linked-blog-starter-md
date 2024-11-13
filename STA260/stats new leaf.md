Throughout the semester we have talked about:
- Unbiasedness
- Minimum Variance:
It is not wrong that cramer-rao theorem gives us a procedure that the given statistic is the minimum variance, how do we find MVUE?
- This will bring us to sufficiency
- Then Rao-Blackwell
- Then completeness, and a unbiased estimator that is sufficient and complete,
- This will give us UMVUE
Today's lecture is pretty dense and we need full attention.
**What is sufficient?**
Sufficiency is if $Y_{1},Y_{2},\dots Y_{n} \sim^{iid} f_y(\theta)$, 
- If we consider the addition of all the observations, the sample mean $\bar{Y}$ contains as much data as the entire sample size
We use the factorization theorem:
- If it possible to decompose the likelihood function into two positive functions, then our statistic is sufficient for estimating $\theta$
$$L\left( y_{1},y_{2}, \dots | \theta \right) = g(u,\theta)  \times h(y_{1},y_{2}\dots y_{n})$$
Where $g(u,\theta)$ is the function only of u and $\theta$ and $h(y_{1},y_{2},\dots y_{n})$ is not a function of $\theta$
ex)
![[Pasted image 20241104113354.png]]
- The maximum function is 0 if any is greater then the theta
![[Pasted image 20241104114435.png]]

A statistic $U=I(Y_{1},Y_{2},\dots Y_{n})$ is said to be complete if and only if for every function $g(U)$ such that:
$$
E(g(U)) = 0 \text{ for all theta implies that g(U)=0}
$$
This meneans that $P(\{ U: g(U) \neq 0 \} = 0 )$ . Basically, taking the expectation of any function of the statistic U should imply that the funciton is also 0
This means that it is is unbiased:
$$
\begin{align}
E[g_{1}(U)] = \theta \\
E[g_{2}(U)] = \theta 
\end{align}
$$
E[g(U) = \theta]
![[Pasted image 20241104121349.png]]
ex 2)
![[Pasted image 20241104123208.png]]
Recall from STA256 that:
$$E[X_{1} | X_{2}] \text{ is a function of } X_{2}$$
Also, that
$$E[E[X_{1}|X_{2}]] = E[X_{1}]$$
$$Var(E[X_{1}|X_{2}]) \leq Var(X_{1})$$

**Rao-Blackwell Theorem:**  Let $\hat{\theta}$ be a unbiased estimator for $\theta$ such that $V(\hat{\theta}) < \infty$ , If U is a sufficient statstic for $\theta$ define $\hat{\theta}* = E(\hat{\theta}|U)$. Then for all $\theta$:
$$ E[\hat{\theta}*]=\theta \text{ and } V(\hat{\theta}*) = V(\hat{\theta})$$
Then, if $\hat{\theta}$ is unbiased and $U$ is sufficient. Then:
$$E[\hat{\theta} | U] = E[unbiased|sufficient] = MVUE$$
The expected value of a unbiased sufficient given a sufficient statistic, $E[statistic|U]$  is a function of U. Then, also, $E[statistic|U]$ is sufficient and unbiased is also unbiased.
$$
E[E[unbiased|sufficient]] = E[unbiased]
$$
$$Var(E[Unbiased|sufficient]) \leq Var(unbiased)$$


In a lesser way, if we have a unbiased estimator $U_{1}$ and a sufficient and complete estimator $U_{2}$ then $E[U_{1}|U_{2}]$ is a unique minimum variance unbiased estimator[UMVUE].
### idk what masoud is doing toay ngl
#### review
If we have $Y_{1}.Y_{2},\dots Y_{n} \sim Exp(\theta)$. Then $f(y) = \frac{1}{\theta} e^{-y/\theta}$, then:
$$
\begin{align}
 L(\theta) &= \left( \frac{1}{\theta^n} e^{-\sum y_{i}/\theta} \right)
\end{align}
$$

Since we can factor this to $g(u,\theta) = (\frac{1}{\theta^n}) e^{-u/\theta}$ and $h(y_{1},..y_{n})=1$, this is a SS. Now, it is also unbiased as:
$$E\left[ \sum  y_{i}\right] = \sum \theta= n\theta$$
So $E\left[ \sum \frac{y_{i}}{n} =\theta\right]$, therefore, this is a MVUE by the Rao-Blackwell Theorem. 
**Summary**:
- Obtain a SS using a factorization theorem
- Check completeness where $E[g(u)]=0 \Rightarrow  \rightarrow g(u)=0$
- Check for unbiasedness
#### Exponential family
We say that the PDF $f(y(\theta))$ belongs to the exponential family if:
$$F(y|\theta) = e^{P(\theta) k(y) + q(\theta) + S(y)}, a < y < b$$
The PDF $f(y|\theta)$ belongs to a regular class of exponential family if and only if three conditions are satisfied:
- The first one is that a and b should be free from $\theta$, the support is free from theta
- $P(\theta)$ and $k(y)$ are non-trivial $\Leftrightarrow$ $P'(\theta) = 0$ and $k'(y)\neq {0}$
- $S(y)$ is continuous 
Then if $f_{y|\theta}$ is a regular member of the exponential family, then 
$$U= \sum_{i=1}^{n} k(y_{i})$$
Also:
$$E[U] = E[ \sum k(y_{i})] = n \frac{q'(\theta)}{p'(\theta)}$$
Proof: Just take the integral equal to on
is sufficient and complete.
Example: If Y is binomial
Now:
$$
\begin{align}
f(y| \theta) &= (nCy) \theta^y
 (1-\theta)^{n-y}\\ \\
&= (nCy) \left( \frac{\theta}{1-\theta} \right)^y
 (1-\theta)^{n} \\ \\
&= e^{\ln((nCy) \left( \frac{\theta}{1-\theta} \right)^y
 (1-\theta)^{n})}\\ \\
&= e^{\ln(nCy) + y\ln(\theta/1-\theta) + n\ln(1-\theta)} \end{align}\\
$$
Therefore, we have a family where $k(y)=y$, $p(\theta) = \ln\left( \frac{\theta}{1-\theta} \right)$, $q(\theta) = n\ln(1-\theta)$, and $S(y) = \ln(nCy)$. Therefore, this is part of the exponential family so 
$$U= \sum_{i=1}^n K(y_{i}) =\sum_{i=1}^n Y_{i} $$
is sufficient and complete.
**Showing Poisson is in exp**
If Y is poisson:
$$
\begin{align}
f(y) &= \frac{e^{-\theta}e^y}{y!}\\ \\
&=  e^{\ln(\dots)}\\ \\
&= e^{y\ln(\theta) - \theta - \ln(y!)}
\end{align}
$$
Now, $p(\theta)= \ln(\theta)$, $k(y)=y$, $q(\theta)=-\theta$, and $S(y) = -\ln(y!)$. This is part of the exponential family so then:
$$
U = \sum k(Y_{i}) = \sum Y_{i}
$$
is sufficient and complete.
EX: Normal
![[Pasted image 20241107104400.png]]
The negative can also go in the denominator, then, $f(y|\theta)$  is in the exponential family and $U= \sum_{i=1}^{n} Y_{i}^2$ is complete adn sufficient for $\theta$.