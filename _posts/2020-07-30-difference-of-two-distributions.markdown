---
layout: post
title:  "[Probability] Difference of Two Distributions"
date:   2020-07-30 13:36:00 +0530
categories: interview probability
---

### Problem Statement:

### Rolls to see all sides
What is the expected number of rolls needed to see all 6 sides of a fair die?

The first roll will always result in a new side being seen. Let k denote the number of sides seen from rolls already. If you have seen k sides, then the probability of rolling an unseen value will be (6-k)/6, since there are 6-k values you have not seen, and 6 possible outcomes each roll.

Note that each roll is independent of previous rolls. Therefore, for the second roll (k = 1), the time until a side not seen appears has a geometric distribution with p = 5/6 since there are 5 sides left to be seen of the 6. Likewise, after two sides (k = 2), the time taken is a geometric distribution with p = 4/6. This continues for all of the sides until all are seen.

Recalling the mean for a geometric distribution is given by 1/p, let X be the number of rolls needed and thus we have:

​	=14.7 rolls

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
