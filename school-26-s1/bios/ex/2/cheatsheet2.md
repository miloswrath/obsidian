# 🧠 Probability & Inference — Exam Cheat Sheet

> **Core Symbols**
> - $X$ = random variable $x$ = value $\bar X$ = sample mean  
> - $\mu$ = population mean $\sigma$ = pop. SD $s$ = sample SD  
> - $E[X]$ = expectation $\mathrm{Var}(X)$ = variance  
> - $z_\alpha$: $P(Z>z_\alpha)=\alpha$ $t_{\nu,\alpha}$: $P(T>t_{\nu,\alpha})=\alpha$

---

## ⚙️ THEORY — Key Ideas

### 🎲 Random Variables
- **Discrete (PMF):** $p(x)=P(X=x)$ $\sum p(x)=1$
- **Continuous (PDF):** $f(x)\ge0$ $\int f(x)\,dx=1$
- **CDF:** $F(x)=P(X\le x)$ → $P(a<X\le b)=F(b)-F(a)$

---

### 📊 Expectation & Variance
- $E[X]=\sum x\,p(x)$ or $\int x f(x)\,dx$
- $\mathrm{Var}(X)=E[(X-\mu)^2]$
- Linearity: $E[aX+bY]=aE[X]+bE[Y]$

---

### 🧩 Named Distributions
| Distribution | Use Case | Parameters | $E[X]$ | $\mathrm{Var}(X)$ |
|---------------|-----------|-------------|-----------|----------------|
| **Bernoulli($p$)** | 1 trial, success/failure | $p$ | $p$ | $p(1-p)$ |
| **Binomial($n,p$)** | $n$ independent Bernoulli | $n,p$ | $np$ | $np(1-p)$ |
| **Poisson($\lambda$)** | Count in time/space | $\lambda$ | $\lambda$ | $\lambda$ |
| **Normal($\mu,\sigma^2$)** | Continuous avg/sum | $\mu,\sigma^2$ | $\mu$ | $\sigma^2$ |

---

### 🔄 Approximations
- Binomial → Poisson if $n$ large, $p$ small ($\lambda=np$)  
- Binomial → Normal if $np, n(1-p) \ge 10$  
- Poisson → Normal if $\lambda$ large  
- CLT: $\bar X \approx N(\mu, \sigma^2/n)$ (for $n\ge30$)

---

### 🧮 Standardization
- **Z-score:** $Z=\dfrac{X-\mu}{\sigma}$  
- **Empirical rule:** $68\%-95\%-99.7\%$ for $\mu\pm1,2,3\sigma$

---

### 🧷 Confidence Intervals (CI)
- CI gives range likely to contain true parameter.
- $100(1-\alpha)\%$ confidence → long-run coverage probability.
- Use:
  - $z$ if $\sigma$ known or $n$ large
  - $t$ if $\sigma$ unknown, $n<30$ (parent ≈ normal)

---

## 🧾 FORMULAE — Compact Reference

### 🧱 Binomial
- **PMF:**  
  $$P(X=x)=\binom{n}{x}p^x(1-p)^{n-x}$$  
- $\mathrm{SD}=\sqrt{np(1-p)}$
- **Combinations:** $\binom{n}{k}=\frac{n!}{k!(n-k)!}$

---

### 🕒 Poisson
- **PMF:**  
  $$P(X=x)=e^{-\lambda}\frac{\lambda^x}{x!}$$  
- **Additivity:** Sum of independent Poissons → Poisson($\sum\lambda_i$)

---

### 📈 Normal
- **Standardize:** $Z=\dfrac{X-\mu}{\sigma}$  
- If $X\sim N(\mu,\sigma^2)$ → $Z\sim N(0,1)$  

---

### 🧮 Sampling & SE
- $\mathrm{SE}(\bar X)=\dfrac{\sigma}{\sqrt n}$ or $s/\sqrt n$
- $\mathrm{SE}(\hat p)=\sqrt{\dfrac{p(1-p)}{n}}$

---

### 📐 Confidence Intervals

**1. Mean ($\sigma$ known):**
$$\bar x \pm z_{\alpha/2}\frac{\sigma}{\sqrt n}$$

**2. Mean ($\sigma$ unknown):**
$$\bar x \pm t_{n-1,\alpha/2}\frac{s}{\sqrt n}$$

**3. Proportion (large $n$):**
$$\hat p \pm z_{\alpha/2}\sqrt{\frac{\hat p(1-\hat p)}{n}}$$

**4. One-Sided CI (upper/lower):**
$$\bar x \pm z_\alpha\frac{\sigma}{\sqrt n}$$ or use $t_{n-1,\alpha}$

---

### 📏 Sample Size
- For margin of error $k$:
  $$n\ge\left(\frac{z_{\alpha/2}\sigma}{k}\right)^2$$
- For proportions:
  $$n\ge\frac{z_{\alpha/2}^2 p_0(1-p_0)}{k^2}$$

---

### 🧮 Normal Approximation (continuity correction)
- $X\sim \mathrm{Bin}(n,p)\approx N(np,\ np(1-p))$  
  $$P(X\le x)\approx P\!\left(Z\le\frac{(x+0.5)-np}{\sqrt{np(1-p)}}\right)$$

---

### 🧾 Quick Reference

| Confidence Level | $z_{\alpha/2}$ |
|:----------------:|:--------------:|
| 90% | 1.645 |
| 95% | 1.96 |
| 99% | 2.576 |

---

### ⚡ Quick Procedures
- **Find $Z$:** $(x-\mu)/\sigma$ → use table for area/tail.  
- **CI:** compute SE, choose $z$ or $t$, apply $\bar x \pm$ critical × SE.  
- **Poisson:** $P(X=x)=e^{-\lambda}\lambda^x/x!$.  
- **Binomial Tail (Normal approx):** continuity correction ±0.5.

---

> ✅ **Exam Tip:** Identify variable type → match to distribution → pick formula (Binomial/Poisson/Normal) → standardize → CI/test.
