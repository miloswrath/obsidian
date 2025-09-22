### Cheat sheet for Exam 1
*Definitions*
- *Mutually Exclusive* - cannot occur simultaneously
- *Independent* - Existence of one cannot affect the other

### Formulas
*Quartiles* - $Q_p = np/100$ // *IQR* = $Q_3 - Q_1$ 
*population variance* - $\sigma^2 = \textstyle\sum_{i = 1} ^ N(x_i - \mu)^2$ where $N$ is the total observations $std = \sqrt{\sigma^2}$
*sample variance* - $s^2=\cfrac{1}{n-1}\textstyle\sum{i=1}^N(x_i - \bar{x})^2$
*coefficient of variation (ratio of deviation to mean)* - $CV = \cfrac{\sigma}{\mu}*100$
*additive rule* - $P(A\cup B) = P(A) + P(B)$ - if mutually exclusive
*general union* - $P(A\cup B) = P(A) + P(B) - P(A\cap B)$ 
*conditional if independent* - $P(A|B) = P(A)$
*multiplicative rule* - $P(A|B) = \cfrac{P(A\cap B)}{P(B)}$ 
*sensitivity (probability obtaining positive result given disease)* - $P(T^+ | D)$
*specificity (probability negative given not disease* - $P(T^- | D)$
> ^^ complements are false positive/false negative rates

PPV/NPV - $P(D|T^+) \quad P(D|T^-)$ in representative samples
in non-representative samples:
$PPV = \cfrac{\text{sens}* \text{prev}}{\text{sens} * \text{prev} + (1-\text{spec})*(1-\text{prev})}$  $NPV = \cfrac{\text{spec}* (1 - \text{prev})}{\text{spec} * (1 - \text{prev}) + (1-\text{sens})*\text{prev}}$

*Relative Risk* - $RR = \cfrac{P(D|E)}{P(D|E^C)}$ - where E is the event an individual is exposed
*Odds* - For exposed individual, odds are:
$\cfrac{P(D|E)}{1-P(D|E)} \quad \text{or} \quad \cfrac{P(D|E)}{P(D^C|E)}$
*Odds Ratio (ratio of risk for exposed vs. not exposed)* - $OR = \cfrac{P(D|E)/P(D^C|E)}{P(D|E^C)/P(D^C|E^)}$
> OR = 1 if independent

