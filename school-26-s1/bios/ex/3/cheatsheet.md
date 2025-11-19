
---

### Errors & Power

- **Type I Error ($\alpha$)**  
  Reject $H_0$ when $H_0$ is actually true.

- **Type II Error ($\beta$)**  
  Retain $H_0$ when $H_A$ is actually true.

- **Power**  
  $$
  1 - \beta = P(\text{Reject } H_0 \mid H_0 \text{ false})
  $$

- **Increase power (decrease $\beta$)** by:
  - Increasing $n$
  - Increasing $\alpha$
  - Increasing effect size
  - Reducing variability ($\sigma$)

---

### One-Sample Inference for a Mean

### Z-Test (known $\sigma$)

Test statistic:
$$
Z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}}
$$

- Use standard normal critical values $z_\alpha$ or $z_{\alpha/2}$.  
- Two-sided: reject $H_0$ if $|Z| > z_{\alpha/2}$.

### t-Test (unknown $\sigma$)

Test statistic:
$$
t = \frac{\bar{x} - \mu_0}{s/\sqrt{n}}, \quad t \sim t_{n-1} \text{ under } H_0
$$

---

### Power & Sample Size for a Mean (Z-Approximation)

Let effect size be $|\mu_A - \mu_0|$ and known $\sigma$.

- **Required ingredients**:
  - $\alpha, \beta$
  - Critical values $z_{\alpha}$ or $z_{\alpha/2}$ (one- vs two-sided)
  - $z_\beta$
  - Effect size $|\mu_A - \mu_0|$
  - Standard deviation $\sigma$

- **Sample size (two-sided Z-test)**:
  $$
  n \ge 
  \left[
    \frac{
      \left(z_{\alpha/2} + z_{\beta}\right)\sigma
    }{
      |\mu_A - \mu_0|
    }
  \right]^2
  $$
---
### One-Sample Inference for a Proportion

Let $\hat{p} = x/n$ be the sample proportion.

### Sampling Distribution of $\hat{p}$

- Standard error:
  $$
  \text{SE}(\hat{p}) = \sqrt{\frac{p(1-p)}{n}}
  $$
### Confidence Interval for $p$

$$
\hat{p} \pm z_{\alpha/2}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}}
$$

### Hypothesis Test for $p$ (Z-Test)

Test statistic (use $p_0$ in SE):
$$
z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}
$$


### Sample Size for Margin of Error $m$

Want:
$$
z_{\alpha/2}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}} \le m
$$

Solution:
$$
n \ge \left(
  \frac{
    z_{\alpha/2}\sqrt{\hat{p}(1-\hat{p})}
  }{
    m
  }
\right)^2
$$

If $\hat{p}$ unknown, use $\hat{p} = 0.5$ (maximizes $\hat{p}(1-\hat{p})$):

$$
n \ge \left(
  \frac{z_{\alpha/2}\cdot 0.5}{m}
\right)^2
$$

---
### Paired Samples (Dependent)

1. Compute differences for each pair: $d_i = Y_{1i} - Y_{2i}$.  
2. Compute $\bar{d}$ and $s_d$.  
3. Test if mean difference is $0$ (or some $\mu_{d0}$).

$$
t = \frac{\bar{d}\sqrt{n}}{s_d}, \quad t \sim t_{n-1} \text{ under } H_0
$$

---

### Two Independent Means

### Case 1: Known Variances $\sigma_1^2, \sigma_2^2$

**CI for $\mu_1 - \mu_2$**:
$$
(\bar{Y}_1 - \bar{Y}_2) 
\pm
z_{\alpha/2}
\sqrt{
  \frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}
}
$$

**Test statistic** ($H_0: \mu_1 - \mu_2 = \mu_0$):
$$
Z = 
\frac{
  (\bar{Y}_1 - \bar{Y}_2) - \mu_0
}{
  \sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}
}
$$

---

### Case 2: Equal Unknown Variances (Pooled t-Test)

**Assumptions**
- Two independent samples  
- $\sigma_1^2 = \sigma_2^2 = \sigma^2$ (equal variances)

**Pooled variance**:
$$
s_p
=
\sqrt
\frac{
  (n_1 - 1)s_1^2 + (n_2 - 1)s_2^2
}{
  n_1 + n_2 - 2
}
$$

- Weights $(n_i - 1)$ come from each sample’s degrees of freedom.  
- Total df: $n_1 + n_2 - 2$.

**CI for $\mu_1 - \mu_2$**:
$$
(\bar{Y}_1 - \bar{Y}_2)
\pm
t_{n_1 + n_2 - 2,\;\alpha/2}
\; s_p
\sqrt{
  \frac{1}{n_1} + \frac{1}{n_2}
}
$$

**Test statistic** ($H_0: \mu_1 - \mu_2 = \mu_0$):
$$
t =
\frac{
  (\bar{Y}_1 - \bar{Y}_2) - \mu_0
}{
  s_p
  \sqrt{
    \frac{1}{n_1} + \frac{1}{n_2}
  }
}
\sim t_{n_1 + n_2 - 2}
$$
---

### Case 3: Unequal Unknown Variances (Welch’s t-Test)

**CI for $\mu_1 - \mu_2$**:
$$
(\bar{Y}_1 - \bar{Y}_2)
\pm
t_{\nu,\;\alpha/2}
\sqrt{
  \frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}
}
$$

**Test statistic** ($H_0: \mu_1 - \mu_2 = \mu_0$):
$$
t =
\frac{
  (\bar{Y}_1 - \bar{Y}_2) - \mu_0
}{
  \sqrt{
    \frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}
  }
}
$$

**Welch–Satterthwaite df**:
$$
\nu
=
\frac{
\left( \frac{s_1^2}{n_1} + \frac{s_2^2}{n_2} \right)^2
}{
\frac{s_1^4}{n_1^2(n_1 - 1)}
+
\frac{s_2^4}{n_2^2(n_2 - 1)}
}
$$

- $\nu$ is typically **non-integer** and often **$< n_1+n_2-2$**.  
- Use when variances appear **unequal**.


---

### Two Proportions (Independent Samples)

Let
$$
\hat{p}_1 = \frac{x_1}{n_1}, \quad
\hat{p}_2 = \frac{x_2}{n_2}, \quad
\hat{p} = \frac{n_1\hat{p}_1 + n_2\hat{p}_2}{n_1 + n_2}
$$

### Large-Sample Conditions

$$
n_i\hat{p}_i \ge 5,\quad n_i(1-\hat{p}_i) \ge 5, \quad i=1,2
$$

### Two-Sided CI for $(p_1 - p_2)$

$$
(\hat{p}_1 - \hat{p}_2)
\pm
z_{\alpha/2}
\sqrt{
  \frac{\hat{p}_1(1-\hat{p}_1)}{n_1}
  +
  \frac{\hat{p}_2(1-\hat{p}_2)}{n_2}
}
$$

(One-sided CI: replace $z_{\alpha/2}$ with $z_{\alpha}$ and cap at $[-1,1]$.)

### Test of $H_0: p_1 = p_2$

**Test statistic** (pooled standard error):
$$
z =
\frac{
  \hat{p}_1 - \hat{p}_2
}{
  \sqrt{
    \hat{p}(1-\hat{p})
    \left(
      \frac{1}{n_1} + \frac{1}{n_2}
    \right)
  }
}
$$

**Rejection Regions**

| $H_A$         | Rejection Region                          |
| ------------- | ----------------------------------------- |
| $p_1 \ne p_2$ | $z < -z_{\alpha/2}$ or $z > z_{\alpha/2}$ |
| $p_1 > p_2$   | $z > z_{\alpha}$                          |
| $p_1 < p_2$   | $z < -z_{\alpha}$                         |

**p-values**

| $H_A$         | p-value     |
| ------------- | ----------- |
| $p_1 \ne p_2$ | $2P(Z > z)$ |
| $p_1 > p_2$   | $P(Z > z)$  |
| $p_1 < p_2$   | $P(Z < z)$  |

---

### Sample Size for Two Proportions (Power-Based)

Target effect size $|p_A - p_0|$ and power $(1-\beta)$.

**Two-sided test**:
$$
n \ge 
\left(
\frac{
  z_{\alpha/2}\sqrt{p_0(1-p_0)} 
  +
  z_{\beta}\sqrt{p_A(1-p_A)}
}{
  |p_A - p_0|
}
\right)^2
$$

**One-sided test**:
$$
n \ge 
\left(
\frac{
  z_{\alpha}\sqrt{p_0(1-p_0)} 
  +
  z_{\beta}\sqrt{p_A(1-p_A)}
}{
  |p_A - p_0|
}
\right)^2
$$
