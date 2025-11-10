
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
