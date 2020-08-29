---
layout: post
title:  "Know the answer or guess the answer"
date:   2020-08-19 07:52:00 +0530
categories: interview probability
---
<hr/>
### Problem:
To answer a multiple choice question, a student may either know the answer or guess it. <br/>

Assume that with probability \\(p\\) the student knows the answer to a question, and with probability \\(q\\), the student guesses the right answer to a question she does not know. <br/>

What is the probability that for a question the student answers correctly, she actually knew the answer to the question?
<br/> <br/> <br/>

<hr/>

### Solution (method 1):

Assuming: <br/>
\\(K\\) be the event she knows the answer, and <br/>
\\(R\\) be the event that she answered the question correctly.

From the question, probabilites of events and their complement are:

$$
\begin{aligned}
P(K) &= p \\[2ex]
P(K^c) &= 1-p \\[2ex]
P(R|K) &= 1   \\[2ex]
P(R|K^c) &= q \\[2ex]
\end{aligned}
$$

We need to find \\(P(K|R)\\). <br/>
Using Bays rule:

$$
\begin{aligned}
P(K|R) &= \frac{P(R|K) \times P(K)}{P(R)} \\[2ex]
&= \frac{P(R|K) \times P(K)}{P(K) \times P(R|K) + P(K^c) \times P(R|K^c)} \\[2ex]
&= \frac{1 \times p}{p \times  1 + (1-p) \times q} \\[2ex]
&= \frac{p}{p + (1-p)q}
\end{aligned}
$$

<hr/>

### Solution (method 2):

Visualising probabilites using a tree:

<div class="mermaid">
graph LR;
    A(1)--"Knows"-->Knows("P(Knows) = p");
    A(1)--"Not Knows"-->NotKnows("P(Not Knows) = 1-p");
    Knows--"Right Answer"-->KnowsRight("P(Right Answer|Knows) = 1");
    Knows--"Not Right Answer"-->KnowsNotRight("P(Not Right Answer|Knows) = 0");
    NotKnows--"Right Answer"-->NotKnowsRight("P(Right Answer|Not Knows) = q");
    NotKnows--"Not Right Answer"-->NotKnowsNotRight("P(Not Right Answer|Not Knows) = 1-q");
</div>

<br/> Since it is given she got the right answer, we ignore the "Not Right Answer" branches.

Fraction of times where she got the \\(\text{Right Answer}\\) when she \\(\text{Knows}\\) the answer: <br/>
(Probabilites are multiplied as we move in a branch)

$$
\begin{aligned}
P(\text{Knows} \cap \text{Right Answer}) &= P(\text{Knows}) \times P(\text{Right Answer}|\text{Knows}) \\[2ex]
&= p \times 1 \\[2ex]
&= p \\[2ex]
\end{aligned}
$$

Total fraction of times she got \\(\text{Right Answer}\\) when she \\(\text{Knows}\\) and \\(\text{Not Knows}\\) the answer: <br/>
(Probabilites are added for leaves of different branches)

$$
\begin{aligned}
P(\text{Right Answer}) &= P(\text{Knows}) \times P(\text{Right Answer}|\text{Knows}) + P(\text{Not Knows}) \times P(\text{Right Answer}|\text{Not Knows}) \\[2ex]
&= p \times 1 + (1-p) \times q \\[2ex]
&= p + (1-p)q \\[2ex]
\end{aligned}
$$

So the required probability \\(P(\text{Knows}\|\text{Right Answer})\\), is the favourable cases divided by total cases:

$$
\begin{aligned}
P(\text{Knows}|\text{Right Answer}) &= \frac{P(\text{Knows} \cap \text{Right Answer})}{P(\text{Right Answer})} \\[2ex]
&= \frac{p}{p+(1-p)q} \\[2ex]
\end{aligned}
$$