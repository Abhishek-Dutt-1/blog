---
layout: post
title:  "Probability of two Heads"
date:   2020-08-18 19:00:00 +0530
categories: interview probability
---
<hr/>
### Problem:
A fair coin is tossed twice. What is the probability that both tosses resulted in heads, given that atleast one of the tosses resulted in heads? <br/> <br/> <br/>

<hr/>

### Solution (method 1):

Sample space \\(\Omega\\) with all the outcomes of this experiment is:

$$
\Omega = \{HT, TH, TT, HH\} 
$$

Probabilites of these 4 events:

$$
P(HT) = P(TH) = P(TT) = P(HH) = \frac{1}{4}
$$

Using definition of Conditional Probability:

$$
P(A|B) = \frac{P(A \cap B)}{P(B)}
$$

We need to find \\(P(HH \| \text{Atleast one } H)\\):

$$
\begin{aligned}
P(HH|\text{Atleast one } H) &= P(HH | HT \cup TH \cup HH) \\[2ex]
&= \frac{P(HH \cap (HT \cup TH \cup HH))}{P(HT \cup TH \cup HH)} \\[2ex]
&= \frac{P(HH)}{P(HT \cup TH \cup HH)} \\[2ex]
&= \frac{\frac{1}{4}}{\frac{1}{4} + \frac{1}{4} + \frac{1}{4}} \\[2ex]
&= \frac{1}{3}
\end{aligned}
$$
