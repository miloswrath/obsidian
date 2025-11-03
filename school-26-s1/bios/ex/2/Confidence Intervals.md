## Definitions
---
- *Point Estimate* - A single stastic collected from the **sample**
- *Interval Estimate* - An interval computed from sample parameter to have a higher degree of confidence of the true population parameter
- $\alpha$ - a small number chosen by researcher that is the outer percentage of confidence
- $100(1-\alpha)$ - is the *confidence level* (e.g. if $\alpha = .05$ then its a $95\%$ CI)



## Two-Sided CIs
---
**General Formula**
$P(\bar{y}_n -z_{\alpha/2}\cfrac{\sigma}{\sqrt{n}}, \ \bar{y}_n + z_{\alpha/2}\cfrac{\sigma}{\sqrt{n}})$ 
Where $\bar{y}_n$ is the sample statistic, 


## One-Sided CIs
---
> Essentially just have one sided = $+\infty$ or $-\infty$ 

**General Formula (Upper as e.g. but flip for lower)**
$P(-\infty, \ \bar{y}_n + z_{\alpha}\cfrac{\sigma}{\sqrt{n}})$



## Sample Size Estimation
> Suppose we want to find the sample size n needed so that the margin of error does not exceed some value k. Accordingly, we want to find the sample size n needed so that the width of a two-sided confidence interval does not exceed 2k.

Take:
$n\ge(\cfrac{z_{\alpha/2}\sigma}{k})^2$


## Small Sample Sizes
---
> When $n<30$ we use T-Distribution

Just plug in $t_{n-1}$ for $z$
$P(\bar{y}_n -t_{(n-1), \ (\alpha/2)}\cfrac{\sigma}{\sqrt{n}}, \ \bar{y}_n + t_{(n-1), \ (\alpha/2)}\cfrac{\sigma}{\sqrt{n}})$ 
or
$P(-\infty, \ \bar{y}_n + t_{(n-1), \ (\alpha)}\cfrac{\sigma}{\sqrt{n}})$
