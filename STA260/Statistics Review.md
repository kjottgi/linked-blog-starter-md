# Order statistics
- **Min CDF/PDF**:

$$\begin{align}  \\
F_{{X_{1}}}(x) &= 1-[1-F(x)]^n \\ \\
f_{{X_{1}}}(x) &= n[1-F(x)]^{n-1} f(x)
 \\
\end{align}$$
- **Max CDF/PDF**:
$$\begin{align}  \\
F_{{X_{n}}}(x) &= [F(x)]^n \\ \\
f_{{X_{n}}}(x) &= n[F(x)]^{n} f(x)
 \\
\end{align}$$
 - **Joint PDF of $X_{1}, X_{n}$**:
 $$\begin{align}  \\
 F_{X_{(1)}X_{(n)}}&= [F(y)]^n - [F(y) - F(x)]^n\\ \\
 f_{X_{(1)}X_{(n)}}&= (n)(n-1)(F(y)-F(x))^{n-2} f(x)f(y)
\end{align}$$
- **PDF of multivaried indp variables**:
$$\begin{align}  \\
f_{{X_{(1)}X_{{(2)}}},\dots..X_{(n)}}(x_{1},x_{2}\dots x_{(n)}) &= n! f(x_{1})f(x_{2})\dots.f({x_{n})} \\
 \\
 \\
\end{align}$$
# Sampling mean and variance
- We can sample in two ways:
	1. **The Sample Mean**:
		$$\bar{Y}=\frac{1}{n}\sum_{i=1}^{n}Y_{i}$$
	2. **The Sample Variance:**
	$$S^2 = \frac{1}{n-1}\sum_{i=1}^{n}(Y_{i}-\bar{{Y}})^2$$
**Sampling Of the Sample Distribution**
Consider samples $Y_1, Y_2,....Y_n \sim_{}{iid} N(\mu, \sigma^2)$, then if we consider the sample mean, it emulates:
$$\bar{Y}\sim N(\mu, \frac{\sigma^2}{n})$$
$Y_1, Y_2,....Y_n \sim_{}{iid} N(\mu, \sigma^2)$
1. Consider any $Y_{1},\dots,Y_{n} \sim^{iid} N(0,1)$, where they are all standard normal, then:
$$U=Y_{1}+Y_{2}+\dots +Y_{n} \sim N(0,n)$$
	This essentially means that adding n normal standards makes a normal standard with variance n.
2. Consider any $Y_i \sim N(\mu_i, \sigma_i^2)$, where each are independent, the similar to previously:
$$U=Y_{1}+Y_{2}+\dots +Y_{n} \sim N(\mu_{1}+\mu_{2},\dots + \mu_{n},\sigma_{1}^2 + \dots + \sigma_{n}^2)$$
3. If we now consider any  $Y_1, Y_2,....Y_n \sim_{iid} N(\mu, \sigma^2)$ , let us finally consider the sample mean:
$$\bar{Y}=\bar{Y_{n}}= \frac{Y_{1}+\dots + Y_{n}}{n}= \frac{U}{n} \sim N\left( \mu, \frac{\sigma^2}{n} \right)$$
	Now, since we know that $\bar{Y}$ emulates the normal, then this means that:
$$Z=\frac{\bar{Y}-\mu}{\sigma / \sqrt{ n  } } \sim N(0,1)$$
4. If we once again have{} $Y_1, Y_2,....Y_n \sim_{iid} N(\mu, \sigma^2)$, consider normalizing each variable where:
$$Z_i = \frac{Y_{i}=u}{\sigma}$$
	- Then, if we square this, we get a chi squared with one degree of freedom, and adding these we get:
	$$\sum_{i=1}^{n}Z_{i}^2 = \sum_{i=1}^{n}\chi^2_{1} = \sum_{i=1}^n(\frac{Y_{i}-\mu}{\sigma})^2$$
	- This gives us a $\chi^2$ distribution with $n$ degrees of freedom as from chi properties from STA256
	- This really applies if it is independent or not, you just need to normalize the variable to form it into a chi.
#### Adding Chi
- If we have independent random variables $Y_1,Y-2,...Y_n$$ that each have chi with $v_1,v_2,...v_n$ degrees of freedom, then the random variable:
- $$U=Y_{1}+\dots + Y_{n}$$
- This has a chi distribution found by adding $v=v_1+...+v_n$
- Remember that $\chi_n^2 = Gamma(n/2,2)$
#### Identity for sample variance
Let us have $Y_1,Y-2,... Y_n$ from a normal distribution with mean $\mu$ and variance $\sigma^2$, Then, we can conclude the following:
$$\frac{(n-1)S^2}{\sigma^2}= \sum_{i=1}^{n}\frac{(Y_i-Y)^2}{\sigma^2} \sim \chi_{n-1}^2$$
We can prove it as follows:
$$\begin{align}  
S^2 &= \frac{1}{n-1}\sum_{i=1}^{n}(Y_{i}-\bar{{Y}})^2\\ 
\frac{S^2(n-1)}{\sigma^2} &= \sum_{i=1}^{n}\left( \frac{Y_{i}-\bar{{Y}}}{\sigma} \right)^2 \\
\frac{S^2(n-1)}{\sigma^2} &= \sum_{i=1}^{n}\chi^2_{1} \\
\frac{S^2(n-1)}{\sigma^2} &= \chi^2_{n}  \\
\end{align}$$
But, we practically act as $S^2$ and $\bar{Y}$ are independent![proof]
## Student T
A way we can deal with inferences on $\mu$ is by using a T distributed RV:
$$T=\frac{\bar{Y}-\mu}{\frac{S}{\sqrt{ n }}} \sim \frac{
\mu ^*-\mu}{\frac{\sigma^*}{\sqrt{ n }}} $$
- This T-Dist has $n-1$ degrees of freedom, by approximating(?)
- Student T can be used for small samples on a normal distribution
- It accommodates for the extremes in small sample sizes better
We can simplify the student T distribution as follows:
$$\begin{align}   
 T &= \frac{\bar{Y}-\mu}{\frac{S}{\sqrt{ n }}}\\
 &= \frac{(\bar{Y}-\mu)\left( \frac{\sigma}{\sqrt{ n }} \right)}{\sqrt{ \frac{S^2}{\sigma^2} }}\\
&= \frac{Z}{\sqrt{ \frac{W}{(n-1)} }}  \\ 
Z & \sim \frac{\bar{Y}-\mu}{\frac{\sigma}{\sqrt{ n }}} \sim N(0,1)\\
W & \sim \frac{(n-1)S^2}{\sigma^2} \sim \chi^2_{n-1}
\end{align}$$This basically allows us to rewrite the student T dist, let us now show it,:
$$T=\frac{N(0,1)}{\sqrt{ \frac{\chi^2_{(n-1)}}{n-1} }} \sim t_{{n-1}} \text{ n deg freedom}$$
**Formal Def of T Dist**:
If we have a standard normal random variable Z and W, a chi squared variable, with $v$ freedom, then if Z and W are independent:
$$T = \frac{Z}{\sqrt{ \frac{W}{v} }} \sim t_{v}$$
- Each curve of $t_v$ is bell shaped and centered at 0, similar to the normal
- Each $t_v$ curve is spread out more then the standard normal on the side
- As we increase $v$, the spread of the $t_v$ decreases
- As we approach $v \to \infty $ then the $t_v$ approaches the standard normal curve, the $Z$ , or normal.
## F-Dist
Consider two chi distributions, $W_1 \sim \chi^2_{v_1}$ and  $W_2 \sim \chi^2_{v_2}$, then the F distribution is:
$$F = \frac{\frac{W_{1}}{v_{1}}}{\frac{W_{2}}{v_{2}}}$$
This has F-Dist with parameters $v_1$ and $v_2$.
### Samples variances and their F-Dist
If we take two sample variances, $S_{1}^2, S_{2}^2$, with sizes of $n_1$ and $n_2$, with variances $\sigma_1^2$ and $\sigma_2^2$, then:
$$\frac{\left( \frac{S_{1}^2}{\sigma_{1}^2} \right)}{(\frac{S_{2}^2}{\sigma_{2}^2})} \sim F(n_{1}-1, n_{2}-2)$$
This can be proven:
$$\begin{align}  \frac{\left( \frac{S_{1}^2}{\sigma_{1}^2} \right)}{\left( \frac{S_{2}^2}{\sigma_{2}^2} \right)} &= \frac{\left( \frac{S_{1}^2}{\sigma_{1}^2} \right)}{\left( \frac{S_{2}^2}{\sigma_{2}^2} \right)} *\frac{n_{1}-1}{n_{1}-1}*\frac{n_{2}-1}{n_{2}-1}  \\
  &= \frac{\frac{\chi^2_{n_{1}-1}}{n_{1}-1}}{\frac{\chi^2_{n_{2}-1}}{n_{2}-1}} \\
 &= F(n-1,n-2)\\
 \\
 \\
 \\
\end{align}$$
### CLT APPROX
Consider any number of random samples from a population, $Y_1, Y_2 \dots Y_n$, with a mean $\mu$, and variance $\sigma^2$ , with a unknown distribution. 
*If n is sufficiently large, then $\bar{Y}$ is approximately normally distributed with mean $\mu$ and variance $\frac{\sigma^2}{n}$ *
$$\bar{Y} \sim N\left( \mu, \frac{\sigma^2}{n} \right)$$
- By sufficiently large, assume n is greater then 30.
#### Binomial Approximation
A normal *continuous* distributions can be used to approximate *discrete* binomial probabilities when there is a very large number of trials.
- np and n(1-p) must be significantly large, where
- $$np \geq 5, n(1-p) \geq 5$$
**If $Y \sim Bin(n,p)$ then $Y \sim N(\mu=np, \sigma^2=npq)$**, but for correction purposes, we use correciton values to fix the values to approx "better". Consider a discrete value b as a interval:
- $$P(Y=b)=P(b-0.5 \leq Y \leq b+0.5)$$
- $$P(Y \leq b)=P(Y \leq b + 0.5)$$
- $$P(b \leq T)=P(b-0.5 \leq Y)$$
# Estimators
##### Criteria for estimators
- **Principle of unbiasedness:** In a long run, you hit the target eventually..
	- $$ E[\widehat{\theta}]=\theta$$ Biased
	- $$ E[\widehat{\theta}]\neq \theta$$ Unbiased
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
##### Standard Error
We can define, where $\sigma^2$ is the population variance.
$$Var(\bar{X}) =\frac{\sigma}{n}$$Then:
$$\sigma_{\bar{Y}}=\sqrt{ Var(\bar{Y})}= \frac{\sigma}{\sqrt{ n }} $$
The standard deviation of $\hat{\theta}$ is called the standard error, (SE) , where the standard error of $\hat{\theta}$ is the standard deviation of $\hat{\theta}$. 
###### Example 8
Consider the example, now let us use the sample mean, where it is $\bar{Y}$. This is a unbiased estimator as:
$$E[\bar{Y}] = \theta, \text{bar(Y) is a unbiased estimator of theta}$$
Also, note how:
$$Var(\bar{Y})= \frac{\sigma^2}{n} = \frac{\theta^2}{n} \rightarrow \sigma_{\bar{Y}} = \frac{\sigma}{\sqrt{ n }}$$
- Now, the standard error, $\sigma_{\bar{Y}}$ is based on $\theta$ which is unknown
- We can use a estimator though, instead, so $\hat{\theta}$:
- $$\sim \frac{\bar{\theta}}{\sqrt{ n }} \rightarrow \sigma_{\overline{Y}} = \frac{\overline{Y}}{\sqrt{ n }}$$
###### Example 8 pt 2
In this case, we know that $n=10$, while $\hat{\theta}=\overline{Y}=1020$.
- We say 2 standard error, so we can go 2 from the error, we can multiply it
- We used the fact that $\sigma_{\overline{Y}} = \frac{\overline{Y}}{\sqrt{ n }}$ 
- $$
\begin{align}
2*\text{Standard Error} &= 2 * \sigma_{\hat{\theta}}  \\ \\
&= 2 * \frac{\overline{Y}}{\sqrt{ n }}\\ \\
&= 2 * \frac{1020}{\sqrt{ 10 }}\\ \\
&= 645.05 

\end{align} \\

$$
**Old Exam Q**
- $$Y_{i}= \text{RV denoting number of random nuclear sites per unit volume }$$
- $$Y_{i} \sim Poisson(\lambda_{A})$$
- $$\begin{align}
E[\bar{Y}] &= \frac{1}{50} \sum_{i=1}^{50}[Y_{i}]\\ \\
&= \lambda_{A}\\ \\
Var(\bar{Y}) &= \frac{\sigma^2}{n}\\ \\
&= \frac{\lambda_{A}}{50}\\ \\
\sigma_{\overline{Y}}&= \sqrt{ \frac{\lambda_{A}}{50} }\\ \\
&= \sqrt{ \frac{\hat{\lambda_{A}}}{50} }\text{(Plug in Principle)} \\ \\
&= \sqrt{ \frac{\overline{Y}}{50} }\\ \\
&= \sqrt{ \frac{20}{50} }\\ \\
&= 0.6324 \\
\text{Solving for the standard by 2}:&\\
20 \pm 2 * 0.6324  &= 20 \pm 1.265 \\ \\
&= (18.735,21.265)
\end{align}$$
- Note that $\frac{\sigma^2}{n}$, depends on the variance of your random variable, in the later case, since each $Y_i$ is all poisson, the variance is just theta itself, while previously it was just the parameter squared due to the difference of distribution
#### Is unbiased estimators actually good?
$$\begin{align}
E[(-1)^Y] &= \sum_{{y=1}}^{\infty} (-1)^y \frac{\theta e^{-\theta}}{y!}\\ \\
&= e^\theta \sum_{{y=1}}^{\infty} \frac{(-\theta)^y}{y!}\\ \\
&= e^{-\theta}e^{-\theta}\\ \\
&= e^{-2\theta}\\ \\
 \end{align}$$
- So, this is a ubised estimator for $e^{-2\theta}$$
- *Why is this estimator not good?*
	- $e^{-2\theta}$ will always be a number that is less then 0, and less then one
		- $0 \leq e^{-2\theta} < 1$
	- What i'm actually estimating is continuous, the $e^{-2\theta}$, but we are estimating using discrete poisson
- *Are we violating the principle of unbiasedness?*
	- A principle is generally true, but not a theorem, but always satisfactory in all cases
# Interval Statistics 1: The Intro
- If we have any estimator $\hat{\theta}$ that estimates $\theta$ 
- We can estimate $\theta$ using a interval $[\hat{\theta_{L}}, \hat{\theta_{U}}]$ instead of using some point $\hat{\theta}$
**Confidence Interval**: The confidence interval which is characterized using the endpoints on the interval $\hat{\theta_{L}}, \hat{\theta_{U}}$, which are the upper confidence level, and lower confidence level, are used to calculate a theta:
$$
P[\hat{\theta_{L}} \leq \theta \leq \hat{\theta_{U}}] = 1 - \alpha
$$
- $\alpha$ is the significance level
- $1-\alpha$ is known as the confidence level
There are multiple types such as:
- Two sided: $[\hat{\theta_{L}}, \hat{\theta_{U}]}$
- Lower one sided: $[\hat{\theta_{L}},  \infty]$
$$
P(\bar{\theta_{L}} \leq \theta) = 1-\alpha
$$
- Upper one sided:$[-\infty, \hat{\theta_{U}}$
- $$
P(\bar{\theta \leq \theta_{L}} ) = 1-\alpha
$$
### Methods of Estimation
We need to find a random variable, called a pivot, which is a function of the estimator of $\theta$ satisfying the following:
1. It is a function of both $\theta$ and the random sample, $Y_{1},Y_{2},\dots Y_{n}$
2. It's distribution(pdf, cdf or mgf)  does not depend on $\theta$ or any unknown parameter
Consider a sample $Y_{1},Y_{2},..Y_{n} \sim N(\mu,\sigma^2)$ and consider $\bar{Y} \sim N(\mu, \sigma^2)$ Consider:
$$
\begin{align}
U_{1} &= \bar{Y}-\mu \sim N\left( 0, \frac{\sigma^2}{n} \right)\\ \\
U_{2} &= \frac{\bar{Y}-\mu/}{\frac{\sigma}{\sqrt{ n }}} \sim N(0,1)
\end{align}
$$
Since $U_{2}$ doss not depend on any unknown parameters, it is a better pivotal point.
How to find the confidence interval:
1. Formulate a possible pivotal quantity U
2. Investigate if this pivotal quantity can be used as a pivotal quantity
3. Constructing a confidence interval using U
We will *usually* be given the pivotal quantity, but may need to derive it!
$1-\alpha:$ The confidence interval we want the range to be into, so the percentage of probability.
Note that we take whatever is not in the range and divide it by two, this is not the only approach but is the best[from outside sources.]
###### How do we find the distribution of U?
There are three methods:
1. Distribution technique
2. Moment generating function technique
		Fact:
		$$M_{{aY+b}}= e^b M_{Y(at)}$$
3. Arithmetic of random variables
		We know that $$
Y \sim Exp(\theta) \rightarrow Y \sim Gam(1,\theta)
$$So, we know the basic fact that if d
$$
Y \sim Gam(\alpha, \beta) \Rightarrow \alpha Y \sim Gam(\alpha, \alpha \beta)
		$$
		We also know another fact that if we have two identical with different alphas but different betas:
		$$
Y_{1 } + Y_{2} \sim \Gamma(\alpha_{1}+\alpha_{2}, \beta)
$$

##### Example 1
1.  If we use the dist function technique:
		$$Y \sim Exp(\theta), F_{Y}(y) = 1- e^{-y/\theta}$$
		$$ \begin{align}
F_{U}(u) &= P(U \leq u )\\ \\
&= P( \frac{Y}{\theta} \leq u)\\ \\
&= P(Y \leq \theta u)\\ \\
&= F_{Y}(\theta u)\\ \\
&= 1-e^{-u}, u >0
\end{align}$$
	It only relies on U.
2. We know that $Y$ is a exponential distribution with mean $\theta$. Consider the critical interval:
$$
Y = \frac{Y}{\theta}
$$
	We know that:
	$$
	\begin{align}
	Y \sim Exp(\theta) &= Gam(1,\theta)\\ \\
	&= \frac{Y}{\theta} \sim Gam\left( \frac{1,\theta}{\theta} \right)\\ \\
	&= U \sim Gam(1,1)\\ \\
	&= U \sim Exp(1)
	\end{align}
	$$
	Therefore, $U$ is a pivotal as it is not reliant on anything.
Let us now construct the critical interval such that:
$$P[a \leq U \leq b] = 1- \alpha$$
![[Pasted image 20240930114636.png]]
$$\begin{align}
P\left[ a \leq \frac{Y}{\theta} \leq b \right] &= 1- \alpha \rightarrow \\ \\
P\left[ \frac{1}{a} \geq \frac{\theta}{y} \geq \frac{1}{b} \right] &= 1- \alpha \rightarrow \\ \\
P\left[ \frac{y}{a} \geq \theta \geq \frac{y}{b} \right] &= 1- \alpha \rightarrow\\ \\
CI = \left[ \frac{y}{b} , \frac{y}{a}\right]
\end{align}$$
We have some rules
- Change inequality sign when inverting a ratio
- Change inequaility signs when multiplying by negative
![[Pasted image 20240930115026.png]]
Using this, we can conclude that:
$$\begin{align}
P[0 \leq U \leq a] &= 0.05\\ \\
F_{U}(a) &= 0.05 \\
1-e^{-a} &= 0.05\\ \\
a =& -\ln(0.95)\\
\end{align}$$In a similar fashion:
$$\begin{align}
P[0 \leq U \leq b] &= 0.95\\ \\
F_{U}(a) &= 0.95 \\
1-e^{-a} &= 0.95\\ \\
a =& -\ln(0.05)\\
\end{align}$$
So, our confidence intervals become:
$$CI = \left[ \frac{y}{-\ln(0.05, )}, \frac{y}{-\ln(0.95)} \right]$$

##### Example 2
$Y_{1},Y_{2},\dots\dots Y_{n} \sim^{iid} Exp(\theta)$
$$
Y= \frac{2}{\theta} \sum_{i=1}^{n} Y_{i}
$$
$$
\begin{align}
Y_{i} \sim Exp(\theta) &\rightarrow Gam(1,\theta)\\ \\
& \rightarrow  \sum_{i=1}^{n} Y_{i} \sim Gam(n, \theta)\\ \\
& \rightarrow \frac{2}{\theta}  \sum_{i=1}^{n} Y_{i} \sim Gam\left( n, \frac{2}{\theta}\theta \right)\\ \\
&\rightarrow U \sim Gam(n,2)
\end{align}
$$
This is simply a chi with $2n$ , as:
$$\chi^2_{v} = Gam\left( \frac{v}{2},2n \right)$$
Let us now use the MGF technique, recall that:
$$(\begin{align}
 M_{ \frac{2}{\theta} \sum_{i=1}^{n} Y_{i}}(t) &= \left[ M_{Y}\left( \frac{2}{\theta}t \right) \right]^n  \\ 
&= (1-\theta(\frac{2}{\theta}t)^{-1})n\\ 
&= (1-2t)^{-n}\\ 
&= (1-2t)^{-2n/2} \text{ MGF of the Chi Dist}\\ 
U &\sim \chi^2_{{2n}}
\end{align})$$
- note that Y is a expoentnial, so so we use the MGF for that!
Let us now construct our CI:
$$
\begin{align}
P[a \leq U \leq b] &= 1- \alpha\\
\\
P\left[ \chi^2_{1-\frac{\alpha}{2}} \leq \frac{2}{\theta} \sum_{i=1}^{n} Y_{i} \leq \chi^2_{\frac{\alpha}{2}}  \right] &= 1-\alpha\\ \\
P\left[ \frac{1}{\chi^2_{1-\frac{\alpha}{2}}} \geq \frac{\theta}{2\sum Y_{i}} \geq \frac{1}{\chi^2_{\frac{\alpha}{2}}} \right]&= 1-\alpha\\ 
&= P\left[ \frac{ 2\sum Y_{i}}{\chi^2_{1-\frac{\alpha}{2}}} \geq \theta \geq \frac{ 2\sum Y_{i}}{\chi^2_{\frac{\alpha}{2}}} \right]
\end{align}
$$
We basically use the fact that it's chi squared to solve for this.
Therefore, the critical interval is:
$$[\frac{ 2\sum Y_{i}}{\chi^2_{\frac{\alpha}{2}}},\frac{ 2\sum Y_{i}}{\chi^2_{1-\frac{\alpha}{2}}}]$$
For part c, 
$$
\begin{align}
\bar{y} &= 4.77 \rightarrow \sum Y_{i} = \bar{n}y = (4.77)(7)\\ \\
[\frac{ 2\sum Y_{i}}{\chi^2_{\frac{\alpha}{2}}},\frac{ 2\sum Y_{i}}{\chi^2_{1-\frac{\alpha}{2}}} & \rightarrow [\frac{ 2(4.77)(7)}{\chi^2_{\frac{0.05}{2}}},\frac{ 2(4.77)(7)}{\chi^2_{1-\frac{0.05}{2}}} \\
CI &= [2.557, 11.862]
\end{align}$$
- **Wrong interpretation:** If we conduct the random experiment, with proability $95\%$ the interval CI (2.5,11.9) will capture $\theta$ 
- **Right interpretation:** If we repeat the experiment 100 times, then on average, the interval $(2.5, 11.9)$ will capture $\theta$ 95 times.
With point estimators, it will be near the interval, while with intervals it captures it.
$$
\begin{align}
Y_{i} \sim Gammma(2, \beta) &\rightarrow \sum Y_{i} \sim Gamma(2n, \beta)\\ \\
& \rightarrow \frac{2}{\beta} \sum Y_{i} \sim Gamma\left( 2n, \frac{2}{\beta}\beta \right) \\ \\
&\rightarrow Gamma(2n,2)\\ \\
&= U \sim Gam\left( \frac{4n}{2}, 2 \right)\\ \\
&= U \sim \chi^2_{(4n)}
\end{align}
$$
$$
\begin{align}
P \left[ \chi^2_{0.975} \leq \left( 2\sum Y_{i}) \right)/ \beta \leq \chi^2_{0.025}  \right] &=0.95\\ \\
P[\frac{2\sum Y_{i}}{\chi^2_{0.025}} \leq \beta leq \frac{2\sum Y_{i}}{\chi^2_{0.975}}]
\end{align}
$$
We can construct confidence intervals based on normal distributions.
If we have a binomial such that
$$
Y \sim Binomial(n,p)
$$
- There n is the number of trials, and p is the success, if we want to estimate *p* then a good estimator can be:
$$
\hat{P} = \frac{Y}{n}
$$
1. This is where $Y$= The number of voters saying movies are getting better, whre $n$ is the number of voters
This means that:
$$E[\hat{P}]= \frac{1}{n}E[Y] = \frac{1}{n}np = p$$
$$Var(\hat{P}) = \frac{1}{n^2}Var(Y) = \left( \frac{1}{n^2} (np)(1-p) \right) = \frac{p(1-p)}{n}$$

Then the critical interval for $p$, is $\hat{p} \pm z_{\alpha} \sigma_{\hat{p}}$
So.., our goal is to estimate p, but we need p, so we can plug in our estimator:
$$
\begin{align}
CI &= 0.45 \pm z_{0.01} \sqrt{ \frac{(0.45)*0.55}{800} } \\
&= 0.45 \pm 0.041 = (0.401,0.491)
\end{align}
$$
The hypothesis that the majority of adults believe that movies are getting better is rejected at $98$ confidence level.
##### After example
Consider any $Y_1,Y_2,....Y_n \sim^{iid} N(\mu, \sigma^2)$ is the following pivotal?
$$
\frac{\bar{Y}-\mu}{\frac{\sigma}{\sqrt{ n }}}
$$
If the $\sigma$ is known, then Yes, $Z = \frac{\bar{Y}-\mu}{\frac{\sigma}{\sqrt{ n }}} \sim N(0,1)$
If $\sigma$ is unknown, then we take the sample variance:
$$
\frac{\bar{Y}-\mu}{\frac{S}{\sqrt{ n }}} \sim t_{{n-1}}
$$
This is n-1 as since $\bar{Y}$ is fixed, we can pick n-1.
$$
\begin{align}
P\left[ -t_{\frac{\alpha}{2}} \leq T \leq t_{\frac{\alpha}{2}} \right] &= 1-\alpha \\
P\left[ -t_{\frac{\alpha}{2}} \leq \frac{\bar{Y}-\mu}{\frac{S}{\sqrt{ n }}} \leq t_{\frac{\alpha}{2}} \right]&= 1-\alpha
\end{align}
$$P[-t_{\frac{\alpha}{2}}]![[Pasted image 20241003103356.png]]
##### Large sample confidence intervals
It is possible to find potential quantities where:
1. $\mu$ is the means and $p$ is the proportions
2. $\mu_{1}-\mu_{2}$ is the difference in means and $p_1-p_2$ is the diffeerence in populations
Let us have an estimator:
$$\triangle = \mu_{1}-\mu_{2}, \hat{\triangle} = \hat{Y}-\hat{X}$$
Where we have independent RVs where:
$$
Y_{1},\dots Y_{n } \sim N(\mu_{1}, \sigma_{1}^2), X_{1},\dots X_{n } \sim N(\mu_{2}, \sigma_{2}^2)
$$

Now, for large sample sizes:
$$
\frac{\hat{\triangle}-\triangle}{\sigma_{{\triangle}}} \sim N(0,1)
$$
$$Z = \frac{\hat{\triangle}-\triangle}{\sqrt{ \frac{\sigma_{1/}^2}{2}+\frac{\sigma_{2/}^2}{2} }}  $$
![[Pasted image 20241003104157.png]]Our assumption is that all the $\sigma_{1}^2 = \sigma_{2}^2 =\sigma$. So, the exact confidence interval of $\triangle$ is:
$$
\frac{(\bar{Y}-\bar{X})-(\mu_{1}-\mu_{2})}{\sigma \sqrt{ \frac{1}{n_{1}} + \frac{1}{n_{2}} }} \sim N(0,1)
$$
- We want to use a convex coeffifient of both to maximize the best of both
$$\frac{n_{1}-1}{n_{1}+n_{2}-2}S_{1}^2 + \frac{n_{2}-1}{n_{1}+n_{2}-2}S_{2}^2 = S_{p}^2$$
Where $S_p^2$ is the weighted average off $S_1^2$ and $S_2^2$(it is a convex combination.)
$$
\begin{align}
E[S_{p}^2] &=  E[\frac{n_{1}-1}{n_{1}+n_{2}-2}S_{1}^2 + \frac{n_{2}-1}{n_{1}+n_{2}-2}S_{2}^2 ]  \\ \\
&= \frac{n_{1}-1}{n_{1}+n_{2}-2}\sigma_{1}^2 + \frac{n_{2}-1}{n_{1}+n_{2}-2}\sigma_{2}^2\\ \\
&= \sigma^2 \text{ SO it is unbiased for sigma}
 \\
\end{align}
$$We know from perviously that we can create $S_1$ and $S_2$ into chi distibutions with $n_1-1$ and $n_2-1$ degrees, this means that:
$$\frac{(n_{1}-1)S_{1}^2}{\sigma_{1}^2} + \frac{(n_{2}-1)S_{2}^2}{\sigma_{2}^2} = \chi^2_{n_{1} + n_{2} - 2}$$
We also know that:
1. $\bar{Y}, S_{1}^2$ are independent
2. $\bar{X}, S_{2}^2$ are independent
3. $S_p$ is independent from $\frac{(\bar{Y}-\bar{X})(\mu_{1}-\mu_{2})}{\sigma \sqrt{ \frac{1}{n_{1}} + \frac{1}{n_{2}} }}$ which is n(0,1)
So, also that:
$$\frac{n_{1}+n_{2} -2}{\sigma^2}(S_{p}^2) \sim X^2 _{{n_{1+n_{2}-2}}}$$

Finally, we can construct a T dist:
$$t_{n_{1}+n_{2}+2} =\frac{\frac{(\bar{Y}-\bar{X})(\mu_{1}-\mu_{2})}{\sigma \sqrt{ \frac{1}{n_{1}} + \frac{1}{n_{2}} }}}{\frac{\frac{n_{1}+n_{2} -2}{\sigma^2}(S_{p}^2)}{n_{1}+n_{2} -2} }$$


###  Normal Estimation 
# Interval Statistics 2: Normal Estimation/ T Dist + Sample Sizes
### Normal Estimation
Consider estimating things like $\mu, p, \mu_{1}-\mu_{2}, p_{1}-p_{2}$, then, for large samples, we can emplot the central limit theorem with our estimator:
$$
Z = \frac{\hat{\theta}-\theta}{\sigma_{\hat{\theta}}}
$$
Z doesn't really depend on $\theta$, and even further, this is kind of what we were doing before, we just, kind of expand it.  
#### Common Example: Showing the Normal Interval is funny
![[Pasted image 20241101162437.png]]
![[Pasted image 20241101162908.png]]
From the graph, we can visualize it like this, now, we know that:
$$\hat{\theta}=N(\theta, \sigma_{\hat{\theta}})$$
Let us now just use the previous methods to solve for the interval:
$$
\begin{align}
P(a \leq Z \leq b) &= 1-  \alpha \\    
P(x \geq b) &= \frac{\alpha}{2}\\ 
b &= z_{\frac{\alpha}{2}} \text{ (you can look up the z score ...)} \\
P(x \leq a ) &= \frac{\alpha}{2}\\ 
P(x \geq -a )  &= \frac{\alpha}{2} \\ 
a &= -z_{\frac{\alpha}{2}}\\
 P(a \leq Z \leq b) &= 1-  \alpha \\   \\
P\left( -z_{\frac{\alpha}{2}} \leq \frac{\hat{\theta}-\theta}{\sigma} \leq z_{\frac{\alpha}{2}} \right) &= 1-  \alpha \\  \\
P(-z_{\frac{\alpha}{2}}\sigma -\hat{\theta} \leq - \theta \leq z_{\frac{\alpha}{2}}\sigma -\hat{\theta} )  &= 1-  \alpha \\  \\
P(z_{\frac{\alpha}{2}}\sigma +\hat{\theta} \geq  \theta \geq -z_{\frac{\alpha}{2}}\sigma +\hat{\theta} )  &= 1-  \alpha \\

\end{align}
$$
We can see that the interval is kind of symmetric, so we can finally conclude that the interval is:
$$C.I = [\hat{\theta} + z_{\frac{\alpha}{2}}\sigma, \hat{\theta}-z_{\frac{\alpha}{2}}\sigma]$$






#### Example
![[Pasted image 20241007111943.png]]
The critical interval in this case does not contain 0, as the hypothesis that $\mu_{1}=\mu_{2}$ is rejected at $95\%$ confidence level.
- We are REJECTING the hypothesis that the math students did better then the literature students.
**What if we're interested in comparing the variance of two populations?**
Confidence interval for $\sigma^2$:
- Pitovtal: $\frac{n-1(S^2)}{\sigma^2} \sim \chi^2_{n-1}$ 
- $100(1-\alpha)\% $ CI for $\sigma^2$ is:
- ![[Pasted image 20241007112546.png]]
So...
$$ P\left[ \frac{(n-1)S^2}{\chi^2_{1-\frac{\alpha}{2}}} \geq \sigma^2 \geq [ \frac{(n-1)S^2}{\chi^2_{\alpha}}  \right]$$
**Example**
![[Pasted image 20241007113051.png]]
Basically apply the formula above, note that due to the degree of freedom being so lesser, that we end up with such a big confidence interval, so we have 3 samples so our confidence interval.

### T-Dist
If we don't know the mean, we can instead resort to using the t-dist, which is fairly similar, so, to estimate $\mu$ when we don't have $\sigma$:

$$\text{ Our Pivotal Quantity} = T = \frac{\bar{Y}-\mu}{\frac{S}{\sqrt{ n }}}$$
The bottom part is basically the standard deviation of the sample mean, we use the sample variance to estimate the theta, and the rest normally follows using the sample mean. this can be simplified using a similar proof to before to show that:

$$C.I = \left[ \bar{Y} - t_{\frac{\alpha}{2}} \frac{S}{\sqrt{ n }   }, \bar{Y} + t_{\frac{\alpha}{2}} \frac{S}{\sqrt{ n }   } \right]$$
### Comparison of means/other params.
If we have two sample means, $\bar{X}$ and $\bar{Y}$, from normal populations so :
$X_{i} = N(\mu_{1},\sigma_{1}),Y_{i} = N(\mu_{1},\sigma_{2})$
where each have a certain # of samples being pooled.
Using previous theorems, if we assume they have the same variance:
$$\bar{X}-\bar{Y}= N\left( \mu_{1}-\mu_{2}, \sigma^2\left( \frac{1}{n_{1}}+\frac{1}{n_{2}} \right) \right)$$
We simply apply the same normalization as previous, and if we assume that $\sigma_{1}=\sigma_{2}=\sigma$, then we can construct a "normal" distribution from the following:
$$
Z=N(0,1) = \frac{(\bar{X}-\bar{Y }) - (\mu_{1}-\mu_{2})}{\sigma\sqrt{\frac{1}{n_{1}}+\frac{1}{n_{2}}  }}
$$
Now, we simply want to find a estimator for the common $\sigma$, we can do so using the t-dist! Consider the sample means once again, let us use it to form a common sample variance, $S_p$. 
$$
\begin{align}
S_{p}^2 &= \frac{(\sum{X_{i}-\bar{X})^2}+ \sum{(Y_{i}-\bar{Y})^2} }{n_{1}+n_{2}-2} \text{ ( We basically add all the data up like we did with a normal mean.)}\\
&= \frac{S_{1}^2(n_{1}-1) + S_{2}^2(n_{2}-1) }{n_{1}+n_{2}-2} \text{ (Rearrange Sample Mean Formulas)}
\end{align}
$$
From previous lectures we know that:
$$W=\chi_{n_{1}+n_{2}-2} = \frac{(n_{1}+n_{2}-2)S_{p}^2}{\sigma^2}$$
Using this, since we have a normal, and a chi dist, we can derive a student t distibution, we can finally plug them all in(simplified)
$$
T= \frac{T}{\sqrt{ \frac{W}{v} }} = \frac{(\bar{X}-\bar{Y }) - (\mu_{1}-\mu_{2})}{ S_{p}\sqrt{ \frac{1}{n_{1}}+\frac{1}{n_{2}} }}
$$
So, we have a pivotal quantity that estimates $u_1-u_{2}$(I think?), and just using it like previous parts we finally get the fact that, our confidence interval is:
$$
C.I = \left( \bar{X}-\bar{Y} \pm t_{\frac{\alpha}{2}}S_{p}\sqrt{ \frac{1}{n_{1}}+\frac{1}{n_{2}} } \right)
$$
a GOOD summary:
![[Pasted image 20241101180227.png]]
### Confidence Interval for stnd. dev
you literally just use a chi distribution, there is no trick, the interval simplifies out as for $\sigma^2$
$$C.I = [\frac{(n-1)S^2}{\chi^2_{1-\frac{\alpha}{2}}},\frac{(n-1)S^2}{\chi^2_{\frac{\alpha}{2}}}] $$

# Review of previous - Consistency 
### Review of Consistency/Dev.
**Limiting Theorems**:  
Let $X_{1},X_{2},\dots.$ be a independent sequence of random variable with:
$$
E[X_{i}] = \mu, Var(X_{i}) = \sigma^2
$$
Then for convergence in probability:
$$
X_{n} \Rightarrow^{P} X \leftrightarrow \lim_{ n \to \infty } P[|X_{n}-X| \geq \epsilon]=0
$$
**Weak Law of large numbers(WLLN)**
For the sample mean $\bar{X_{n}}=\frac{1}{n} \sum_{{n}}^{n}X_{i}$, the following holds, let's prove it:
$$\bar{X_{n}} \Rightarrow^P \mu$$
![[Pasted image 20241007113936.png]]
Then, $\lim_{ n \to \infty } P[|X_{n}-\mu| \geq \epsilon]=0$, but note how $\mu$ is not a random variable, but it is, as it is a degenerate random variable!
Recall **chebysev's inequality:**
$$ \begin{align}
\forall \epsilon > 0, P[|X-E[X]| \geq \epsilon] \leq \frac{Var(X)}{\epsilon^2}\\ \\
P[|\bar{X_{n}}-E[\bar{X_{n}}]| \geq \epsilon] & \leq \frac{Var(\bar{X_{n}})}{n\epsilon^2}\\ \\
 \lim_{ n \to \infty } P[|\bar{X_{n}}-E[\bar{X_{n}}]| \geq \epsilon] & \leq  \lim_{ n \to \infty }  \frac{Var(\bar{X_{n}})}{n\epsilon^2} \\
& \leq 0 \\ \\
\bar{X_{n}} \rightarrow^P \mu
\end{align}$$
This gives us the following:
**Lemma:** If $E[X_n]=c$, then $X_n \rightarrow^p c$ if $\lim_{ n \to \infty } Var(X_n) = 0$, where $X_n$ is any sequence of random variables.
Now, recall the following
$$
X_{n} \rightarrow^p X \text{ and } Y_{n} \rightarrow^p Y \Rightarrow X_{n}+Y_{n} \rightarrow^p X+ Y 
$$
If c is also a constant, then
$\text{ if } X_{n} \rightarrow^p X \Rightarrow cX_{n} \rightarrow^p cX$
**Continuous Mapping Theorem**
$$ X_{n} \rightarrow^p c \Rightarrow g(X_{n}) \rightarrow^p g(c)$$
There $g$ is a continuous function at c. 
**Weak Law of Large Numbers**
Consider the standard $\bar{X_{n}}$ definition and we showed that:
$$\bar{X_{n}} \rightarrow^p E[X]$$
$$
\begin{align}
\bar{X_{n}} &= \frac{1}{n} \sum_{{i=1}}^{n} X_{i} \rightarrow \bar{X_{n}} \Rightarrow^p E[X_{1}]\\ 
\bar{X^2} &= \frac{1}{n} \sum_{{i=1}}^{n} X_{i^2} \rightarrow \bar{X^2} \Rightarrow^p E[X_{1}^2]\\  
\end{align}
$$
- For the end, we consider $n/n-1$ as a degenerate function, that goes to 1 with a larger n.
- ![[Pasted image 20241007121759.png]]
- Convergence tells you that the long run, the chance that you miss goes to near 0.
**Convergence in distribution**
Let $X_{1},X_{2},\dots.$ be a independent sequence of random variable with with CDF= $F_{X_n}$ and X is a target random variable with $CDF =F_X(x)$,  then if:
$$\lim_{ n \to \infty }  F_{X_{n}}(x) = F_{X}(x) \Leftrightarrow X_{n} \rightarrow^D X$$
![[Pasted image 20241007122527.png]]

If, one converges in probability, it does in dist:
$$X_{n} \rightarrow^p X \Rightarrow X_{n}\rightarrow^D X$$
If 
$$X_{n} \rightarrow_{D} constant. \Rightarrow X_{n} \rightarrow_{p} consant$$**Theorem: $The \triangle method**$
**Let us have it so**
**$$\sqrt{ n } (X_{n}-\theta) \rightarrow_{D} N(0,\sigma^2)$$**
**Let $g(x)$ be a differentiable at $\theta$**, and $g'(\theta) \neq 0$, then:
$$ \sqrt{ n } (g(X_{n}) - g(\theta)) \rightarrow^D N(0,\sigma^2 (g'(\theta))^2 )$$

**Slutsky's Lemma**:
If $X_n \rightarrow_{D} X$ and $Y_{n} \rightarrow_{P} c$, then we can derive the following:
$$X_{n} + Y_{n} \rightarrow_{D} X+c$$
$$X_{n}Y_{n} \rightarrow_{S} cX$$
$$\frac{X_{n}}{Y_{n}} \rightarrow_{D} \frac{X}{c}, c \neq 0$$
**Example:**
![[Pasted image 20241007124639.png]]
### Why does this matter
A estimator $\hat{\theta}_{n}$ is said to be a consistent estimator of $\theta$ if for any positive number $\epsilon$ :
$$
\lim_{ n \to \infty } P(|\hat{\theta}_{n} - \theta| \leq \epsilon) = 1 
$$
Or, equivalently:
$$
\lim_{ n \to \infty } P(|\hat{\theta}_{n} - \theta| \geq \epsilon) = 0 
$$
On top of this, a unbiased estimator $\hat{\theta}_{n}$ for $\theta$ is a consistent estimator of $\theta$ if:
$$\lim_{ n \to \infty } V(\hat{\theta}_{n})=0$$
Using the above theorems above consistent estimators, we can then form more using the blow theorems.
Suppose that $\hat{\theta}_{n}$ converges to probability to $\theta$ and that $\hat{\beta_{n}}$ converges to $\beta$
1. $\hat{\theta}_{n} + \hat{\beta}_{n}$ converges to $\theta + \beta$
2. $\hat{\theta}_{n} \times \hat{\beta}_{n}$ converges to $\theta \times \beta$
3. If $\hat{\theta}_{n} \neq 0$, then $\frac{\hat{\theta}_{n}}{\hat{\beta}_{n}}$ converges to $\frac{\theta}{\beta}$
4. If we have a function that is continuous at $\theta$, then $g(\hat{\theta}_{n})$ converges in probability to $g(\theta)$


# Eff in Statistics.
If $\hat{\theta_{1}}$ and $\hat{\theta_{2}}$ are unbiased estimators of $\theta$  
**Efficiency of $\hat{\theta_{1}}$ relative to $\hat{\theta_{2}}$ * is given by*
$$
eff(\hat{\theta_{1}},\hat{\theta_{2}}) = \frac{Var(\hat{\theta_{2}})}{Var(\hat{\theta_{1}})}
$$
If $eff(\hat{\theta_{1}},\hat{\theta_{2}})>1$, then $\hat{\theta_{1}}$ is preferred as $Var(\hat{\theta_{2}})>Var(\hat{\theta_{1}})$.
##### Example
![[Pasted image 20241010101842.png]]
![[Pasted image 20241010103539.png]]
- We use the estimator using the maximum and multiply by the coefficient $\frac{n+1}{n}$ which is always greater then 1, to fix it.
#### Example 2
![[Pasted image 20241010105329.png]]
- The second estimator is still biased, but is unbiased **asymptotically** for a large n.
# How to find estimators?
Is there a systematic way to find estimators?
**Method of Moments(MOM)**
MOM is a systematic approach to find estimators
- The following is the $kth$ population (theoretical) mean
$$
\mu'_{k} = E[Y^k]
$$
- The following is the $k^{th}$e sample (emperical)
$$ m'_{k} = \frac{1}{n}\sum_{i=1}^n Y_{i}^k$$
### Example

![[Pasted image 20241017104248.png]]

# Maximum Likelihood Estimation(MLE)
MLE procedures are asymptotically optimal under regulating conditions
$$
Y_{1},Y_{2},\dots Y_{n} \sim^{iid} f(y: \theta) \theta \in \Omega \text{ (Paramaterized)}
$$

$$
\begin{align}
L(\theta|y_{1},y_{2,\dots y_{n}})]=f_{Y_{1},Y_{2},\dots.Y_{n}} = \Pi^{n}_{i=1}{ (y_{i})| \theta)}
\end{align}
$$
How likely (plausible ) is it that the specific value of $\theta$ has been the parameter of the pdf when the sample of realized, where L is the likeleihood function.
#### Example
Let $$Y_{1},Y_{2},\dots Y_{n} \sim^{iid} f(y) = \theta^y (1-\theta)^{1-y}$$
Where $y=0,1$ and $0 \leq \theta \leq 1$.
![[Pasted image 20241021111957.png]]
Here we can use the log-likelihood function:
$$
\begin{align}
L(\theta) &= \log(L(\theta))\\ \\
l(\theta)&= \left( \sum y_{i} \right) + \log(\theta) + \left( n-\sum y_{i} \right) \log(1-\theta) \\ \\
\frac{\partial l(\theta)}{\partial \theta} &= 0 \\ \\
\frac{\left( \sum y_{i} \right)}{\theta} - \frac{\left( n-\sum y_{u} \right)}{1-\theta } &= 0 \\ \\
n \theta &= \sum y_{i}\\ \\
\widehat{\theta}&= \bar{Y}
\end{align}
$$
Be careful to write $\hat{\theta}$ in terms of uppercase letters
![[Pasted image 20241021113901.png]]
![[Pasted image 20241021113918.png]]

Sometimes we want to estimate mu to the power of two, etc. All we need to do is use the values we have and substitute
**Invariance property**: If $\hat{\theta}$ is the MLE of $\theta$, then $g(\hat{\theta})$ is the MLE of $g(\theta)$.
So the MLE of $\mu^2=\\bar{}{Y}^2$

### Example ![[Pasted image 20241021115443.png]]
**Regularity Condition:** Support of a r.v should not depend on $\theta$:
$$
\begin{align}
\hat{\theta} &= Argmax(L(\theta)) = Agmax(l(\theta))\\ \\
\frac{\partial l(\theta)}{\theta \partial} &= 0 \text{ estimating equation}
\end{align}
$$If the support depends on $\theta$, differential calculus is useless.
![[Pasted image 20241021121709.png]]
# Cramer Ras Low Bound and Effciency
Let $$
Y_{1},Y_{2},\dots Y_{n} \sim^{iid} f(y: \theta) \theta \in \Omega \text{ (Paramaterized)}
$$
Recall that:
$$
\int_{-\infty}^{\infty} f(y;\theta)dy = 1 
$$
If we differentiate this with theta:
$$
 \frac{\partial}{\partial \theta}\int_{-\infty}^{\infty} f(y;\theta)dy = 0 
$$

Under the regularity condition we get that:
$$
 \int_{-\infty}^{\infty} \partial \frac{f(y;\theta)dy}{\partial \theta} = 0 
$$
Let us now multiply and divide by the PDF:
$$
 \int_{-\infty}^{\infty} \frac{\partial \frac{f(y;\theta)dy}{\partial \theta}}{f(y;\theta)} f(y: \theta) = 0 
$$
If we consider the numerator which is the derivative divided by the function itself, recall that $\ln(u)= \frac{u'}{u}$. 
$$
 \int_{-\infty}^{\infty} \frac{\partial \log(f(y;\theta)) }{\partial \theta} f(y: \theta) dy = 0 
$$
This can now be seen as an expectation:
$$E[ \frac{\partial \log(f(y;\theta))}{\partial \theta}] = 0 $$

We call $" \frac{\partial \log(f(y;\theta))}{\partial \theta}"$ the "score function".
$\frac{\partial \log(f(y;\theta))}{\partial \theta}$  is a random variable.
We use the "score function" to find the estimation equations for MLE:
$$\sum_{i=1}^{n} \frac{\partial \log(f(y;\theta))}{\partial \theta} = 0 $$
Let's rewrite the last equation and difference to $\theta$:
$$
 \int_{-\infty}^{\infty} \frac{\partial \log(f(y;\theta)) }{\partial \theta} f(y: \theta)  = 0 
$$
Differentiating..
$$
 \int_{-\infty}^{\infty} \frac{\partial^2 \log(f(y;\theta)) }{\partial \theta^2} f(y: \theta)  dy + \int_{-\infty}^{\infty} \frac{\partial^2 \log(f(y;\theta)^2) }{\partial^2 \theta^2} f(y: \theta)  dy= 0 
$$
We call the second term the Filshur information:
$$ \int_{-\infty}^{\infty} \frac{\partial^2 \log(f(y;\theta)^2) }{\partial^2 \theta^2} f(y: \theta) dy = I(\theta)$$
This is simply the expectation of the previous function squared:
$$I(\theta)= E[\frac{\partial^2 \log(f(y;\theta)^2) }{\partial^2 \theta^2}]$$
Alternatively:
$$I(\theta) = -\int_{-\infty}^{\infty} \frac{\partial^2 \log(f(y;\theta)) }{\partial \theta^2} f(y: \theta)  dy  = -E[\int_{-\infty}^{\infty} \frac{\partial^2 \log(f(y;\theta)) }{\partial \theta^2} ]$$![[Pasted image 20241021124521.png]]
If $\theta \rightarrow 0 \Rightarrow I(\theta) \text{ increases}$, and if $\theta \rightarrow 1 \Rightarrow I(\theta) \text{ increases}$
![[Pasted image 20241021125157.png]]

 
# Hypothesis Testing
Hypoth