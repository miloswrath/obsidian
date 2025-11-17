# Inference on Proportions
---
**Proportions Review**
$X$ can be a *sucess* or *failure*.
The **proportion of succsses** $\hat{p} = x/n$ where $x$ is the number of successes and $n$ is the number of observations

## Sampling Distribution
---
$\hat{p}$ is an *estimator* of the population proportion $p$

### Properties of $\hat{p}$
---
- The mean (or $E[X]$) of $\hat{p}$ is the same as the population proportion $p$
- S.D. is $\sqrt{p(1-p)/n}$
	- This is often called the **standard error of the proportion**
	- Essentially reflects the accuracy of $\hat{p}$ in estimating $p$
**Central Limit Theorem**
If $np \ge 5$ and $n(1-p) \ge 5$ then central limit applies

## Confidence Interval
---
**Formula**
$$\hat{p} \ \pm \ z_{\alpha/2} \sqrt{\cfrac{\hat{p}(1-\hat{p})}{n}}$$ 
> For upper and lower, remember it's from [0, 1]

## Hypothesis Testing
---
**Formula**
$$ z = \cfrac{\hat{p} - p_0}{\sqrt{\cfrac{p_0(1-p_0)}{n}}} $$
**p-value calculation**

| $H_A$       | p-value          |
| ----------- | ---------------- |
| $p \ne p_0$ | $2P(Z > \|z\| )$ |
| $p > p_0$   | $P(Z > z)$       |
| $p < p_0$   | $P(Z<z)$         |

**Rejection Region**
| $H_A$         | Rejection Region                                      |
|-----------------|--------------------------------------------------------|
| $p \neq p_0$ | $z < -z_{\alpha/2}$ **or** $z > +z_{\alpha/2}\)     |
| $p > p_0$     | \(z > +z_{\alpha}\)                                    |
| $p < p_0$    | \(z < -z_{\alpha}\)                                    |

## Sample Size Estimation
---



## Comparison of Two Proportions
---
