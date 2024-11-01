##### Criteria for estimators
- **Principle of unbiasedness:** In a long run, you hit the target eventually..
	- $$ E[\widehat{\theta}]=\theta$$ Unbiased
	- $$ E[\widehat{\theta}]\neq \theta$$ Bbiased
	- $$B[\widehat{\theta}] = E[\widehat{\theta}] - \theta$$ The bias of the estimator
 
- **Consistency:**  Convergence in probability(The variance vanishes as $n \rightarrow \infty$)
	- If $E[\bar{Y}]$ = $\mu$, where $\bar{Y}$ is a unbiased estimator for $\mu$, then $Var(\bar{Y})= \sigma ^2 /n$
- **Principle of minimum variance:** An estimator having minimum variance is prefered
- **Known Dist:** should have a known sampling distribution:
	- $$Y_1, Y_2,....Y_n \sim N(\mu \sigma^2), \bar{Y} = N(\mu, \sigma^2/n)$$
	- If we can't find the dist, like for example, if we use a $Beta(\alpha, \beta)$, then we would have to use CLT or something but the approx would not be good.
	- This would not be good.
- ![[Pasted image 20240923112545.png]]
#### How do we ensure these are met?
**Mean Square Error:** $MSE(\widehat{\theta}) = E[ ( \widehat{\theta} - \theta)^2]$
- It is rarely the case that $n \rightarrow \infty$ so we introduce MSE.
**Biased Variance Tradeoff:** $MSE(\widehat{\theta}) = Var(\widehat{\theta})+ [B(\widehat{\theta})]^2$
- It involves both terms, the variance of a estimator and it's bias, with the MSE
- We should be able to get a grasp of how both terms are impacting
- As we decrease bias, the variance increase, and vice versa, so we have a tradeoff
- The ultimate goal in statistical analysis is to find this tradeoff where it is the best
###### Proof
$$
\begin{align}
MSE[\widehat{\theta}] &= E[ ( \widehat{\theta} - \theta)^2]\\
&= E[((\widehat{\theta} - E[\widehat{\theta}]) + (E[\widehat{\theta} - \theta]))^2]\\
&= E([\widehat{\theta} - E[\widehat{\theta}]]^2) + E[(E[\widehat{\theta}] - \theta)^2] + 2 E[(E(\widehat{\theta})- \theta)( \widehat{\theta} - E[\widehat{\theta}])]\\
&= Var(\widehat{\theta}) + B(\widehat{\theta})^2 + 2E[B(\widehat{\theta})(\widehat{\theta}- E[\widehat{\theta}])]\\
&= Var(\widehat{\theta}) + B(\widehat{\theta})^2 + 2B[\widehat{\theta}] E[\widehat{\theta} - E[\widehat{\theta}]]\\
&= Var(\widehat{\theta}) + B(\widehat{\theta})^2 + 0\\
&= Var(\widehat{\theta}) + B(\widehat{\theta})^2
\end{align}



$$
- We used the bias definitioned
- The expectation of any centered random variable is 0, this is used in line 5, if we subtract the mean from the observation itself.
- $$\begin{align} E[ \widehat{\theta} - E[\widehat{\theta}]] &= E[\widehat{\theta}] - E[E[\widehat{\theta}]]\\ &=  E[\widehat{\theta}] - E[\widehat{\theta}] \\
&= 0\end{align}$$
###### Unbiased
Say, we have a biased estimator such that:
$$ E[ \widehat{\theta}] = a \theta + b$$
Can we convert this estimator to a unbiased one?
1. Consider that $$B[\widehat{\theta}] = E[\widehat{\theta}] - \theta = a\theta + b-\theta = (a-1)\theta + b$$
	- Now, $B(\widehat{\theta}) = 0$,  so it is biased
	- Usually, we always get biased estimators, but we can convert it(idk how yet)
2. $$\begin{align} 
	E[\widehat{\theta}] &= a\theta + b \\
	 E[\widehat{\theta}] -b &= a\theta\\
	 1/a(E[\widehat{\theta}]-b) = \theta \\
	 E[\frac{\widehat{\theta}-b}{a}] &= \theta
\end{align}$$
	- This is unbiased, and we can consider this as a new estimator:
	- $$ \widehat{\theta} = \frac(\widehat{\theta}-b}{a}$$
##### Estimators
Note how $1/n \sum_{i=1}^{n}(Y_i-\bar{Y})^2$ estimates $\sigma^2$ 
**Convex Combinations:** 
This is when $w_1 + w_2 = 1$, and $0<w_1,w_2<1$, and:
$$w_1 X_1 + w_2 X_2$$
We can write one in the other where $w_2 = 1- w_1$, 

##### Example
Consider the example int he slides, if we have such that:
$$\widehat{\theta}_3 = a \widehat{\theta}_1 + (1-a) \widehat{\theta}_2$$
Where $0<a<1$, then if a = 0.8, we obtain:
$$\widehat{\theta}_3 = (0.8) \widehat{\theta}_1 + (0.2) \widehat{\theta}_2$$
Now:
$$\begin{align} 
E[\widehat{\theta}_3] &= E[a\widehat{\theta}_1 + (1-a)\widehat{\theta}_2]\\
&= aE[\widehat{\theta}_1] + ( 1-a)E[\widehat{\theta}_2]\\
&= a \theta + (1-a)\theta\\
&= \theta
\end{align}$$
Therefore, this $\widehat{\theta}_3$ is unbiased for $theta$, let us minimize the variance where they are *independent*:
$$\begin{align}

Var(\widehat{\theta}_3) &= Var(a\widehat{\theta}_1 + (1-a)\widehat{\theta}_2)\\
&= a^2 Var(\widehat{\theta}_1) + ( 1-a)^2 Var(\widehat{\theta}_2)\\
&= a^2 (\sigma_{1})^2 + (1-a)^2 (\sigma_{2})^2
\end{align}
$$
- a is a constant so we can apply it like this
- We essentially end up with a quadratic function since the variances are known, so we want to minimize it as 0 where derivative is 0 :
$$\begin{align} 
g(a)&= a^2 (\sigma_{1})^2 + (1-a)^2 (\sigma_{2})^2\\
dg(a)/ da &= 2\sigma_1^2 a -  2 \sigma_2 ^2 (1-a) = 0 \\
\sigma_1 ^2 a + \sigma_2 ^2 &= \sigma _2 ^2 \\
a &= \frac{\sigma_2 ^2 }{\sigma_1 ^2 + \sigma_2 ^2 }\\
d^2g(a)/ da^2 &=  2 \sigma_1 ^2 + 2 \sigma_2 ^2 > 0 (\text{ at 0, it is concave up})
	\end{align}$$
- We get the fact that this new value of a, $a*$ is a globa minimum, so to minimize it, we just plus this new value of a as the constant in the formula given above.
###### Sample means
Consider where:
$$ S^2 = 1/(n-1) \sum_{i=1}^{n} (Y_1-\bar{Y})^2 $$
- Most of us forgot on how to derive this, especially it's variance, remember this.
- Recall that $E[S^2] = \sigma^2$ and $\frac{(n-1) S^2}{\sigma^2} \sim \chi_{n-1}^2$:
$$\begin{align} 
Var(\frac{(n-1) S^2}{\sigma^2}) &= 2(n-1)\\
(n-1)^2 / \sigma^4 = Var(S^2) &= 2(n-1)\\
Var(S^2) &= 2\sigma^4 / ( n-1)
\end{align}$$Consider, now, where:
$$ \tilde{S}^2 = 1/(n) \sum_{i=1}^{n} (Y_1-\bar{Y})^2 $$
- This is nothing but the previous example multiplied with $(n-1)/n$!, so:
- $E[\tilde{S}] = (n-1)/n \sigma^2$
- $Var(\tilde{S}^2) = 2 (n-1)/n^2 \sigma ^4$
Let us consider bias:
$$\begin{align} B(\tilde{S}^2) &= E[\tilde{S}^2] - \sigma^2 \\
&= (n-1)/(n) \sigma^2 - \sigma^2 \\
&= (-1/n) \sigma^2 < 0 \end{align}$$
So, $\tilde{S}^2$ is biased for $\sigma^2$
$$\begin{align} 
MSE[S^2] &= Var(S) - [B[S^2]]^2 \\
&= (2/(n-1))\sigma^4 \\
MSE(\tilde{S}^2) &= Var(\tilde{S}^2) + [B[\tilde{S}^2]]^2\\
&= 2 (n-1)/n^2 \sigma ^4 + (1/n^2) \sigma^4 \\
&= \frac{2(n-1)}{n^2}\sigma^4
\end{align}$$
Let us compare these two now:
- For $n>1$, the $MSE[S^2] > MSE[\tilde{S}^2]$,
- $S^2$ is unbiased for $\sigma^2$ but has larger MSE as compared to $\tilde{S}^2$ which is biased.
##### Example 2
Consider the example on slide 12, the minimum of the sample has a exponential with the parameter:
$$\hat{Y}_{(1)} \sim Exp(\theta/n)$$
Now, $E[\theta]=\theta$, and $E[\hat{Y}_{(1)}]] = \theta/n$ , then $E[n\hat{Y}_{(1)}] = \theta$, , so $E[\tilde{\theta}]=\theta$, so it is unbiased for $\theta$. Let us do the MSE:
$$MSE(\tilde{\theta}) = Var(n\hat{Y}_{(1)}) + B(n\hat{Y}_{(1)}) = n^2 Var(\hat{Y}_{(1)}) = n^2 \theta^2 / n ^2 = \theta^2$$
We also use the fact that the expectation and variance of the exponential on the sheet.
- If we use the first, just $Y$, it is very unbiased, but the variance is $\theta^2/n$, so it decreases as it is just a exponential with paramter $\theta$.
- The second one has unchanging variance and expectation as shown above.
##### Uniform Dist
Consider such $Y_1, Y_2, .... Y_n \sim_{iid} Unif(\theta, 2)$ 
Homework(???): Find $E[Y_{(1)}]$, the minimum.