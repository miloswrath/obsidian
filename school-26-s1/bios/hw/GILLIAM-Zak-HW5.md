## Question 1
---
- **Type I error** → _false rejection_ (you reject a true null hypothesis).  
    → “You said there was an effect when there wasn’t.”  
    → Also called a **false positive**.
    
- **Type II error** → _false retainment_ (you fail to reject a false null hypothesis).  
    → “You missed a real effect.”  
    → Also called a **false negative**.

## Question 2
---
$$
\begin{array}{l}
\textbf{(a) Hypotheses (one-sided, lower-tail)}\\[4pt]
H_0:\ \mu=7250 \quad \text{(mean WBC equals general population)}\\[4pt]
H_1:\ \mu<7250 \quad \text{(infected persons have a lower mean WBC)}
\end{array}
$$

$$
\begin{array}{l}
\textbf{(b) Test statistic and decision at }\alpha=0.05\\[4pt]
\text{Given } n=16,\ \bar{x}=4742,\ s=3218 \Rightarrow \text{ one-sample } t\text{-test (unknown }\sigma).\\[6pt]
t=\dfrac{\bar{x}-\mu_0}{s/\sqrt{n}}=\dfrac{4742-7250}{3218/\sqrt{16}}=-3.117\\[4pt]
\text{df}=15,\quad p\text{-value}=P(T_{15}\le -3.117)=0.00353\\[4pt]
t_{\mathrm{crit},\,0.05}=-1.753\ \text{(lower tail)}\\[4pt]
\text{Decision: } t=-3.117<-1.753\ \text{ and }\ p=0.00353<0.05\ \Rightarrow\ \text{Reject }H_0.
\end{array}
$$
$$
{\begin{aligned}
&\textbf{(c) Conclusion} \\[6pt]
&\text{At the } \alpha=0.05 \text{ level, there is statistically significant evidence that the mean WBC count} \\[4pt]
&\text{among persons infected with \emph{E.\ canis} is lower than } 7250/\text{mm}^3. 
\end{aligned}}
$$

## Question 3
---
$$
\begin{array}{l}
\textbf{(a) Systolic blood pressure test (two-sided, } \alpha = 0.10\text{)}\\[4pt]
H_0:\ \mu_s = 136 \quad\text{vs.}\quad H_1:\ \mu_s \ne 136\\[4pt]
\text{Given } n=81,\ \bar{x}_s=145,\ s_s=23.1.\\[4pt]
z = \dfrac{\bar{x}_s - \mu_0}{s_s/\sqrt{n}} = \dfrac{145-136}{23.1/\sqrt{81}} = 3.506.\\[4pt]
p = 2(1-\Phi(|3.506|)) = 0.00045.\\[4pt]
\text{Decision: } p=0.00045 < 0.10 \Rightarrow \text{Reject } H_0.\\[4pt]
\text{Conclusion: Mean systolic pressure is significantly different (higher) for affected workers.}
\end{array}
$$
$$
\begin{array}{l}
\textbf{(b) Diastolic blood pressure test (two-sided, } \alpha = 0.10\text{)}\\[4pt]
H_0:\ \mu_d = 84 \quad\text{vs.}\quad H_1:\ \mu_d \ne 84\\[4pt]
\text{Given } n=81,\ \bar{x}_d=87,\ s_d=14.5.\\[4pt]
z = \dfrac{\bar{x}_d - \mu_0}{s_d/\sqrt{n}} = \dfrac{87-84}{14.5/\sqrt{81}} = 1.862.\\[4pt]
p = 2(1-\Phi(|1.862|)) = 0.0626.\\[4pt]
\text{Decision: } p=0.0626 < 0.10 \Rightarrow \text{Reject } H_0.\\[4pt]
\text{Conclusion: There is weak evidence that diastolic pressure is higher in the coronary group.}
\end{array}
$$
$$
\begin{array}{l}
\textbf{(c) Comparison of groups}\\[4pt]
\text{Both systolic and diastolic blood pressures are elevated among workers who have experienced}\\[4pt]
\text{a major coronary event. The systolic difference is highly significant (}p<0.001\text{), while the}\\[4pt]
\text{diastolic difference is marginally significant (}p\approx0.06\text{). This suggests higher overall}\\[4pt]
\text{blood pressure levels are associated with the coronary event group.}
\end{array}
$$

## Question 4
---
No, it is not possible for the FDA to completely eliminate Type II errors. To guarantee that no unsafe or ineffective drug is ever approved, the agency would have to test the drug on every individual in the population under every possible condition — an impossible task both ethically and practically. Even with extensive trials and rigorous review, there will always be variability in human responses and limitations in sample size and study design. Therefore, while the FDA can minimize the risk of Type II errors through careful testing and regulation, it can never reduce that risk to zero.


## Question 5
---
$$
\begin{array}{l}
\textbf{Setup (known }\sigma=43\text{, one-sided lower-tail test)}\\[4pt]
H_0:\ \mu=244\quad;\quad H_1:\ \mu<244\quad(\alpha=0.05),\ \ X\sim N(\mu, \sigma^2),\ \bar{X}\sim N\!\left(\mu,\frac{\sigma^2}{n}\right).\\[8pt]
\textbf{(a) Type I error}\\[2pt]
P(\text{Type I error})=\alpha=\boxed{0.05}.\\[8pt]
\textbf{(b) Type II error for }n=29\text{ when true }\mu=219\\[2pt]
\text{Critical value }c=\mu_0+z_\alpha\frac{\sigma}{\sqrt{n}}
=244+(-1.6449)\cdot\frac{43}{\sqrt{29}}= \boxed{230.8660}.\\[4pt]
\beta=P(\bar{X}>c\mid \mu=219)=1-\Phi\!\left(\frac{c-219}{43/\sqrt{29}}\right)=\boxed{0.06863}.\\[8pt]
\textbf{(c) Power}\\[2pt]
\text{Power}=1-\beta=\boxed{0.93137}.\\[8pt]
\textbf{(d) How to increase power}\\[2pt]
\text{Increase }n;\ \text{increase }\alpha;\ \text{reduce }\sigma\ \text{(better measurement/control)};\ \text{test for larger effect sizes}.\\[8pt]
\textbf{(e) Required }n\text{ so that }\beta=0.05\text{ at }\mu=219\ (\alpha=0.05)\\[2pt]
n=\left[\frac{\sigma\,(z_{1-\beta}-z_\alpha)}{\mu_0-\mu_{\text{true}}}\right]^2
=\left[\frac{43\,(1.6449-(-1.6449))}{25}\right]^2=\boxed{33}\ (\text{exact }n=32.016\ldots).\\[8pt]
\textbf{(f) Required }n\text{ so that }\beta=0.10\text{ at }\mu=219\ (\alpha=0.05)\\[2pt]
n=\left[\frac{43\,(1.2816-(-1.6449))}{25}\right]^2=\boxed{26}\ (\text{exact }n=25.335\ldots).
\end{array}
$$

## Question 6
---
$$
\begin{array}{l}
\textbf{Two-sided }z\text{-test (known }\sigma=462\text{), } \alpha=0.05,\ \beta=0.10,\ \Delta=|3200-3500|=300.\\[4pt]
n=\left(\frac{z_{1-\alpha/2}+z_{1-\beta}}{\Delta/\sigma}\right)^2
=\left(\frac{1.96+1.2816}{300/462}\right)^2
=\boxed{25}\ (\text{exact }24.919\ldots).\\[6pt]
\text{Answer: } \boxed{n=25}.
\end{array}
$$

## Question 7
---
$$
\begin{array}{l}
\textbf{Known }\sigma_d=8.9,\ \text{two-sided test vs } \mu_0=74.1,\ n=9,\ \bar{x}_d=81.0.\\[6pt]
\textbf{(a) }H_0:\ \mu_d=74.1 \qquad \textbf{(b) }H_A:\ \mu_d\neq 74.1\\[8pt]
\textbf{(c) Test at }\alpha=0.05\ (\text{normal }X\Rightarrow \text{use }z\text{-test with known }\sigma)\\[2pt]
z=\dfrac{\bar{x}-\mu_0}{\sigma/\sqrt{n}}
=\dfrac{81.0-74.1}{8.9/\sqrt{9}}=\boxed{2.3258}.\\[4pt]
p\text{-value}=2\{1-\Phi(|z|)\}=\boxed{0.02003}.\\[4pt]
\text{Decision at } \alpha=0.05:\ p=0.02003<0.05 \Rightarrow \text{Reject }H_0.\\[6pt]
\textbf{(d) Conclusion: } \text{There is significant evidence that } \mu_d\neq 74.1\ \text{mm Hg}.\\[6pt]
\textbf{(e) At } \alpha=0.01:\ p=0.02003>0.01 \Rightarrow \text{Do not reject }H_0\ \text{(conclusion would differ).}
\end{array}
$$

## Question 8
---
$$
\begin{array}{l}
\textbf{Unknown }\sigma,\ n=51,\ \bar{x}=24.73,\ s=3.2,\ \text{use }t\text{ with }df=50.\\[6pt]
\textbf{(a) 95\% CI for }\mu:\\[2pt]
\bar{x}\ \pm\ t_{0.975,50}\cdot \dfrac{s}{\sqrt{n}}
=24.73\ \pm\ 2.0086\cdot \dfrac{3.2}{\sqrt{51}}
=\boxed{(23.830,\ 25.630)}.\\[8pt]
\textbf{(b) Test }H_0:\mu=24.0\ \text{ vs }\ H_A:\mu\neq 24.0\ \text{ at } \alpha=0.05\\[2pt]
t=\dfrac{24.73-24.0}{3.2/\sqrt{51}}=\boxed{1.6291},\quad
p\text{-value}=2\{1-F_{t,50}(|t|)\}=\boxed{0.1096}.\\[6pt]
\textbf{(c) Conclusion: } p=0.1096>0.05\Rightarrow \text{Do not reject }H_0.\\[8pt]
\textbf{(d) CI consistency: }24.0\ \text{lies within }(23.830,25.630),\ \text{so not rejecting }H_0\ \text{is expected.}
\end{array}
$$
