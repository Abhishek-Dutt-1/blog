---
layout: post
title:  "Bernoulli Distribution"
date:   2020-08-19 10:42:00 +0530
categories: interview probability
---

[Bernoulli]({{site.baseurl}}{% post_url 2020-08-19-bernoulli-probobality-distribution %}) \| Binomial \| [Geometric]({{site.baseurl}}{% post_url 2020-08-01-geometric-probability-distribution %}) \| Uniform \| Normal \| Poisson 

Consider a random variable \\(X\\) which can have only two possible values \\(1\\) or \\(0\\). <br/>
It takes value \\(1\\) with probability \\(p\\) and \\(0\\) with \\(1-p\\):

$$
\begin{aligned}
P(X=1) &= p \\
P(X=0) &= (1-p) \\
\end{aligned}
$$

It is used to represent the possible outcomes of a **single** experiment which has binary outcomes. <br/>
E.g. It can be used to represent a possibly biased coin toss where probability of \\(\text{Heads}\\) is \\(p\\).

The Bernoulli distribution is a special case of the Binomial distribution with \\(n = 1\\).

### Expected Value

$$
\begin{aligned}
E(X) &= \sum_x x \cdot P(X=x) \\[2ex]
&= 1 \cdot p + 0 \cdot (1-p) \\[2ex]
\implies E(X) &= p \\[2ex]
\end{aligned}
$$

### Variance:
By definition:

$$
\begin{aligned}
Var(X) &= E(X^2) - E(X)^2 \\[2ex]
\end{aligned}
$$

Where:

$$
\begin{aligned}
E(X^2) &= \sum_x x^2 \cdot P(X=x) = 1^2 \cdot p + 0^2 \cdot (1-p) = p
\end{aligned}
$$

Therefore:

$$
\begin{aligned}
Var(X) = p - p^2 = p(1-p)
\end{aligned}
$$

