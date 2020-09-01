---
layout: post
title:  "What is the expected number of coin tosses to get two heads in a row?"
date:   2020-09-01 17:13:00 +0530
categories: interview probability
---
<hr/>
### Problem:
What is the expected number of coin tosses to get two heads in a row? 
<br/> <br/> <br/>

<hr/>

_Hint: We need to find a recursive relation of \\(X\\)_

### Solution:

Let \\(X\\) be the number of tosses need to get two Heads. <br/>
So we need to find \\(E(X)\\).

$$
E(X) = \frac{1}{2} \times E(X|T) + \frac{1}{2} \times E(X|H) \\[2ex]
$$

Here: <br/>
\\(E(X\|T)\\) are expected number of tosses to get two Heads if the first toss was a Tail. <br/>
\\(E(X\|H)\\) are expected number of tosses to get two Heads if the first toss was a Head.

Suppose we start tossing the coin.

**Case 1:** First toss is **Tails**. <br/>
In this case we still need \\(X\\) **more** tosses, apart from **1** we just wasted. <br/>
Hence, total number of toss required in this case = 1 + \\(X\\)

$$
E(X|T) = 1 + E(X)
$$

**Case 2:** First toss is a **Heads** <br/>
Now there are further 2 cases: <br/>
- Second toss is a **Heads**: 
    - Here number of toss required are 2 and we dont need to toss more. <br/>
    - i.e. \\(E(X\|HH) = 2\\)
- Second toss is a **Tails**: 
    - Now 2 tosses are wasted and the number of tosses required is 2 + \\(X\\) <br/>
    - i.e. \\(E(X\|HT) = 2 + E(X)\\)

Combining both these sub-cases to find \\(E(X\|H)\\):

$$
\begin{aligned}
E(X|H) &= \frac{1}{2} \times E(X|HH) + \frac{1}{2} \times E(X|HT) \\[2ex]
&= \frac{1}{2} \times 2 + \frac{1}{2} \times (2 + E(X)) \\[2ex]
&= 1 + 1 + \frac{E(X)}{2} \\[2ex]
&= 2 + \frac{E(X)}{2} \\[2ex]
\end{aligned}
$$

Therefore

$$
\begin{aligned}
E(X) &= \frac{1}{2} \times E(X|T) + \frac{1}{2} \times E(X|H) \\[2ex]
E(X) &= \frac{1}{2} \times (1 + E(X)) + \frac{1}{2} \times (2 + \frac{E(X)}{2}) \\[2ex]
E(X) &= \frac{1}{2} + \frac{E(X)}{2} + 1 + \frac{E(X)}{4} \\[2ex]
4 \cdot E(X) &= 2 + 2 \cdot E(X) + 4 + E(X) \\[2ex]
\implies E(X) &= 6 \\[2ex]
\end{aligned}
$$
