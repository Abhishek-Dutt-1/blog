---
layout: post
title: "Geometric Distribution"
date: 2020-08-01 10:37:00 +0530
tags: theory probability
---

[Index]({{site.baseurl}}{% post_url 2020-08-10-table-of-contents %}) \| Uniform \| Normal \| Poisson \| Binomial \| [Geometric]({{site.baseurl}}{% post_url 2020-08-01-geometric-probability-distribution %})

### Bernoulli trial:
A Bernoulli trial is trial with following two properties:
- Only two possible outcomes. Often called success and failure.
- Probability of success remains the same for all trials. i.e. trials are independent.


### Geometric distribution:
Geometric distribution can usually mean on of two similar but different probability distributions.
1. Probability distribution of the number (\\(X\\)) of Bernoulli trials needed to get the first success.
- Here \\(X\\) can be any of {1, 2, 3, 4, ...}
2. Probability distribution of the number of failures (\\(X\\)) before getting the first success.
- Here \\(X\\) can be any of {0, 1, 2, 3, 4, ...}

For the rest of this article we will consider definition 1.

### Properties:
The geometric distribution gives the probability that the first occurrence of success requires \\(k\\) independent trials, each with success probability \\(p\\).

If the probability of success on each trial is \\(p\\), then the probability that the \\(k^{th}\\) trial (out of \\(k\\) trials) is the first success is:
<div>$$ P(X=k) = (1-p)^{k-1} \cdot p  \tag{1}\label{eq1}$$</div>
<div>$$ \forall \, k = 1, 2, 3, \cdots $$</div>

#### Expected Value and Variance:
The expected value for the number of independent trials to get the first success, of a geometrically distributed random variable \\(X\\): 
<div>$$ E(X) = \frac{1}{p}  \tag{2}\label{eq2}$$</div>
And its variance:
<div>$$ var(X) = \frac{1-p}{p^2}  \tag{3}\label{eq3}$$</div>

#### Calculation of Expected Value:
By definition of Expected value:
<div>$$ E(X) = \sum_{k=1}^\infty k \cdot P(X=k) $$</div>

Using the \\(P(X)\\) for Geometric distribution:

<div>$$
\begin{aligned}
E(X) &= \sum_{k=1}^\infty k \cdot (1-p)^{k-1} \cdot p \\[2ex]
\implies E(X) &= 1 \cdot (1-p)^0 \cdot p + 2 \cdot (1-p)^1 \cdot p + 3 \cdot (1-p)^2 \cdot p + 4 \cdot (1-p)^3 \cdot p + \cdots \\[2ex]
\implies E(X) &= 1 \cdot p + 2 \cdot (1-p) \cdot p + 3 \cdot (1-p)^2 \cdot p + 4 \cdot (1-p)^3 \cdot p + \cdots \\[2ex]
\end{aligned}
$$</div>
Multiplying both sides by \\((1-p)\\):
<div>$$
\begin{aligned}
\implies (1-p) \cdot E(X) &= \quad 1 \cdot (1-p) \cdot p + 2 \cdot (1-p)^2 \cdot p + 3 \cdot (1-p)^3 \cdot p + 4 \cdot (1-p)^4 \cdot p + \cdots \\[2ex]
\end{aligned}
$$</div>
Subtracting both equations:
<div>$$
\begin{aligned}
E(X) - (1-p) \cdot E(X) &= 1 \cdot p + 1 \cdot (1-p) \cdot p + 1 \cdot (1-p)^2 \cdot p + 1 \cdot (1-p)^3 \cdot p + 1 \cdot (1-p)^4 \cdot p + \cdots \\[2ex]
\implies E(X) - E(X) + p \cdot E(X) &= p + (1-p) \cdot p + (1-p)^2 \cdot p + (1-p)^3 \cdot p + (1-p)^4 \cdot p + \cdots \\[2ex]
\implies E(X) &= 1 + (1-p) + (1-p)^2 + (1-p)^3 + (1-p)^4 + \cdots \\[2ex]
\end{aligned}
$$</div>

R.H.S. is a geometric series with the first term \\(a = 1\\) and common ratio \\(r = (1-p)\\). <br/>
Sum of geometric series is given by:
<div>$$ a + ar + ar^2 + ar ^ 3 + ar ^ 4 + \cdots = \sum_{k=0}^\infty ar^k = \frac{a}{1-r}, \forall \; |r| < 1 $$</div>

Therefore \\(E(X)\\):
<div>$$
\begin{aligned}
\implies E(X) &= \frac{1}{1-(1-p)} \\[2ex]
\implies E(X) &= \frac{1}{p} \\[2ex]
\end{aligned}
$$</div>

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
