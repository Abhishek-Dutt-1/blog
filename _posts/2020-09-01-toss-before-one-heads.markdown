---
layout: post
title:  "What is the expected number of coin tosses to get one heads?"
date:   2020-09-01 19:14:00 +0530
categories: interview probability
---
<hr/>
### Problem:
What is the expected number of coin tosses to get one heads? <br/> <br/> <br/>

<hr/>

### Solution (method 1):

Let \\(X\\) be the number of tosses required to get a Head. <br/>
We need to calulate \\(E(X)\\).

Suppose we start tossing the coin. <br/>
We have two cases, each with probability 1/2. <br/>

$$
E(X) = \frac{1}{2} \times E(X|H) + \frac{1}{2} \times E(X|T)
$$

Here:
\\(E(X|H)\\) is the expected number of tosses required to get a Head given that first toss was a Head.
\\(E(X|T)\\) is the expected number of tosses required to get a Head given that first toss was a Tails.

**Case 1:**
If first toss is a head, number of tosses \\(X\\) = 1.
i.e. \\(E(X|H) = 1\\).

**Case 2:**
If first toss is a tails, then we wasted 1 toss and we still need X tosses more.
i.e. \\(E(X|T) = 1 + E(X)\\).

Combining the two cases to get \\(E(X)\\):

$$
\begin{aligned}
E(X) &= \frac{1}{2} \times E(X|H) + \frac{1}{2} \times E(X|T) \\[2ex]
&= \frac{1}{2} \times 1 + \frac{1}{2} \times (1 + E(X)) \\[2ex]
&= \frac{1}{2} + \frac{1}{2} + \frac{E(X)}{2} \\[2ex]
\implies E(X) &= 1 + \frac{E(X)}{2} \\[2ex]
\implies E(X) &= 2 \\[2ex]
\end{aligned}
$$

<hr/>

### Solution (method 2):

By definition, number of trials needed to get the first success (\\(X\\)) follows the [Geometric distribution]({{site.baseurl}}{% post_url 2020-08-01-geometric-probability-distribution %}).

Let \\(p\\) be the probability of success. <br/>
Then, expected values of \\(X\\) in Geometric distribution is given by:

$$
E(X) = \frac{1}{p}
$$

For a fair coin toss: 

$$
p = \frac{1}{2}
$$

Therefore:

$$
E(X) = \frac{1}{p} = 2
$$