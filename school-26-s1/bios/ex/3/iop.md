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

| $H_A$        | Rejection Region                               |
| ------------ | ---------------------------------------------- |
| $p \neq p_0$ | $z < -z_{\alpha/2}$ **or** $z > +z_{\alpha/2}$ |
| $p > p_0$    | $z > +z_{\alpha}$                              |
| $p < p_0$    | $z < -z_{\alpha}$                              |

## Sample Size Estimation
---
> Suppose we want to find $n$ s.t. our ME doesn't exceed some value $m$

We are looking for an n s.t.
$$
z_{\alpha/2}\sqrt{\cfrac{\hat{p}(1-\hat{p})}{n}}\le m
$$
**Solution**
$$
n \ge \Bigg(\cfrac{z_{\alpha/2}\sqrt{\hat{p}(1-\hat{p})}}{m}\Bigg)^2 
$$
> But we don't know $\hat{p}$ yet!
> So we can use $\hat{p} = 0.5$ since $\hat{p}(1-\hat{p})$ maxes out at 0.5

**Thus**
$$
n \ge \bigg( \cfrac{z_{\alpha/2}* 0.5}{m}\bigg)^2
$$
#### Sample Size Using Power

**Suppose**
We want to test some $p_A$ s.t. the effect size $|p_A - p_0|$ is reached and we have a power above $(1 - \beta)$ 
**We Need:**
1. $\alpha$ and $\beta$
2. crits either $z_\alpha$ or $z_{\alpha/2}$ for one-sided / two-sided respectively
3. crit vale $z_\beta$
4. hypothesized proportions $p_A  \ \text{and } p_0$ 

$$
\text{For a two-sided test, take:} \quad
n \ge 
\left(
\frac{
z_{\alpha/2}\sqrt{p_0(1-p_0)} 
\;+\;
z_{\beta}\sqrt{p_A(1-p_A)}
}{
|p_A - p_0|
}
\right)^2
$$

$$
\text{For a one-sided test, take:} \quad
n \ge 
\left(
\frac{
z_{\alpha}\sqrt{p_0(1-p_0)} 
\;+\;
z_{\beta}\sqrt{p_A(1-p_A)}
}{
|p_A - p_0|
}
\right)^2
$$

## Comparison of Two Proportions
---
> ***Requires Independent Samples***


---
### One-Sided Confidence Interval for \( (p_1 - p_2) \)

A level \(100(1-\alpha)\%\) one-sided confidence interval based on the Z distribution is:

**Lower bound:**

$$
\left(
(\hat{p}_1 - \hat{p}_2)
-
z_\alpha
\sqrt{
\frac{\hat{p}_1(1-\hat{p}_1)}{n_1}
+
\frac{\hat{p}_2(1-\hat{p}_2)}{n_2}
},
\;
1
\right)
$$

**Upper bound:**

$$
\left(
-1,\;
(\hat{p}_1 - \hat{p}_2)
+
z_\alpha
\sqrt{
\frac{\hat{p}_1(1-\hat{p}_1)}{n_1}
+
\frac{\hat{p}_2(1-\hat{p}_2)}{n_2}
}
\right)
$$

---

### Two-Sided Confidence Interval for \( (p_1 - p_2) \)

A level \(100(1-\alpha)\%\) two-sided CI is:

$$
(\hat{p}_1 - \hat{p}_2)
-
z_{\alpha/2}
\sqrt{
\frac{\hat{p}_1(1-\hat{p}_1)}{n_1}
+
\frac{\hat{p}_2(1-\hat{p}_2)}{n_2}
},
$$

$$
(\hat{p}_1 - \hat{p}_2)
+
z_{\alpha/2}
\sqrt{
\frac{\hat{p}_1(1-\hat{p}_1)}{n_1}
+
\frac{\hat{p}_2(1-\hat{p}_2)}{n_2}
}
$$


### Test Statistic for Two Proportions

The z-test statistic is:

$$
z
=
\frac{\hat{p}_1 - \hat{p}_2}{
\sqrt{
\hat{p}(1-\hat{p})\left(\frac{1}{n_1} + \frac{1}{n_2}\right)
}
}
$$

where the pooled proportion is:

$$
\hat{p}
=
\frac{n_1\hat{p}_1 + n_2\hat{p}_2}{n_1 + n_2}
$$

**Large-sample condition:**

$$
n_1\hat{p}_1 \ge 5,\quad
n_1(1-\hat{p}_1) \ge 5,\quad
n_2\hat{p}_2 \ge 5,\quad
n_2(1-\hat{p}_2) \ge 5
$$

### Rejection Regions

| $H_A$          | Rejection Region                              |
| -------------- | --------------------------------------------- |
| $p_1 \neq p_2$ | $z < -z_{\alpha/2}$ **or** $z > z_{\alpha/2}$ |
| $p_1 > p_2$    | $z > z_{\alpha}$                              |
| $p_1 < p_2$    | $z < -z_{\alpha}$                             |


### p-values

| $H_A$          | p-value    |     |     |
| -------------- | ---------- | --- | --- |
| $p_1 \neq p_2$ | $2P(Z >    | z   | )$  |
| $p_1 > p_2$    | $P(Z > z)$ |     |     |
| $p_1 < p_2$    | $P(Z < z)$ |     |     |
