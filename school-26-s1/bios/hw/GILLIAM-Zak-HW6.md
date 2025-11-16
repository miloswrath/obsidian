
## Question 1
---
**a**
*II* would be the best. Since there are only 14 individuals, having gold-standard laboratory test to confirm objective specificity is both plausible and preferred.

**b***
These two samples are dependent because they are repeated measurements on the same individuals under two conditions. 

**c**
Paired t-test

**d**
$\mu_{\text{corn}} = 4.3621$,  
$\mu_{\text{oat}} = 4.0986$,  
$\mu_{\text{diff}} = 0.2636$.
The sample standard deviation of the paired differences is $s_{diff}=0.4758$.

**e**
$H_0 = \mu_\text{diff} = 0$
$H_A = \mu_\text{diff} \ne 0$

**f**
```python
from scipy.stats import ttest_rel
   ...:
   ...: corn = [4.56, 6.36, 5.26, 4.37, 3.90, 3.77, 5.00, 4.28, 3.
      ⋮ 66, 4.59, 5.28, 3.85, 2.12, 4.07]
   ...: oat =  [3.76, 5.60, 5.86, 4.88, 3.75, 3.01, 4.33, 3.66, 3.
      ⋮ 58, 3.89, 5.33, 3.79, 1.76, 4.18]
   ...:
   ...: t_stat, p_value = ttest_rel(corn, oat)
   ...:
   ...: alpha = 0.05
   ...: print("t-statistic:", t_stat)
   ...: print("p-value:", p_value)
   ...:
   ...: if p_value < alpha:
   ...:     print("Reject H0: There is a significant difference.")
      ⋮
   ...: else:
   ...:     print("Fail to reject H0: No significant difference at
      ⋮  α = 0.05.")
   ...:
t-statistic: 2.072809777677331
p-value: 0.0586310407573271
Fail to reject H0: No significant difference at α = 0.05.
```


**g**
There is no evidence that oat lowers cholesterol. There is no evidence that there is even a difference between the two. The p-value for a difference between the two is $\approx 0.8$ greater than 0.05 thus there is no difference. Given the test stat is $\text{Corn} - \text{Oat}$ and it is positive, there is a slight reduction in LDL but not a statistically significant reduction a $\alpha = 0.05$

**h**
```python
   # Using the same corn/oat from above
   ...: 
   ...: diff = corn - oat
   ...: n = len(diff)
   ...: mean_diff = np.mean(diff)
   ...: sd_diff = np.std(diff, ddof=1)
   ...:
   ...: alpha = 0.05
   ...: df = n - 1
   ...: t_crit = t.ppf(1 - alpha/2, df)
   ...:
   ...: lower = mean_diff - t_crit * (sd_diff / np.sqrt(n))
   ...: upper = mean_diff + t_crit * (sd_diff / np.sqrt(n))
   ...:
   ...: print("95% CI: [", lower, ",", upper, "]")
   ...:
   ...:
   ...: corn = np.array([4.56, 6.36, 5.26, 4.37, 3.90, 3.77, 5.00,
      ⋮  4.28, 3.66, 4.59, 5.28, 3.85, 2.12, 4.07])
   ...: oat =  np.array([3.76, 5.60, 5.86, 4.88, 3.75, 3.01, 4.33,
      ⋮  3.66, 3.58, 3.89, 5.33, 3.79, 1.76, 4.18])
   ...:
   ...: diff = corn - oat
   ...: n = len(diff)
   ...: mean_diff = np.mean(diff)
   ...: sd_diff = np.std(diff, ddof=1)
   ...:
   ...: alpha = 0.05
   ...: df = n - 1
   ...: t_crit = t.ppf(1 - alpha/2, df)
   ...:
   ...: lower = mean_diff - t_crit * (sd_diff / np.sqrt(n))
   ...: upper = mean_diff + t_crit * (sd_diff / np.sqrt(n))
   ...:
   ...: print("95% CI: [", lower, ",", upper, "]")
   
95% CI: [ -0.011133688683670429 , 0.5382765458265277 ]
```

**(i)**
In a small crossover study (n=14) of men with high LDL cholesterol, average LDL was slightly lower after two weeks on an oat bran cereal compared with corn flakes (mean paired difference Corn − Oat = 0.26 mmol/L; 95% CI: −0.01 to 0.54; p=0.059). This suggests a possible LDL benefit of oat bran, but results were not statistically conclusive in this sample. People considering dietary changes should consult healthcare professionals; larger, longer studies are needed to confirm the effect.

**(j)**
- Consider nutrition education materials that highlight whole-grain/oat options as a promising LDL-lowering strategy, while noting current evidence here is suggestive not definitive.  
- Support funding for larger, longer randomized trials of oat products on cholesterol and cardiovascular outcomes.  
- Encourage food labeling and cafeteria/menu nudges that increase access to high-fiber cereals, especially in community and school settings, paired with monitoring programs to evaluate impact.


## Question 2
---
**a**
$H_0 = \mu_\text{corn} = \mu_\text{oat}$
$H_A = \mu_\text{corn} \ne \mu_\text{oat}$ 

**b**
```python
   ...: from scipy.stats import ttest_ind
   ...:
   ...: corn = np.array([4.56, 6.36, 5.26, 4.37, 3.90, 3.77, 5.00,
      ⋮  4.28, 3.66, 4.59, 5.28, 3.85, 2.12, 4.07])
   ...: oat  = np.array([3.76, 5.60, 5.86, 4.88, 3.75, 3.01, 4.33,
      ⋮  3.66, 3.58, 3.89, 5.33, 3.79, 1.76, 4.18])
   ...:
   ...: # two-sample t-test assuming equal (pooled) variance
   ...: t_stat, p_value = ttest_ind(corn, oat, equal_var=True)
   ...:
   ...: t_stat, p_value
(np.float64(0.6766948952297902), np.float64(0.5045758608921785))

```
using independent samples with shared unkown variances, the p-value is $\approx 0.505$

**c**
There is no significant difference in mean LDL cholesterol between the corn and oat groups when treated as independent samples with a shared but unknown variance.

**d**
Compared to Problem 1 (where the data were paired), this result is even less statistically convincing. Treating the samples as independent removes the within-subject matching that controlled for individual variability. Without pairing, each observation carries more unexplained variation, which increases the standard error and weakens the test statistic.

As a result, the independent-sample test shows no evidence of a difference, and detecting any true effect under this design would likely require a much larger sample size.

## Question 3
---
**Paired samples** are two subsequent measurements under different conditions from the same sample of inidividuals. Each person in the sample experiences both conditions and thus the difference within individual must be modeled. In this scenario, the two measurements are dependent with shared variance.



## Question 4
---
The sample size $n$, alpha ($\alpha$), and the proportion itself all contribute to the length of the confidence interval
For example, an upper-bound for a proportion is modeled as:
$$
\Big(0, \ \hat{p} \  + z_\alpha\sqrt{\cfrac{p(1-p)}{n}} \ \Big)
$$
So the right side of the '$+$' is what we are focused on here. The crit value $\alpha$ obviously makes a difference. The rooted numerator '$p(1-p)$' means that the variability of the estimate depends on how close the true proportion is to 0.5. When ppp is near 0.5, the term $p(1−p)$ reaches its maximum, producing a wider confidence interval because uncertainty is highest when outcomes are most variable. As ppp approaches 0 or 1, $p(1-p)$ becomes smaller, and the confidence interval narrows, reflecting greater certainty in extreme proportions.

Additionally, since the whole expression is divided by $\sqrt{n}$ a larger sample size produces a tighter MoE and reduces CI size.

## Question 5
---
**a**  
$\hat{p} = \dfrac{464}{489} \approx 0.949$

**b**  
$95\% \ \text{CI} = \hat{p} \pm z_{\alpha} \sqrt{\dfrac{\hat{p}(1-\hat{p})}{n}} = 0.949 \pm 1.96 \sqrt{\dfrac{0.949(1-0.949)}{489}} \approx [0.929,\ 0.968]$

**c**  
We are $95\%$ confident that the true effectiveness of mifepristone lies between $92.9\%$ and $96.8\%$.  
This narrow interval suggests the treatment is highly effective, with relatively low sampling variability due to the large sample size.

**d**
$90\% \ \text{CI} = \hat{p} \pm z_{\alpha} \sqrt{\dfrac{\hat{p}(1-\hat{p})}{n}} = 0.949 \pm 1.645 \sqrt{\dfrac{0.949(1-0.949)}{489}} \approx [0.932,\ 0.965]$

We are $90\%$ confident that the true effectiveness of mifepristone lies between $93.2\%$ and $96.5\%$.  

**e**
As expected, this interval is slightly narrower than the $95\%$ confidence interval due to the lower confidence level. Though, not by much due to large sample size and high confidence in extreme proportions.

## Question 6
---
**a** 
90% CI:
$$
\begin{aligned}
n &= 60, \quad x = 6 \\
\hat{p} &= \frac{x}{n} = \frac{6}{60} = 0.10 \\[4pt]
z_{\alpha/2} &= z_{0.95} \approx 1.645 \quad (\text{for a 90\% CI}) \\[6pt]
\text{SE}(\hat{p}) 
  &= \sqrt{\frac{\hat{p}(1-\hat{p})}{n}}
   = \sqrt{\frac{0.10 \cdot 0.90}{60}}
   \approx 0.0387 \\[6pt]
\text{90\% CI for } p 
  &= \hat{p} \pm z_{\alpha/2} \cdot \text{SE}(\hat{p}) \\
  &= 0.10 \pm 1.645(0.0387) \\[4pt]
  &\approx 0.10 \pm 0.0637 \\[4pt]
  &\approx (0.036, \ 0.164)
\end{aligned}
$$
**b**
$$
\begin{aligned}
H_0 &: p = 0.22 \\
H_A &: p \ne 0.22
\end{aligned}
$$

**c & d** 
$$
\begin{aligned}
\text{Given:} \quad 
&\hat{p} = 0.10, \quad p_0 = 0.22, \quad n = 60, \quad \alpha = 0.05 \\[4pt]
\text{Test statistic:} \quad
z &= \frac{\hat{p} - p_0}{\sqrt{\dfrac{p_0(1 - p_0)}{n}}} \\[4pt]
  &= \frac{0.10 - 0.22}{\sqrt{\dfrac{0.22 \cdot 0.78}{60}}}
   \approx -2.24 \\[8pt]
\text{Two-sided p-value:} \quad
p &\approx 0.025 \\[8pt]
\text{Decision (}\alpha = 0.05\text{):} \quad
&p < 0.05 \;\Rightarrow\; \text{Reject } H_0. \\[4pt]
\text{Conclusion:} \quad
&\text{There is evidence that the proportion in the special education program} \\
&\text{is significantly different from } 0.22 \text{ (and is lower in this sample).}
\end{aligned}
$$

$$ 
\begin{aligned}
\hat{p} = 0.1 \\
p_0 = 0.22 \\
\alpha = 0.05 \\

z = \cfrac{\hat{p} - p_0}{\sqrt{\cfrac{p_0(1-p_0)}{n}}} \\
= -3.09 \\

\end{aligned}
$$

$$\begin{aligned}\boxed{\text{The two populations are significantly different with a p-value < 0.001}}\end{aligned}$$

**e**
$$
\begin{aligned}
\text{Given: } &p_0 = 0.22,\quad p_1 = 0.10,\quad 
\alpha = 0.05\ (\text{two-sided}), \quad \beta = 0.05 \\[6pt]

n &= 
\frac{\left[
z_{\alpha/2}\sqrt{p_0(1-p_0)} +
z_{\beta}\sqrt{p_1(1-p_1)}
\right]^2}
{(p_1 - p_0)^2} \\[10pt]

&=
\frac{\left[
1.96\sqrt{0.22(0.78)} +
1.645\sqrt{0.10(0.90)}
\right]^2}
{(0.10 - 0.22)^2} \\[10pt]

&\approx 
\frac{(1.307)^2}{0.0144}
\approx 118.7
\end{aligned}
$$

$$
\boxed{n \approx 119\ \text{participants required}}
$$

## Question 7
---
**a** (Point estimate)
$$
\begin{aligned}
n_1&=120,\ x_1=13 \ \Rightarrow\ \hat p_1=\frac{13}{120}=0.1083\\
n_2&=100,\ x_2=11 \ \Rightarrow\ \hat p_2=\frac{11}{100}=0.11\\[4pt]
\widehat{(p_1-p_2)}&=\hat p_1-\hat p_2 = -0.0017
\end{aligned}
$$

**b** 
$$
\begin{aligned}
\text{SE} &= \sqrt{\frac{\hat p_1(1-\hat p_1)}{n_1}+\frac{\hat p_2(1-\hat p_2)}{n_2}}
= 0.04224\\
\text{CI}_{95\%}&:\ (\hat p_1-\hat p_2)\ \pm\ z_{0.975}\cdot \text{SE}
= -0.0017 \pm 1.96(0.04224)\\
&\approx (-0.0845,\ 0.0811)
\end{aligned}
$$

**c** 
$$
\begin{aligned}
\hat p &= \frac{x_1+x_2}{n_1+n_2}=\frac{24}{220}=0.1091, \quad
\text{SE}_{\text{pooled}}=\sqrt{\hat p(1-\hat p)\!\left(\frac{1}{n_1}+\frac{1}{n_2}\right)}=0.0422\\
z &= \frac{\hat p_1-\hat p_2}{\text{SE}_{\text{pooled}}} = -0.0395, 
\quad p\text{-value}=0.969\\
\text{Decision:}&\ \ p>0.05\ \Rightarrow\ \text{Fail to reject }H_0.
\end{aligned}
$$

**d** (Conclusion)
$$
\text{No evidence that physician advice changes quit rates in this sample (difference }\approx -0.17\%\text{; 95\% CI spans 0; }p=0.969).
$$


## Question 8
---
**a** 
$$
\begin{aligned}
n_1&=318,\ x_1=14 \ \Rightarrow\ \hat p_{\text{prepaid}}=\frac{14}{318}=0.0440\\
n_2&=311,\ x_2=26 \ \Rightarrow\ \hat p_{\text{trad}}=\frac{26}{311}=0.0836
\end{aligned}
$$

**b** 
$$
\begin{aligned}
\hat p &= \frac{14+26}{318+311}=0.0636, \ 
\text{SE}_{\text{pooled}}=\sqrt{\hat p(1-\hat p)\!\left(\frac{1}{318}+\frac{1}{311}\right)}\\
z &= \frac{0.0440-0.0836}{\text{SE}_{\text{pooled}}} = -2.034,\quad
p=0.0420
\end{aligned}
$$

**c** (Conclusion)
$$
p=0.042<0.10 \Rightarrow \text{Reject }H_0.\ \ \text{The prepaid plan shows a lower crisis-center visit rate than traditional Medicaid in this sample.}
$$


## Question 9
---
Let Rhine = group 1 $(n_1=9,\ \bar x_1=5.36,\ s_1=2.26)$ and Moselle = group 2 $(n_2=14,\ \bar x_2=3.57,\ s_2=1.02)$; test $\mu_1-\mu_2$ (Rhine $-$ Moselle).

**a** 
$$
\begin{aligned}
s_p^2 &= \frac{(n_1-1)s_1^2+(n_2-1)s_2^2}{n_1+n_2-2}=2.45,\quad
s_p=1.567\\
\text{SE} &= s_p\sqrt{\frac{1}{n_1}+\frac{1}{n_2}}=0.686\\
t &= \frac{\bar x_1-\bar x_2}{\text{SE}}=\frac{1.79}{0.686}=2.603,\quad
df=21,\quad p=0.0166
\end{aligned}
$$

**b** 
$$
(\bar x_1-\bar x_2)\ \pm\ t_{0.975,21}\cdot \text{SE}
= 1.79 \pm 2.080(0.686)
\approx (0.360,\ 3.220)
$$

**c** (Unequal variances; Welch $t$ at $\alpha=0.05$)
$$
\begin{aligned}
\text{SE}_W&=\sqrt{\frac{s_1^2}{n_1}+\frac{s_2^2}{n_2}}=0.801, \quad
t=\frac{1.79}{0.801}=2.234\\
df&\approx 10.13,\quad p=0.0492
\end{aligned}
$$

**d**
$$
(\bar x_1-\bar x_2)\ \pm\ t_{0.975,\,10.13}\cdot \text{SE}_W
= 1.79 \pm 2.228(0.801)
\approx (0.008,\ 3.572)
$$

**e** (Which to report?)
$$
\text{Report Welch (unequal-variance) results for robustness; conclusions align (significant) and Welch does not assume equal variances.}
$$
