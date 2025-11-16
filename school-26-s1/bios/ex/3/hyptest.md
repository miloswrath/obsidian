
## General Concepts
---

*Statistical Hypothesis* - claim about an unknown parameter

*Null Hypothesis* - What is assumed to be true before experiment is conducted
	Typically that the wanted result isn't true, there is no difference etc.

### Types of Errors in HTs
---
**Type I** - when the null hypothesis is true but we reject
**Type II** - Null hypothesis is false but we retain

**Power $(1 - \beta)$** = $P(\text{Retain} \ H_0 \ | \ H_0 \ \text{false} )$

## Hypothesis Testing
---

> Steps and definitions for conducting hypothesis testing

### Steps
---
1. Label and describe parameters of interest ($\mu, \ \sigma \ \text{or} \ s, \ \text{etc.}$)
2. State $H_0$ and $H_A$ 
3. Select $\alpha$
4. Specify the **test statistic** to be used (a number used to decide to retain or reject null hypothesis)
5. Compute test statistic (defined below)
6. Compute the **p-value** (defined below) based on:
	1. the form of $H_A$
	2. the numerical value of the test statistic
7. Arrive to conclusion by either:
	1. comparing the p-value to $\alpha$
	2. determining whether the test statistic falls in the **rejection region**

### Definitions
---
**p-value** - The p-value (probability value) addresses the following question. Assuming H0 is true, how likely would it be to observe a test statistic as extreme or more more extreme than the one we obtained in our study?

**rejection region** - region on the outside of crit values where you would reject null hypothesis


## Types of Errors and Power
---
> Researchers want to know the chance of rejecting $H_0$ - so power is used to do that

*Type II Error*
$\beta = P(\text{Retain } H_0 \ | \ H_A \text{True})$

*Power*
$1 - \beta$ (above)
Probability Reject $H_0$ given $H_A$ is True

> Power calculation is conducted on a certain $\mu_A$ or $\mu_0$ so differing values for this lead to different powers. This requires some simulation to be conducted during practice

**You can increase $\beta$ by either *Increasing Sample Size* or *Increase $\alpha$*** 

$|\mu_\alpha - \mu_0|$ = **effect size** 

## Sample Size Estimation
---




## Classic Formulae
---

**Z-Test**
$$
Z = \cfrac{\bar{x} - \mu_0}{\sigma/ \ \sqrt{n}}
$$
This you compare against the value at $\alpha$ or $\alpha/2$ level. If $|Z| > \alpha$ then you reject the $P(Z)$ is the p-value

**T-Test**

$$
t = \cfrac{\bar{x} - \mu_0}{s \ \sqrt{n}}
$$
Here $t$ is based on $n-1$ dof. make sure to use that











































