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
