---
layout: post
title:  "Expected value of Y = X^2"
date:   2020-08-19 09:12:00 +0530
categories: interview probability
---
<hr/>
### Problem:
Let the random variable \\(X\\) take values -2, -1, 1 and 3 with probabilites 1/4, 1/8, 1/4 and 3/8 respectively. <br/>

What is the expectation of the random variable \\(Y = X^2\\) ?
<br/> <br/> <br/>

<hr/>

### Solution (method 1):

\\(P(X)\\) maps given values to their probabilites directly. <br/>
\\(Y\\) first maps \\(X\\) to \\(X^2\\):
<div class="mermaid">
graph LR;
  AX("-2") -- "P(X)" --> AXP("1/4");
  AX -- "Y=X^2" --> AXP1("4");
  AXP1 -- "P(Y)" --> AXP;

  BX("-1") -- "P(X)" --> BXP("1/8");
  BX -- "Y=X^2" --> BXP1("1");
  BXP1 -- "P(Y)" --> BXP;

  CX("1")  -- "P(X)" --> CXP("1/4");
  CX -- "Y=X^2" --> CXP1("1");
  CXP1 -- "P(Y)" --> CXP;

  DX("3")  -- "P(X)" --> DXP("3/8");
  DX -- "Y=X^2" --> DXP1("9");
  DXP1 -- "P(Y)" --> DXP;
</div>

Two probabilites \\(\frac{1}{8}\\) and \\(\frac{1}{4}\\) for same \\(Y=1\\) are added.

i.e. \\(Y\\) takes values \\(4, 1, 9\\) and with probabilites \\(\frac{1}{4}, \frac{3}{8}, \frac{3}{8}\\).

$$
\begin{aligned}
E(Y) &= \sum_y y \cdot P(Y=y) \\[2ex]
&= 4 \cdot \frac{1}{4} + 1 \cdot \frac{3}{8} + 9 \cdot \frac{3}{8} \\[2ex]
&= \frac{19}{4} \\[2ex]
\end{aligned}
$$

<hr/>

### Solution (method 2):
By definition:

$$
\begin{aligned}
E(Y) = E(X^2) &= \sum_x x^2 \cdot P(X=x) \\[2ex]
&= (-2)^2 \cdot \frac{1}{4} + (-1)^2  \cdot \frac{1}{8} + (1)^2 \cdot \frac{1}{4} + (3)^2 \cdot \frac{3}{8} \\[2ex]
&= \frac{19}{4} \\[2ex]
\end{aligned}
$$