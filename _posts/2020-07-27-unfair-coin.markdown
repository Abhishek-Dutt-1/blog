---
layout: post
title:  "[Probability] Fair or Unfair Coin "
date:   2020-07-27 21:00:00 +0530
categories: interview probability
---
<hr/> <br/>

### Problem:

There is a fair coin (one side heads, one side tails) and an unfair coin (both sides tails). <br/>
You pick one at random, flip it 5 times, and observe that it comes up as tails all five times. <br/>
What is the chance that you are flipping the unfair coin? <br/> <br/>
<hr/>
<br/>

### Solution (method 1):

Let's define two events: <br/> 

<div>
$$
\begin{aligned} 
\text{Choosing the Unfair coin}&: Unfair \\
\text{Getting 5 Tails in a row}&: TTTTT \\
\end{aligned}
$$
</div>

Then, the problem is asking us to calculate:
\\[
P(Unfair | TTTTT): \text{Probability of choosing unfair coin given we got 5 Tails}
\\]


Using Bays theorem:

<div>
$$
P(Unfair | TTTTT) = \frac{ P(TTTTT | Unfair) \cdot P(Unfair) }{ P(TTTTT) } \tag{1}\label{eq1}
$$
</div>

Here:
<div>
$$
\begin{aligned} 
P(Unfair) &: \text{Probability of choosing the unfair coin} \\
P(TTTTT | Unfair) &: \text{Probability of getting 5 Tails given we are tossing the Unfair coin} \\
P(TTTTT) &: \text{Probability of getting 5 Tails} \\
\end{aligned}
$$
</div>
Along with these, we will need a couple of more probabilites to solve this problem:
<div>
$$
\begin{aligned} 
P(Fair) &: \text{Probability of choosing the fair coin} \\
P(TTTTT|Fair) &: \text{Probability of getting 5 Tails given we are tossing the fair coin} \\
\end{aligned}
$$
</div>

<br/>
Now, lets put values to these probabilites: <br/>
Probability of choosing any one of the two coins at random is 1/2:
<div>
$$ P(Unfair)=P(Fair)=\frac{1}{2} $$
</div>

Since the unfair coin will always show Tails:
<div>
$$ P(TTTTT | Unfair) = 1^5 = 1 $$
</div>

And, probability of getting 5 Tails with a fair coin:
<div>
$$
P(TTTTT|Fair) = \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} \cdot \frac{1}{2} = \left(\frac{1}{2}\right)^5
$$
</div>


Now, \\( P(TTTTT) \\) is the sum of probabilites of getting 5 Tails after choosing the fair coin and the unfair coin:
<div>$$
\begin{aligned}
P(TTTTT) &= P(Fair) \cdot P(TTTTT|Fair) + P(Unfair) \cdot P(TTTTT|Unfair) \\[2ex]
&= \left(\frac{1}{2}\right) \cdot \left(\frac{1}{2}\right)^5 + \left(\frac{1}{2}\right) \cdot 1 \\[2ex]
&= \left(\frac{1}{2}\right) \cdot \biggl(\left(\frac{1}{2}\right)^5 + 1\biggr)
\end{aligned}
$$</div>

Finally substituting all these values in our original equation \\(\eqref{eq1}\\) to get the answer:
<div>$$
\begin{aligned}
P(Unfair | TTTTT) &= \frac{ P(TTTTT | Unfair) \cdot P(Unfair) }{ P(TTTTT) } \\[2ex]
&= \frac{1 \cdot \left(\frac{1}{2}\right)}{ \left(\frac{1}{2}\right) \cdot \bigl(\left(\frac{1}{2}\right)^5 + 1\bigr) } \\[2ex]
&= \frac{1}{\bigl(\left(\frac{1}{2}\right)^5 + 1\bigr)} \\[2ex]
&= \frac{2^5}{2^5+1}
\end{aligned}
$$</div>

<br/>
<hr/>
<br/>

### Solution (method 2):

We can viusalize the probabilities using the follwoing diagram:

<div class="mermaid">
graph LR;
    A(Start)--Fair-->F("P(Fair)=1/2");
    A(Start)--Unfair-->U("P(Unfair)=1/2");
    F--TTTTT-->FT("P(TTTTT|Fair)=(1/2)^5");
    F--Not TTTTT-->FNT("P(Not TTTTT|Fair)=1-(1/2)^5");
    U--TTTTT-->UT("P(TTTTT|Unfair)=1");
    U--Not TTTTT-->UNT("P(Not TTTTT|Unfair)=0");
</div>

So the total probability of getting TTTTT:
<div>$$
P(TTTTT|Unfair) + P(TTTTT|Fair) = 1 + \left(\frac{1}{2}\right)^5
$$</div>
Of these, contribution from the Unfair coin was:
<div>$$
P(TTTTT|Unfair) = 1
$$</div>
So probability that we had the Unfair coin, given that we observed TTTTT:

<div>$$
\begin{aligned}
P(Unfair|TTTTT) &= \frac{ P(TTTTT|Unfair) }{ P(TTTTT|Unfair) + P(TTTTT|Fair) } \\[2ex]
&= \frac{ 1 }{ \bigl( 1 + \left( \frac{1}{2} \right) ^5 \bigr)} \\[2ex]
&= \frac{2^5}{2^5+1} \\[2ex]
\end{aligned}
$$</div>

https://www.quora.com/You-have-two-coins-one-of-which-is-fair-and-comes-up-heads-with-a-probability-1-2-and-the-other-which-is-biased-and-comes-up-heads-with-probability-3-4-You-randomly-pick-coin-and-flip-it-twice-and-get-heads-both-times-What-is-the-probability-that-you-picked-the-fair-coin

https://www.glassdoor.co.in/Interview/I-have-one-fair-coin-and-one-biased-two-headed-coin-and-I-put-both-in-my-pocket-I-randomly-choose-one-coin-and-flip-it-I-QTN_861522.htm

<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {
    inlineMath: [ ['$','$'], ["\\(","\\)"] ],
    displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
    processEscapes: false,
  }
});
</script>
<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
<script src="https://unpkg.com/mermaid@8.6.4/dist/mermaid.min.js"></script>
