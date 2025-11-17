# Comparison of Means
---
> Comparing two means - covers:
> - Dependent Samples (paired)
> - Independent Samples 
> 	- Known Variance
> 	- Shared Unknown Variance
> 	- Unknown Differing Variances

***Why?***
In the previous unit we covered testing whether some new mean is different than some preexisting one

In practice, we would usually want to find if two samples share means since we most likely don't know some true population mean, or we could have some intervention trying to find if the groups are different in some important outcome measure.

## Paired Samples
---
### Definition
---
*What is a paired sample?*
**Paired sample** occurs when there are two populations and the measurements of each population correspond to the same individual (1-1 match).
	e.g. if the same 50 people try two different cereals and rate which one they like more. Each measurement can be "*paired*" to the same person in other sample

### General Steps
---
In this scenario it is normal to simple **subtract the two means** and then ask "*is the difference between the means 0?*"

**Same steps as others with a few differences below:**
1. Must calculate the average difference $\bar{d}$ and the S.D. of differences $s_d$ 
2. Keep track of the initial subtraction to have a correct interpretation

*Paired T-test test statistic*

$$
\cfrac{\bar{d}\sqrt{n}}{s_d}
$$
*i.f.f.* n < 30

## Independent Samples
---
> Two mostly/completely different samples that we are testing against each other

### Same Known Variance
---
> Not realistic but a foundation

Confidence Interval:
$$
CI = (\bar{Y_1} - \bar{Y_2}) \ \pm \ z_{\alpha/2} \ \sqrt{\cfrac{\sigma_1}{n_1}+\cfrac{\sigma_2}{n_2}}
$$
Test Statistic:
$$
\frac{(\overline{Y}_1 - \overline{Y}_2) - \mu_0}
{\sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}}
$$

### Same Unknown Variance
---
> More realistic ig

Confidence Interval:

$$
\begin{aligned}
&\text{100}(1-\alpha)\%\ \text{confidence interval for } (\mu_1 - \mu_2): \\
&(\,\overline{Y}_1 - \overline{Y}_2\,)
\;\pm\;
t_{\,n_1+n_2-2,\;\alpha/2}\;
s_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}
\\
\end{aligned}
$$
Test Statistic:

$$
\begin{aligned}
&\text{Test statistic for } H_0:\ \mu_1 - \mu_2 = \mu_0: \\
&t
=
\frac{(\overline{Y}_1 - \overline{Y}_2) - \mu_0}
{s_p \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}}
\sim t(n_1 + n_2 - 2)
\end{aligned}
$$

- **Why pooled variance?**  
    Assumes both populations share the **same variance**, so combining sample variances gives a more stable estimate than using each alone.
    
- **Why weights (n₁−1, n₂−1)?**  
    Each variance estimate has **n−1 degrees of freedom**.  
    The pooled variance is a **weighted average**, giving more influence to the sample with more information.
    
- **Degrees of freedom:**  
    Total df is **n1+n2−2n_1 + n_2 - 2n1​+n2​−2**, the sum of both samples’ degrees of freedom.
    
- **When to use this method:**
    
    - Two **independent** samples
        
    - Variances **assumed equal**
        
    - Estimating or testing **mean differences**


### Differing Unknown Variances
---
$$
\begin{aligned}
&\textbf{Welch's Confidence Interval for } (\mu_1 - \mu_2): \\[0.6em]
&(\,\overline{Y}_1 - \overline{Y}_2\,)
\;\pm\;
t_{\upsilon,\;\alpha/2}
\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}
\\[1.4em]
&\textbf{Welch's Test Statistic for } H_0:\ \mu_1 - \mu_2 = \mu_0: \\[0.6em]
&t
=
\frac{(\overline{Y}_1 - \overline{Y}_2) - \mu_0}
{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}
\\[1.4em]
&\textbf{Welch--Satterthwaite Degrees of Freedom:} \\[0.6em]
&\upsilon
=
\frac{
\left( \frac{s_1^2}{n_1} + \frac{s_2^2}{n_2} \right)^2
}{
\frac{s_1^4}{\,n_1^2(n_1 - 1)\,}
+
\frac{s_2^4}{\,n_2^2(n_2 - 1)\,}
}
\end{aligned}
$$

**Explanation of $\upsilon$ (Welch–Satterthwaite Degrees of Freedom)**
The quantity $\upsilon$ is an **approximate degrees of freedom** value used in Welch’s $t$-test when the two population variances are **unknown and unequal**.  
Because each sample contributes its own estimated variance, the standard error has uncertainty coming from **two different sources**, making the true degrees of freedom non-integer.

Welch’s approximation adjusts for this by reducing the degrees of freedom based on how much variability comes from each sample.

$$
\upsilon
=
\frac{
\left( \frac{s_1^2}{n_1} + \frac{s_2^2}{n_2} \right)^2
}{
\frac{s_1^4}{\,n_1^2(n_1 - 1)\,}
+
\frac{s_2^4}{\,n_2^2(n_2 - 1)\,}
}
$$

### **Interpretation**
- $\upsilon$ determines **which $t$-distribution** to use for inference.  
- It is usually **non-integer** and often **smaller** than $n_1 + n_2 - 2$, reflecting greater uncertainty when variances differ.  
- When one sample is much more variable or much smaller, the degrees of freedom shrink substantially—making the test more conservative.  
- The formula weights each sample’s contribution by both:  
  - its **variance estimate** ($s_i^2$), and  
  - its **information amount** ($n_i - 1$).  
- As sample sizes grow large, $\upsilon$ approaches the ordinary large-sample degrees of freedom, and Welch’s test behaves like the standard $z$-test.



### **F-Test for Equality of Two Population Variances**
$$
\begin{aligned}
&\textbf{Test Statistic:} \\[0.4em]
&F \;=\; \frac{s_1^2}{s_2^2}
\\[1.2em]
&\textbf{Distribution Under } H_0:\ \sigma_1^2 = \sigma_2^2 \\[0.4em]
&F \sim F_{\,n_1-1,\; n_2-1}
\\[1.2em]
&\textbf{Hypotheses:} \\[0.4em]
&H_0: \sigma_1^2 = \sigma_2^2 \\[0.3em]
&H_A: \sigma_1^2 \neq \sigma_2^2 \quad (\text{two-sided}) \\[0.3em]
&H_A: \sigma_1^2 > \sigma_2^2 \quad (\text{right-sided}) \\[0.3em]
&H_A: \sigma_1^2 < \sigma_2^2 \quad (\text{left-sided})
\\[1.2em]
&\textbf{Decision Rule (two-sided):} \\[0.4em]
&\text{Reject } H_0 \text{ if }
F < F_{\alpha/2,\; n_1-1,\; n_2-1}
\quad \text{or} \quad
F > F_{1-\alpha/2,\; n_1-1,\; n_2-1}
\end{aligned}
$$

**Explanation (Concise + Useful)**

- **Purpose:**  
  The F-test checks whether two populations have **equal variances**, a key assumption for the pooled-variance t-test.

- **Test statistic:**  
  Uses the ratio of sample variances  
  $( s_1^2 / s_2^2 )$
  By convention, place the **larger variance in the numerator** to ensure ($F \ge 1$).

- **Distribution:**  
  Under equal variances, the ratio follows an **F distribution** with  
  ( $n_1 - 1$ ) and ( $n_2 - 1$) degrees of freedom.

- **Use cases:**  
  - Deciding whether to use the **pooled t-test** vs **Welch’s t-test**  
  - Testing variance equality in quality control or ANOVA preprocessing  
  - Checking homoscedasticity for two independent samples

- **Limitations:**  
  The F-test is **sensitive to non-normality**; large deviations from normality can distort results.

