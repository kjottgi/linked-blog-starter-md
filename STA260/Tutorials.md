Given a point estimator $\hat{\theta}$ for the paramater $\theta $, the bias is calculated by $$B[\hat{\theta}] = E[\hat{\theta}]-\theta$$

We say a point estimator if the above is 0.
##### Q1
$$\begin{align}
B[\hat{\mu}]&= E[\hat{\mu}]-\mu \\
\hat{\mu}&= X_{(1)}\\ \\
P(X_{i} \leq 1) &= 1 - (PX_{(1)}>x)\\ \\
&= 1 - P(X_{1}>x)\dots P(X_{n}>x)\\ \\
&= 1 - (P(X_{1 }>x))^n\\ \\
&= 1 - (1-P(X_{1}<x))\\ \\
f_{X}(x) &= n (1-F_{X}(x))^{n-1} f_{X}(x)\\ \\
F_{X}(x) &= \int_{\mu}^{x} e^{-t+\mu}dt\\ \\
&= e^\mu \int_{\mu}^{x} e^{-t} dt\\ \\
&= e^\mu (-e^x + e ^{-\mu})\\ \\
&= 1 - e^{\mu-x}\\ \\
F_{X}(x) &= n (1 - 1 + e^{\mu+x})^{n-1}e^{\mu-x}\\ \\
&= n (e^{\mu+x})^{n-1}e^{\mu-x}\\ \\
&= ne^{\mu n}e^{-xn}\\ \\
E[\hat{\mu}] &= \int_{\mu}^{\infty} xne^{\mu n}e^{-xn} dx \\
&= ne^{n\mu} \int_{\mu}^{\infty} xe^{-nx}\\ \\
&= [\text{ integration by parts... }]\\ \\
&= ne^{n\mu}\left[ \frac{-xe^{-nx}}{x}- (\frac{e^{-nx})}{n} \right] |^{\infty}_{\mu} \\
&= ne^{n\mu}[ 0 + 0 +  \frac{\mu e^{n\mu}}{n}+ \frac{e^{-n\mu}}{n^2}]\\ \\
&= \frac{n\mu}{n} + \frac{1}{n}\\  \\
&= \mu + \frac{1}{n}\\ \\ \\
B[..] &= \mu + \frac{1}{n} - \mu\\ \\
&= \frac{1}{n}
\end{align}$$
- You can use l-hopital's for the latter part to show it goes to 0.
- Review Integration by parts, you can review
#### Q2
$$\begin{align}
MSE(\widehat{\theta}) &= Var(\widehat{\theta})- [B(\widehat{\theta})]^2 \\
&= Var(\hat{\mu}) -\left( \frac{1}{n} \right)^2\\ \\
Var(\hat{\mu}) &= E[\hat{\mu}^2]-E[\hat{\mu}]^2\\ \\
E[\hat{\mu}^2]&= \int_{\mu}^{\infty} x^2 n e^{\nu} e^{-nx} dx\\ \\
&= ne^{\nu} \int_{\mu}^{\infty} x^2 e^{-nx} dx\\ \\
&= [\text{Two intergration by parts, use a table.}]\\ \\
&= ne^{n\mu} \left[  \frac{-xe^{-nx}}{n} - \frac{2xe^{-nx}}{n^2} - \frac{2e^{-nx}}{n^3}\right] |^{\infty}_{\mu}\\ \\
&= \mu^2 + \frac{2\mu}{n} + \frac{2}{n^2}\\ \\
Var(\hat{\mu})&- \mu^2 + \frac{2\mu}{n } + \frac{2}{n^2} - \left( \mu + \frac{1}{n} \right)^2 \\
&= \frac{1}{n^2}\\ \\
Mse(\hat{\mu})&= 1 / n^2 + 1 / n^2 \\ \\
&= \frac{2}{n^2}
\end{align}\\

$$
# Q3
$$\begin{align}
E[\hat{\theta_{1}}] &= E[\hat{Y}] - \frac{1}{2}\\  \\
&= \frac{\theta + \theta + 1 }{2} -\frac{1}{2}\\ \\
&= \frac{2\theta + 1}{2} - \frac{1}{2}\\ \\
&= \theta\\
E[\hat{\theta_{2}}] &=  E[Y_{(n)}] - \frac{n}{n-1}\\ \\
Y_{(n)}&= [P(Y_{n \leq y})]^n \\ \\
f_{Y_{(n)}}(y) &= nF_{Y}(y)^{n-1} f_{Y}(y)\\ \\
f_{Y}(y) &= \frac{1}{\theta + 1 - \theta}= 1\\ \\
F_{Y}(y) &= \int_{\theta}^y 1 dt\\ \\
&= y - \theta \\ \\
f_{Y_{(n)}}(y) &= n(y - \theta)^{n-1} (1)\\ \\ \\
E[Y_{(n)}] &= \int_{\theta}^{\theta+1} yn(y-\theta)^{n-1} dy\\ \\
&= [\text{use  u sub with u = y - theta, du=dv}] \\
&= n \int_{0}^{1} u^n + \th\eta y^{n-1} du\\ \\
&= \dots.[ \text{ I cba to write this, just look at pics}]\\ \\
&= \frac{n}{(n+1)}\\ \\
E[\theta_{2}] = \th\eta
\end{align}$$
