# Biostats Exam 1 — One-Page (Front/Back) Cheat Sheet

> All math is shown as LaTeX inside this single code block. Inline math uses `$...$`; display math uses:
$$
... 
$$

---

## 1) Core Definitions

- **Mutually Exclusive (Disjoint)** — cannot occur simultaneously  
  $P(A \cap B) = 0$

- **Independent** — occurrence of one does not affect the other  
  $P(A \mid B) = P(A)$, and equivalently $P(A \cap B) = P(A)\,P(B)$

> **Note:** Nontrivial events cannot be both mutually exclusive **and** independent (unless a probability is $0$).

---

## 2) Set/Probability Identities

- Complement  
  $P(A^c) = 1 - P(A)$

- Partition of $B$ by $A$  
  $P(B) = P(A \cap B) + P(A^c \cap B)\ \Rightarrow\ P(A^c \cap B) = P(B) - P(A \cap B)$

- De Morgan  
  $(A \cup B)^c = A^c \cap B^c,\qquad (A \cap B)^c = A^c \cup B^c$

---

## 3) Union, Conditional, and Product Rules

- **Additive rule** (mutually exclusive)  
  $P(A \cup B) = P(A) + P(B)$

- **General union**  
  $P(A \cup B) = P(A) + P(B) - P(A \cap B)$

- **Multiplicative rule**  
  $P(A \cap B) = P(B)\,P(A \mid B) = P(A)\,P(B \mid A)$

- **Independence test**  
  $A \perp B \iff P(A \cap B) = P(A)P(B) \iff P(A \mid B) = P(A)$

---

## 4) Screening / Diagnostic Testing (2×2 Table)

Let $D$ = disease, $T^+$ = positive test.

- **Sensitivity** (true positive rate)  
  $P(T^+ \mid D)$

- **Specificity** (true negative rate)  
  $P(T^- \mid D^c)$

- **False rates**  
  $\text{FPR} = P(T^+ \mid D^c) = 1 - \text{specificity}$,  
  $\text{FNR} = P(T^- \mid D) = 1 - \text{sensitivity}$

- **Bayes (representative samples)**  
  $PPV = P(D \mid T^+),\qquad NPV = P(D^c \mid T^-)$

- **Bayes (expressed via sens/spec/prevalence)**  
$$
PPV = \frac{\text{sens}\cdot \text{prev}}{\text{sens}\cdot \text{prev} + (1-\text{spec})\cdot (1-\text{prev})}
$$
$$
NPV = \frac{\text{spec}\cdot (1-\text{prev})}{\text{spec}\cdot (1-\text{prev}) + (1-\text{sens})\cdot \text{prev}}
$$

- **Law of total probability (useful for case-mix)**  
  $P(T^+) = \text{sens}\cdot P(D) + (1-\text{spec})\cdot P(D^c)$

- **Likelihood Ratios (quick Bayes updates)**  
  $LR^+ = \dfrac{\text{sens}}{1-\text{spec}},\quad LR^- = \dfrac{1-\text{sens}}{\text{spec}}$

- **2×2 counts notation** (rows = $D$/$D^c$, cols = $T^+$/ $T^-$)
  - $a$ = TP, $b$ = FP, $c$ = FN, $d$ = TN  
  $\text{sens} = \dfrac{a}{a+c},\ \text{spec} = \dfrac{d}{b+d},\ PPV = \dfrac{a}{a+b},\ NPV=\dfrac{d}{c+d}$

---

## 5) Case-Partitioning / Stratification

- **Overall prevalence from strata $S_i$**  
$$
P(D) = \sum_i P(D \mid S_i)\,P(S_i)
$$

- **Overall positivity and PPV**  
$$
P(T^+) = \sum_i \big[\text{sens}\cdot P(D \mid S_i) + (1-\text{spec})\cdot (1 - P(D \mid S_i))\big]\,P(S_i)
$$
$$
PPV = \frac{\sum_i \text{sens}\cdot P(D \mid S_i)\,P(S_i)}{P(T^+)}
$$

> **Interpretation:** Higher-risk strata (higher $P(D\mid S_i)$) raise PPV.

---

## 6) Risk, Odds, RR, and OR

- **Risk (incidence proportion)**  
  $P(D \mid E)$ and $P(D \mid E^c)$

- **Relative Risk**  
  $RR = \dfrac{P(D \mid E)}{P(D \mid E^c)}$

- **Odds** (in group $G$)  
  $\text{odds}_G = \dfrac{P(D \mid G)}{1 - P(D \mid G)}$

- **Odds Ratio** (probability form)  
  $OR = \dfrac{P(D \mid E)/P(D^c \mid E)}{P(D \mid E^c)/P(D^c \mid E^c)}$

- **Odds Ratio (2×2 counts)**  
  $OR = \dfrac{a/c}{b/d} = \dfrac{ad}{bc}$

- **Rare disease link**  
  $OR \approx RR$ when $P(D)$ is small in both groups

---

## 7) Descriptives: Quartiles, IQR, Variance, SD, CV

- **Quartile position** (for ordered data, sample size $n$)  
  $Q_p$ at position $n\cdot p/100$ (apply your course’s rounding/interpolation rule)

- **Interquartile Range**  
  $IQR = Q_3 - Q_1$

- **Population variance / SD**  
$$
\sigma^2 = \frac{1}{N}\sum_{i=1}^{N}(x_i - \mu)^2,\qquad \sigma = \sqrt{\sigma^2}
$$

- **Sample variance / SD**  
$$
s^2 = \frac{1}{n-1}\sum_{i=1}^{n}(x_i - \bar x)^2,\qquad s = \sqrt{s^2}
$$

- **Coefficient of Variation**  
  $CV_{\text{pop}} = \dfrac{\sigma}{\mu}\times 100\%,\qquad CV_{\text{samp}} = \dfrac{s}{\bar x}\times 100\%$

---

## 8) Quick Pitfalls & Checks

- If $A$ and $B$ are **mutually exclusive**, then $P(A \cap B)=0$ (they are **not** independent unless a probability is $0$).  
- Always check **independence** via $P(A \cap B)\stackrel{?}{=}P(A)P(B)$.  
- **PPV/NPV depend on prevalence**—enriched case samples inflate PPV and deflate NPV.  
- Use **case-partitioning** when risk differs across strata (age, sex, site, etc.).  
- Keep track of complements:  
  $P(A^c \cap B) = P(B) - P(A \cap B)$,  
  $P(T^+ \mid D^c) = 1 - \text{spec}$,  
  $P(T^- \mid D) = 1 - \text{sens}$.
