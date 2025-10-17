## What was covered?
---
- Random Variables
- Probability mass and density functions
- Poisson, binomial, and normal distributions
## Terminology Review
---
- $\mu$ = population mean
- $\sigma^2$ = population variance
- $\sigma$ = the standard deviation
- $E(X)$ is the expected value of X
	- Or the probability of X in its pmf

## Random Variables
---
#### Definitions
- **Random Variable** - Some variable that is the outcome of a random experiment
	- Discrete values only assume specific values
	- Continuous can have any
- **Probability Distribution** - A function that assigns every possible value a probability 
- **Probability Mass Function** - This is what they call the probability distribution of a *discrete* RV - Each value has its own probability
- **Probability Density Function** - This is what they call the probability distribution of a *continuous* RV. - Each value has a probability of 0, only intervals (inequalities) can have values

## Binomial
---
*Factorial* - $n!$ 
The binomial coefficient $\binom{n}{k}$ counts the ways to choose $k$ items from $n$ without order, given by $\binom{n}{k}=\dfrac{n!}{k!\,(n-k)!}$.

#### Bernoulli Trials // Binomial Distribution
---
> Must satisfy the below criteria
1. Each trial only has two outcomes *usually success or fail*
2. Each trial is independent
3. The probability of success $p$ remains the same for each trial

 *If the above is true:*
  - Then $X$ is said to be a **Binomial RV**
  - Probability distribution of $X$ (binomial distribution) is noted as

**Formula Yields***
$p(X) = P(X=x) = \dbinom{n}{x}p^x(1-p)^{n-x}$

**Other Formula Values**
$E(X) = np$
$\sigma^2 = np(1-p)$
$\sigma  = \sqrt{np(1-p)}$

> If we are interested in proportiond just divide by $n$

## Poisson
---
*Criteria*
1. An event occurs periodically over time or space
2. Expected number of events is proportional to the length
3. Within a single interval, an infinite number of occurrences is theoretically possible
4. Events occur independently, both within same interval and between trial

#### Terminology
---
$\lambda$ = mean number of occurences over the interval

#### Function
---
$p(x) = P(X = x) = \cfrac{e^{-\lambda}\lambda^x}{x!}$
$\mu = \lambda$
$\sigma^2 = \lambda$

#### Extras
- As lambda increases, becomes less right skewed and more normal looking
- Can be approximated to a binomial if $n$ is larege and $p$ is small


## Normal Distribution
---
> No specific criteria for a normal distribution, only a standard normal

#### Standard Normal (Z)
Must have:
$\mu = 0$
$\sigma = 1$

#### Non-standard Normal
To normalize must do:
$Z = \cfrac{X-\mu}{\sigma}$

