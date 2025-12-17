> Only Stuff from most recent chapter, most should be theory and less formulae

### *Contingency*
---
**Test of $\chi^2$**
All cell counts need to be $\ge 5$
$\chi^2 \approx P(\chi^2 > \chi_{df}^2)$ $\text{df} = (r-1)(c-1)$ $r, c$ is dimensionality of table

**McNemar - Paired Samples**
Using *discordant pairs* $(r, s)$ - assume $R \approx Bin(r+s, \  p = 0.5)$ - test $H_0: p = 0.5$
*Test Statistic* ~ $\chi^2 = \cfrac{(|r - s| - 1)^2}{r+s}$ ~ $\chi_1^2$ ~ when ~ $r + s \ge 10$

**Odds Ratio**
$\hat{OR} = \cfrac{n_{11}n_{22}}{n_{12}n_{21}}$, $\hat{RR} = \cfrac{n_{11}*(n_{12}+n_{22})}{n_{12}*(n_{11}+n_{21})}$
*Relative Risk: the ratio of the probabilities of disease comparing exposed to unexposed*
> If a disease is rare, thus the values of $n_{11}$ and $n_{12}$ are small relative to the values of $n_{21}$ and $n_{22}$, then the relative risk can be approximated by the odds ratio.

> ***Come back to more theory here??***

### *Correlation*
---
**Pearson's $r$**
*$[-1, 1]$ magnitude of linear relationship*
- Not robust, can be influenced by outliers
- If R tests $H_0 = true$ then assume independence is fine
- *Requires Normality*
*Spearman's $r$*
**Need to Calculate**
*Measures the strength of monotonic rank relationship*
- Does not require normality, and is robust
~ Do the rank squared difference thing then :LiArrowRight: $1-\cfrac{6}{n(n^2-1)}\sum{d_i^2}$ 
![[Pasted image 20251217123008.png]]

### OLS
---


### *Standardization*
---
