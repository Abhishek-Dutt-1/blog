---
layout: post
title: "Probability of choosing the unfair coin"
date: 2020-07-27 21:00:00 +0530
categories: interview probability
---
<hr/>
### Problem:
There is a fair coin (one side heads, one side tails) and an unfair coin (both sides tails). <br/>
You pick one at random, flip it 5 times, and observe that it comes up as tails all five times. <br/>
What is the chance that you are flipping the unfair coin? <br/> <br/> <br/>

<hr/>

### Solution (method 1):

Let's define two events:

$$
\begin{aligned} 
\text{Choosing the Unfair coin}&: Unfair \\
\text{Getting 5 Tails in a row}&: TTTTT \\
\end{aligned}
$$


Then, the problem is asking us to calculate:

$$
P(Unfair | TTTTT): \text{Probability of choosing unfair coin given we got 5 Tails}
$$


Using Bays theorem:

$$
P(Unfair | TTTTT) = \frac{ P(TTTTT | Unfair) \cdot P(Unfair) }{ P(TTTTT) } \tag{1}\label{eq1}
$$

Here:

$$
\begin{aligned} 
P(Unfair) &: \text{Probability of choosing the unfair coin} \\
P(TTTTT | Unfair) &: \text{Probability of getting 5 Tails given we are tossing the Unfair coin} \\
P(TTTTT) &: \text{Probability of getting 5 Tails} \\
\end{aligned}
$$

Along with these, we will need a couple of more probabilites to solve this problem:

$$
\begin{aligned} 
P(Fair) &: \text{Probability of choosing the fair coin} \\
P(TTTTT|Fair) &: \text{Probability of getting 5 Tails given we are tossing the fair coin} \\
\end{aligned}
$$

Now, lets put values to these probabilites: <br/>
Probability of choosing any one of the two coins at random is 1/2:

$$ P(Unfair)=P(Fair)=\frac{1}{2} $$

Since the unfair coin will always show Tails:

$$ P(TTTTT | Unfair) = 1^5 = 1 $$

And, probability of getting 5 Tails with a fair coin:

$$
P(TTTTT|Fair) = \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} = \left(\frac{1}{2}\right)^5
$$


Now, \\( P(TTTTT) \\) is the sum of probabilites of getting 5 Tails after choosing the fair coin and the unfair coin:

$$
\begin{aligned}
P(TTTTT) &= P(Fair) \cdot P(TTTTT|Fair) + P(Unfair) \cdot P(TTTTT|Unfair) \\[2ex]
&= \left(\frac{1}{2}\right) \cdot \left(\frac{1}{2}\right)^5 + \left(\frac{1}{2}\right) \cdot 1 \\[2ex]
&= \left(\frac{1}{2}\right) \cdot \biggl(\left(\frac{1}{2}\right)^5 + 1\biggr)
\end{aligned}
$$

Finally substituting all these values in our original equation \\( \eqref{eq1} \\) to get the answer:

$$
\begin{aligned}
P(Unfair | TTTTT) &= \frac{ P(TTTTT | Unfair) \cdot P(Unfair) }{ P(TTTTT) } \\[2ex]
&= \frac{1 \cdot \left(\frac{1}{2}\right)}{ \left(\frac{1}{2}\right) \cdot \bigl(\left(\frac{1}{2}\right)^5 + 1\bigr) } \\[2ex]
&= \frac{1}{\bigl(\left(\frac{1}{2}\right)^5 + 1\bigr)} \\[2ex]
&= \frac{2^5}{2^5+1}
\end{aligned}
$$

<hr/>

### Solution (method 2.1):

Suppose we repeated the experiment 10,000 times.

We can viusalize the number of cases for each event using the following tree:

<div class="mermaid">
graph LR;
    A(10,000)--"P(Fair)=1/2"-->F("5,000");
    A(10,000)--"P(Unfair)=1/2"-->U("5,000");
    F--"P(TTTTT|Fair)=(1/2)^5"-->FT("5,000 * (1/2)^5");
    F--"P(Not TTTTT|Fair)=1-(1/2)^5"-->FNT("5,000 * 1-(1/2)^5");
    U--"P(TTTTT|Unfair)=1"-->UT("5,000");
    U--"P(Not TTTTT|Unfair)=0"-->UNT("5,000 * 0");
</div>

Since its given we got 5 tails, we ignore the Not TTTTT branches.

The total number of cases where we get TTTTT:

$$
TTTTT = TTTTT|Fair + TTTTT|Unfair = 5000 \times \left(\frac{1}{2}\right)^5 + 5000
$$

Of these, contribution from the Unfair coin was:

$$
TTTTT|Unfair = 5000
$$

So probability that we had the Unfair coin, given that we observed TTTTT:

$$
\begin{aligned}
P(Unfair|TTTTT) &= \frac{ TTTTT|Unfair }{ TTTTT|Fair + TTTTT|Unfair } \\[2ex]
&= \frac{ 5000 }{ 5000 \times \left(\frac{1}{2}\right)^5 + 5000 } \\[2ex]
&= \frac{ 1 }{ \bigl( \left( \frac{1}{2} \right) ^5 + 1 \bigr)} \\[2ex]
&= \frac{2^5}{2^5+1} \\[2ex]
\end{aligned}
$$

<hr/>

### Solution (method 2.2):

Another way of visualizing the probability tree is to just multiply the probabilities as we go deeper into a branch.
This is same as taking 1 instead of 10,000 in above method.

<div class="mermaid">
graph LR;
    A(1)--"Fair"-->F("P(Fair)=1/2");
    A(1)--"Unfair"-->U("P(Unfair)=1/2");
    F--"TTTTT|Fair"-->FT("P(TTTTT|Fair)=(1/2)*(1/2)^5");
    F--"Not TTTTT|Fair"-->FNT("P(Not TTTTT|Fair)=(1/2)*(1-(1/2)^5)");
    U--"TTTTT|Unfair"-->UT("P(TTTTT|Unfair)=(1/2)*1");
    U--"Not TTTTT|Unfair"-->UNT("P(Not TTTTT|Unfair)=(1/2)*0");
</div>

Since it is given we got 5 tails, we ignore the Non TTTTT branches. <br/>
Hence, the probability that we had the Unfair coin, given that we observed TTTTT:

$$
\begin{aligned}
P(Unfair|TTTTT) &= \frac{ P(TTTTT|Unfair) }{ P(TTTTT|Fair) + P(TTTTT|Unfair) } \\[2ex]
&= \frac{ (1/2)*1 }{ (1/2) * (1/2)^5 + (1/2)*1 } \\[2ex]
&= \frac{ 1 }{ \bigl( \left( \frac{1}{2} \right) ^5 + 1 \bigr)} \\[2ex]
&= \frac{2^5}{2^5+1} \\[2ex]
\end{aligned}
$$

<hr/>
[TODO: Add baysian explaination]

https://www.quora.com/You-have-two-coins-one-of-which-is-fair-and-comes-up-heads-with-a-probability-1-2-and-the-other-which-is-biased-and-comes-up-heads-with-probability-3-4-You-randomly-pick-coin-and-flip-it-twice-and-get-heads-both-times-What-is-the-probability-that-you-picked-the-fair-coin

https://www.glassdoor.co.in/Interview/I-have-one-fair-coin-and-one-biased-two-headed-coin-and-I-put-both-in-my-pocket-I-randomly-choose-one-coin-and-flip-it-I-QTN_861522.htm

<hr/>
