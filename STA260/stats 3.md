# Hypothedsis testing
If we have $\theta \in \Omega$ 
**Goal**: test the "null hypothesis".$H_{o}$ and alternate, $H_{a}$.
If $\Omega_{i}$ or $\Omega_{a}$ contains one point(it is a singleton), then it is called a "simple hypothesis". Otherwise, we all in the "composite hypothesis".

"composite hypothesis"
$\theta_{a}, \theta=70$ simple
$\theta_{o}, \theta>70$ composite
## Decision Rule
If $D=space\{ Y_{1},\dots Y_{n}\}$ space of the sample. A 'ten' of $H_{o}$ and $H_{a}$ is based on a subset C of D.

The set C is called the "critical region" or "rejection region" and its corresponding "decision rule" is:

- Reject $H_{o}$ (accept $H_{a}$) if $(y_{1}\dots y_{n} \in C)$
- Reject $H_a$ (reject $H_{a}$) if  $(y_{1}\dots y_{n} \in C^C)$
![[Pasted image 20241111114331.png]]

If you to minimize one, the other will increase, if you want to increase the other, then the other will increase.

Ideally, we want to select a critical region from all possible critical regions which minimize the possibilities of both

Type I and Type II errors -> This in general is not possible ( seaside effect)
- We've seen this with our error of estimators
