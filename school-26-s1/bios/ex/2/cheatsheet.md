*Symbols*

| Symbol                      | Meaning            |     | Symbol   | Meaning          |
| :-------------------------- | :----------------- | :-- | :------- | :--------------- |
| $X,\ x$                     | RV, its value      |     | $\bar X$ | Sample mean      |
| $\mu,\ \sigma^2,\ \sigma$   | Mean, variance, SD |     | $E[X]$   | Expectation      |
| $z_\alpha,\ t_{n-1,\alpha}$ | Critical values    |     | $\alpha$ | Tail area (1–CL) |
*Theory*

| Concept             | Summary                                                       |
| :------------------ | :------------------------------------------------------------ |
| **Random Variable** | Discrete (countable) or continuous (infinitely many) outcomes |
| **PMF/PDF**         | $p(x)=P(X=x)$ or $f(x)$ s.t. $\int f(x)\,dx=1$                |
| **Expected Value**  | $E[X]=\sum x\,p(x)$ or $\int x f(x)\,dx$                      |
| **Variance**        | $Var(X)=E[(X-\mu)^2]$                                         |
| **CLT**             | $\bar X \sim N(\mu,\sigma^2/n)$ for large $n$ ($\ge30$)       |
| **CI Concept**      | Range where parameter likely lies; wider = more confident     |
*Distributions*

| Dist. | When / Use | Parameters | $E[X]$ | $Var(X)$ | Formula |
|:--|:--|:--|:--|:--|:--|
| **Bernoulli** | 1 trial, success/fail | $p$ | $p$ | $p(1-p)$ | $P(X=1)=p$ |
| **Binomial** | $n$ indep. Bernoulli | $n,p$ | $np$ | $np(1-p)$ | $\binom{n}{x}p^x(1-p)^{n-x}$ |
| **Poisson** | # of rare events | $\lambda$ | $\lambda$ | $\lambda$ | $\frac{e^{-\lambda}\lambda^x}{x!}$ |
| **Normal** | Continuous, bell curve | $\mu,\sigma^2$ | $\mu$ | $\sigma^2$ | $\frac{1}{\sigma\sqrt{2\pi}}e^{-(x-\mu)^2/(2\sigma^2)}$ |


*Core Formulas (Grouped)*

| Category                       | Formula                                                   | Notes                   |
| :----------------------------- | :-------------------------------------------------------- | :---------------------- |
| **Binomial PMF**               | $P(X=x)=\binom{n}{x}p^x(1-p)^{n-x}$                       | discrete, 0–$n$         |
| **Binomial Coeff.**            | $\binom{n}{k}=\frac{n!}{k!(n-k)!}$                        | # of combinations       |
| **Poisson PMF**                | $P(X=x)=e^{-\lambda}\lambda^x/x!$                         | mean=var=λ              |
| **Z-Score**                    | $Z=\frac{X-\mu}{\sigma}$                                  | standardize any normal  |
| **SE (Mean)**                  | $\frac{\sigma}{\sqrt n}$                                  | sample mean variability |
| **SE (Proportion)**            | $\sqrt{\frac{p(1-p)}{n}}$                                 | use $\hat p$ if unknown |
| **Normal Approx. to Binomial** | $Z=\frac{x+0.5-np}{\sqrt{np(1-p)}}$                       | CC +0.5                 |
| **CLT Dist.**                  | $\bar X\sim N(\mu,\sigma^2/n)$                            | for means               |
| **CI (Z-known)**               | $\bar X\pm z_{\alpha/2}\frac{\sigma}{\sqrt n}$            | two-sided               |
| **CI (T-unknown)**             | $\bar X\pm t_{n-1,\alpha/2}\frac{s}{\sqrt n}$             | small $n$               |
| **One-Sided CI**               | $\bar X+z_\alpha\frac{\sigma}{\sqrt n}$                   | flip for lower          |
| **Sample Size**                | $n\ge(\frac{z_{\alpha/2}\sigma}{k})^2$                    | margin $k$              |
| **Prop. CI**                   | $\hat p\pm z_{\alpha/2}\sqrt{\frac{\hat p(1-\hat p)}{n}}$ | large $n$               |

*Quick Reference Table*

| CL $(1-\alpha)$ | $z_{\alpha/2}$ | Coverage | Comment |
|:--|:--:|:--|:--|
| 90% | 1.645 | 0.90 | narrowest |
| 95% | 1.96 | 0.95 | standard |
| 99% | 2.576 | 0.99 | widest |

*Quick Notes*
- **CI Interpretation:** 95% → in long run, 95% of such CIs contain true mean.  
- **Increasing CL ⇒** larger $z_{\alpha/2}$ ⇒ wider CI.  
- **Poisson ≈ Binomial:** when $n>20$, $p<0.05$.  
- **Sketch shapes:** Binomial (bumps), Poisson (right-skew→normal), Normal (bell).  
- **Check assumptions:** independence, fixed $n$, constant $p$, proper model.
