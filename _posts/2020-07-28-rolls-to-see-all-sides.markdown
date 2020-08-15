---
layout: post
title:  "Rolls to See All Sides of a Die"
date:   2020-07-28 21:54:00 +0530
categories: interview probability
---
<hr/>

### Problem:

What is the expected number of rolls needed to see all 6 sides of a fair die? <br/> <br/>
[Index]({{site.baseurl}}{% post_url 2020-08-10-table-of-contents %}) <br/>

<hr/>

### Solution:
Let number of sides already seen = \\(k\\), here \\(k\\) = 0, 1, 2, 3, 4, 5, 6 <br/>
Probability of seeing the a new side, after seeing \\(k\\) sides already \\(= \frac{6-k}{6} \\) <br/>

Probability distribution of seeing a new side follows the Geometric Distribution. <br/>
For Geometric Distributions, the expected number of rolls to see new side is given by: <br/>

$$
E(X) = \frac{1}{p} = \frac{6}{6-k} = \text{Number of rolls needed to see a new side, having already seen k unique sides.}
$$

Here: <br/>
\\(X\\): random variable denoting the number of rolls needed to see the new side <br/>
\\(p\\): probability of success (i.e. seeing a new side) on a roll.

Hence, expected number of rolls needed to see all sides:

$$
\begin{aligned}
\sum_{k=0}^{5} \frac{6}{6-k} &= 1 + \frac{6}{5} + \frac{6}{4} + \frac{6}{3} + \frac{6}{2} + \frac{6}{1} \\
&= 14.7 \\
\end{aligned}
$$

Ref. [Geometric Distribution]({{site.baseurl}}{% post_url 2020-08-01-geometric-probability-distribution %}) for more details.

<hr/>

### Solution Discussion:

Basically required answer is:
```
Average number of rolls needed to see all sides = 
  Av. number of rolls needed to see 1st new side
+ Av. number of rolls needed to see 2nd new side after seeing 1st side
+ Av. number of rolls needed to see 3rd new side after seeing 2 unique sides
+ Av. number of rolls needed to see 4th new side after seeing 3 unique sides
+ Av. number of rolls needed to see 5th new side after seeing 4 unique sides
+ Av. number of rolls needed to see 6th new side after seeing 5 unique sides
```
In other words, then average number of rolls needed to see **all** sides is:

$$
= E(X)_{k=0} + E(X)_{k=1} + E(X)_{k=2} + E(X)_{k=3} + E(X)_{k=4} + E(X)_{k=5}
$$

Where \\(k\\) is the number of sides already seen.

<hr/>

Lets consider the scenario:

**On first roll:** <br/>
We will see the first new side on the first roll. <br/>

**On second roll:** <br/>
There's a \\(\frac{5}{6}\\) probability of seeing a new side. <br/>
Suppose, we get the same side as on the first roll. <br/>

**On third roll:** <br/>
Probability of seenig a new side is still \\(\frac{5}{6}\\). <br/>
Suppose, again we get the same side as on the first roll. <br/>

**On fourth roll:** <br/>
Probability of seenig a new side is still \\(\frac{5}{6}\\). <br/>
This time we get a success, i.e. we get any one of the 5 unseen sides of the die. <br/>

In this example we saw the second side in 3 rolls, but it could have potentially been any of the 1st or 2nd or 3rd or 4th or 5th or 10th or 10,000th roll. i.e. any number between 1 and infinity. <br/>

If we try this whole scenario again, we might see the second new side on some different roll (say 5). <br/>

But what we need is the average (expected) number of rolls needed to see the second new side of the die. <br/>

<hr/>

Let the number of rolls needed untill we see the second new side be the random variable \\(X\\), and probability of seeing this new side is \\(p = \frac{5}{6}\\) as before. <br/>

$$
\begin{aligned}
P(X=1) &= \frac{5}{6} \\[2ex]
P(X=2) &= \left(1-\frac{5}{6}\right) * \frac{5}{6} \quad &&\text{(i.e. first is a failure, 2nd is success)} \\[2ex]
P(X=3) &= \left(1-\frac{5}{6}\right)^2 * \frac{5}{6} \quad &&\text{(i.e. first and second are a failure, 3rd is success)} \\[2ex]
& \cdots \\
P(X=k) &= \left(1-\frac{5}{6}\right)^{k-1} * \frac{5}{6} \quad &&\text{(i.e. first k-1 are a failure, k is success)} \\[2ex]
\end{aligned}
$$

This \\(P(X)\\) is known as the Geometric Distribution.

<hr/>

Even without stating explicitly like above, we can observe that:
- On each roll there can be just two outcomes, success (we see a new side) and failure (we see an old side of the die).
- Probability of success does not change with each roll.

In such trials, probability of getting a success in \\(k^{th}\\) trial follows the Geometric Distribution:

$$
P(X=k) = (1-p)^{k-1} \cdot p
$$

Expected value of a Geometric Distribution is well known:

$$ E(X) = \frac{1}{p} $$

<hr/>

So on average we can expect to see the second new face in \\(E(X) = \frac{1}{p} = \frac{6}{5} \\) rolls after seeing the first one.

Therefore after \\(\left(1 + \frac 6 5 \right)\\) rolls on average we would have seen 2 unqiue sides.

Continuing with similar argument for 3rd unseen side of the die (after seeing 2 unqiue sides already): <br/>
Probability of seeing the 3rd new side is \\(\frac{4}{6}\\). <br/>
Therefore, we will see this 3rd new side in average \\(\frac{6}{4}\\) rolls. <br/>

Similarly to see the 4th, 5th and 6th side, we would have seen 3, 4 and 5 new sides already and have 3, 2 and 1 unseen sides remaining respectively. <br/>

This means the probability of seeing the 4th, 5th and 6th as yet unseen side of the die are \\(\frac{3}{6}, \frac{2}{6}, \frac{1}{6} \\). <br/>

On average we will see the 4th, 5th and 6th unseen side in \\(\frac{6}{3}, \frac{6}{2}, \frac{6}{1} \\) roll respectively, after seeing the previous new side. <br/>

To get the expected number of rolls needed to see all the sides, we add all the expected number of rolls to see 1st, 2nd, 3rd, 4th, 5th and 6th new side.

$$
\begin{aligned}
&= 1 + \frac{6}{5} + \frac{6}{4} + \frac{6}{3} + \frac{6}{2} + \frac{6}{1} \\[2ex]
&= 14.7 \\[2ex]
\end{aligned}
$$

[Back to Index]({{site.baseurl}}{% post_url 2020-08-10-table-of-contents %})
