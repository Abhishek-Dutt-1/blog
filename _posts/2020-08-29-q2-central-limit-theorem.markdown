---
layout: post
title:  "CLT: Practice Questions - II"
date:   2020-08-29 19:28:00 +0530
categories: probability clt
---

[Central Limit Theorem]({{site.baseurl}}{% post_url 2020-08-29-central-limit-theorem %}) | [CLT: Practice Questions - I]({{site.baseurl}}{% post_url 2020-08-29-q1-central-limit-theorem %}) | [CLT: Practice Questions - II]({{site.baseurl}}{% post_url 2020-08-29-q2-central-limit-theorem %}) <br/>

<hr/>
### Problem 1:

*Source: [Khan Academy](https://www.khanacademy.org/math/ap-statistics/sampling-distribution-ap/sampling-distribution-mean/e/finding-probabilities-sample-means)*

A pizza chain monitors the total weight of pepperoni that goes on its deluxe pepperoni pizzas to make sure customers are satisfied and product isn't being wasted.

Suppose that for pizzas in this population, these weights are strongly skewed to the left with a mean of \\(250 \text{ g}\\) and a standard deviation of \\(8 \text{g}\\).

Management takes a random sample of \\(64\\) of these pizzas and calculates the mean weight of the pepperoni on the pizzas. Assume that the pizzas in the sample are independent.

**What is the probability that the mean weight of the pepperoni from the sample of \\(64\\) pizzas \\(\bar{x}\\) is within \\(1\,\text{g}\\) of the true mean?**

**Choose 1 answer:** <br/>
A) \\(P(249 < \overline{x} < 251) \approx 0.09 \\) <br/>
B) \\(P(249 < \overline{x} < 251) \approx 0.34 \\) <br/>
C) \\(P(249 < \overline{x} < 251) \approx 0.68 \\) <br/>
D) \\(P(249 < \overline{x} < 251) \approx 0.95 \\) <br/>
E) We cannot calculate this probability because the sampling distribution is not normal.
<br/> <br/> <br/>

<hr/>

### Solution:

Useful information given in the question: <br/>
Population mean \\(\mu\\) = \\(250 \text{ g}\\) <br/>
Population standard deviation \\(\sigma\\) = \\(8 \text{ g}\\) <br/>
Sample size \\(n\\) = \\(64\\) <br/>
Since \\(n \geqslant 30\\) we can assume CLT is valid in this case. <br/>

From CLT we know that probability distribution of mean weight of pepperoni from \\(64\\) samples will follow the normal distribution with mean \\(\mu\\) and standard deviation \\(\sigma/\sqrt{n}\\).

Therefore: <br/>
Mean of the sample mean's probability distribution = \\(\mu_{\overline{x}}\\) = \\(\mu\\) = \\(250 \text{ g}\\) <br/>
Standard deviation of the sample mean's probability distribution = \\(\sigma_{\overline{x}}\\) = \\(\sigma/\sqrt{n}\\) = \\(8/\sqrt{64}\\) = 1 <br/>

Now, the requried probability \\(p\\) is: 

$$
\begin{aligned}
p = P(249 < \overline{x} < 251) \\[2ex] 
\text{Here: } \overline{x} \sim N \Bigl( \mu, \frac{\sigma}{\sqrt{n}} \Bigr)
\end{aligned}
$$

Converting it to standard normal: 

$$
\begin{aligned}
p &= P(249 < \overline{x} < 251) \\[2ex]
&= P \Bigl( \frac{249-\mu}{\sigma/\sqrt{n}} < \Bigl( \frac{\overline{x} - \mu}{\sigma/\sqrt{n}} \Bigr) < \frac{251-\mu}{\sigma/\sqrt{n}} \Bigr) \\[2ex]
&= P \Bigl( \frac{249-250}{1} < \Bigl( \frac{\overline{x} - 250}{1} \Bigr) < \frac{251-250}{1} \Bigr) \\[2ex]
&= P \Bigl( -1 < \Bigl( \frac{\overline{x} - 250}{1} \Bigr) < 1 \Bigr) \\[2ex]
&= P(-1 < z < 1) \\[2ex]
\text{Here: } z &= \frac{\overline{x} - 250}{\sigma/\sqrt{n}} \sim N(0, 1)
\end{aligned}
$$

Finally, solving:

$$
\begin{aligned}
p &= P(249 < \overline{x} < 251) \\[2ex]
&= P(-1 < z < 1) \\[2ex]
&= 2 \times (0.5 - P( z < -1)) \\[2ex]
\end{aligned}
$$

Looking at the z-table: 

$$
P( z < -1) \approx 0.1587
$$

Therefore:

$$
\begin{aligned}
p &= 2 \times (0.5 - 0.1587) \\[2ex]
&= 0.6826 \\[2ex]
\end{aligned}
$$

Correct answer is **option (C)**.

<hr/>

### Problem 2:

*Source: [Khan Academy](https://www.khanacademy.org/math/ap-statistics/sampling-distribution-ap/sampling-distribution-mean/v/sampling-distribution-example-problem)*

The average male drinks 2 L of water when active outdoors (with a standard deviation of 0.7 L).

You are planning a full day nature trip for 50 men and will bring 110 L of water. 

**What is the probability that you will run out?**
<br/> <br/> <br/>

<hr/>

### Solution:

Useful information given in the question: <br/>
Population mean \\(\mu\\) = \\(2\\) L <br/>
Population standard deviation \\(\sigma\\) = \\(0.7\\) L <br/>
Sample size \\(n\\) = \\(50\\) <br/>
Since \\(n \geqslant 30\\) we can assume CLT is valid in this case. <br/>

From CLT we know that probability distribution of average water consumed from \\(50\\) samples will follow the normal distribution with mean \\(\mu\\) and standard deviation \\(\sigma/\sqrt{n}\\).

Therefore: <br/>
Mean of the sample mean's probability distribution = \\(\mu_{\overline{x}}\\) = \\(\mu\\) = \\(2\\) L<br/>
Standard deviation of the sample mean's probability distribution = \\(\sigma_{\overline{x}}\\) = \\(\sigma/\sqrt{n}\\) = \\(0.7/\sqrt{50}\\) = 0.09899 <br/>

We will run out of water if on average people drink more than: \\(\frac{110}{50} = {2.2}\\) L 

Therefore, the requried probability \\(p\\) is: 

$$
\begin{aligned}
p = P(\overline{x} > 2.2) \\[2ex] 
\text{Here: } \overline{x} \sim N \Bigl( \mu, \frac{\sigma}{\sqrt{n}} \Bigr)
\end{aligned}
$$

Converting it to standard normal: 

$$
\begin{aligned}
p &= P(\overline{x} > 2.2) \\[2ex] 
&= P \Bigl( \Bigl( \frac{\overline{x} - \mu}{\sigma/\sqrt{n}} \Bigr) > \frac{2.2-\mu}{\sigma/\sqrt{n}} \Bigr) \\[2ex]
&= P \Bigl( \Bigl( \frac{\overline{x} - 2}{0.09899} \Bigr) > \frac{2.2-2}{0.09899} \Bigr) \\[2ex]
&= P \Bigl( \Bigl( \frac{\overline{x} - 2}{0.09899} \Bigr) > 2.0204 \Bigr) \\[2ex]
&= P( z > 2.0204 ) \\[2ex]
&= 1 - P( z < 2.0204 ) \\[2ex]
\text{Here: } z &= \frac{\overline{x} - 2}{\sigma/\sqrt{n}} \sim N(0, 1)
\end{aligned}
$$

Looking at the z-table: 

$$
P( z < 2.0204) \approx 0.9783
$$

Therefore:

$$
\begin{aligned}
p &= P(\overline{x} > 2.2) \\[2ex] 
&= 1 - P( z < 2.0204 ) \\[2ex]
&= 1 - 0.9783 \\[2ex]
&= 0.0217 \\[2ex]
&= 2.17 \% \\[2ex]
\end{aligned}
$$



<hr/>
### Problem 3:

*Source: [Khan Academy](https://www.khanacademy.org/math/ap-statistics/sampling-distribution-ap/sampling-distribution-mean/e/finding-probabilities-sample-means)*

Houseflies have pretty short lifespans. Males of a certain species have lifespans that are strongly skewed to the right with a mean of \\(26\\) days and a standard deviation of \\(12\\) days. A biologist collects a random sample of \\(9\\) of these male houseflies and observes them to calculate the sample mean lifespan.

**What is the probability that the mean lifespan from the sample of \\(9\\) houseflies \\(\bar{x}\\) is less than \\(24\\) days?**

**Choose 1 answer:** <br/>
A) \\(P( \overline{x} < 24 ) \approx 0.31\\) <br/>
B) \\(P( \overline{x} < 24 ) \approx 0.35\\) <br/>
C) \\(P( \overline{x} < 24 ) \approx 0.39\\) <br/>
D) \\(P( \overline{x} < 24 ) \approx 0.43\\) <br/>
E) We cannot calculate this probability because the sampling distribution is not normal.
<br/> <br/> <br/>

<hr/>

### Solution:

Useful information given in the question: <br/>
Population mean \\(\mu\\) = \\(26\\) days <br/>
Population standard deviation \\(\sigma\\) = \\(12\\) days <br/>
Sample size \\(n\\) = \\(9\\) <br/>

For Central Limit Thoerom to hold, it requires that:
- Either \\(n\\) is large (usually \\(\geqslant 30\\)) 
- Or, the population distribution is normal

Since the parent population is not normally distributed, the small sample size of \\(9\\) will result in a sampling distribution that isn't normal.

Hence, we cannot calculate this probability because the sampling distribution is not normal.

Correct answer is **option (D)**.

<hr/>
### Problem 4:

*Source: [Khan Academy](https://www.khanacademy.org/math/ap-statistics/sampling-distribution-ap/sampling-distribution-mean/e/finding-probabilities-sample-means)*

A manufacturer makes integrated circuits that each have a resistance layer with a target thickness of \\(200\\) units. A circuit won't work well if this thickness varies too much from the target value. These thickness measurements are approximately normally distributed with a mean of \\(200\\) units and a standard deviation of \\(12\\) units. A random sample of \\(16\\) measurements is selected for a quality inspection. We can assume that the measurements in the sample are independent.

**What is the probability that the mean thickness in these \\(16\\) measurements \\(\bar{x}\\) is farther than \\(3\\) units away from the target value?**

**Choose 1 answer:** <br/>
A) 0.16 <br/>
B) 0.32 <br/>
C) 0.40 <br/>
D) 0.80 <br/>
E) We cannot calculate this probability because the sampling distribution is not normal. <br/>
<br/> <br/> <br/>

<hr/>

### Solution:

Useful information given in the question: <br/>
Population mean \\(\mu\\) = \\(200\\) units <br/>
Population standard deviation \\(\sigma\\) = \\(12\\) units <br/>
Sample size \\(n\\) = \\(16\\) <br/>

Although \\(n \lt 30\\) but the population is (apporximately) normally distributed so we can assume CLT is valid in this case.<br/>

From CLT we know that probability distribution of mean thickness of \\(16\\) samples will follow the normal distribution with mean \\(\mu\\) and standard deviation \\(\sigma/\sqrt{n}\\).

Therefore: <br/>
Mean of the sample mean's probability distribution = \\(\mu_{\overline{x}}\\) = \\(\mu\\) = \\(200\\) units<br/>
Standard deviation of the sample mean's probability distribution = \\(\sigma_{\overline{x}}\\) = \\(\sigma/\sqrt{n}\\) = \\(12/\sqrt{16}\\) = 3 <br/>

Now, the requried probability \\(p\\) is: 

$$
\begin{aligned}
p &= P(\overline{x} < 197 \text{ || } \overline{x} > 203)  \\[2ex] 
\text{Here: } & \overline{x} \sim N \Bigl( \mu, \frac{\sigma}{\sqrt{n}} \Bigr)
\end{aligned}
$$

Converting it to standard normal: 

$$
\begin{aligned}
p &= P(\overline{x} < 197 \text{ || } \overline{x} > 203)  \\[2ex] 
&= 2 \times P(\overline{x} < 197) \\[2ex]
&= 2 \times P \Bigl( \Bigl( \frac{\overline{x} - \mu}{\sigma/\sqrt{n}} \Bigr) < \frac{197-\mu}{\sigma/\sqrt{n}} \Bigr) \\[2ex]
&= 2 \times P \Bigl( \Bigl( \frac{\overline{x} - 200}{3} \Bigr) < \frac{197-200}{3} \Bigr) \\[2ex]
&= 2 \times P \Bigl( \Bigl( \frac{\overline{x} - 200}{3} \Bigr) < -1 \Bigr) \\[2ex]
&= 2 \times P( z < -1) \\[2ex]
\text{Here: } z &= \frac{\overline{x} - 200}{3} \sim N(0, 1)
\end{aligned}
$$

From the z-table: 

$$
P( z < -1) \approx 0.1587
$$

Therefore:

$$
\begin{aligned}
p &= P(\overline{x} < 197 \text{ || } \overline{x} > 203)  \\[2ex] 
&= 2 \times P( z < -1) \\[2ex]
&= 2 \times 0.1587 \\[2ex]
&= 0.3174 
\end{aligned}
$$

Correct answer is **option (B)**.



<hr/>
### Problem 5:

*Source: [Khan Academy](https://www.khanacademy.org/math/ap-statistics/sampling-distribution-ap/sampling-distribution-mean/e/finding-probabilities-sample-means)*

A scientist studying water quality measures the lead level in parts per billion (ppb) at each of \\(49\\) randomly chosen locations along a water line. Suppose that the lead levels across all the locations on this line are strongly skewed to the right with a mean of \\(17\,\text{ppb}\\) and a standard deviation of \\(14\,\text{ppb}\\). Assume that the measurements in the sample are independent.

**What is the probability that the mean lead level from the sample of \\(49\\) measurements \\(\bar{x}\\) is less than \\(15\,\text{ppb}\\)?** <br/>

**Choose 1 answer:** <br/>
A) \\(P(\overline{x} <15) \approx 0.02\\) <br/>
B) \\(P(\overline{x} <15) \approx 0.16\\) <br/>
C) \\(P(\overline{x} <15) \approx 0.30\\) <br/>
D) \\(P(\overline{x} <15) \approx 0.44\\) <br/>
E) We cannot calculate this probability because the sampling distribution is not normal.

<br/> <br/> <br/>

<hr/>

### Solution:

Useful information given in the question: <br/>
Population mean \\(\mu\\) = \\(17 \text{ ppb}\\) <br/>
Population standard deviation \\(\sigma\\) = \\(14 \text{ ppb}\\) <br/>
Sample size \\(n\\) = \\(49\\) <br/>
Since \\(n \geqslant 30\\) we can assume CLT is valid in this case. <br/>

From CLT we know that probability distribution of mean lead levels from \\(49\\) samples will follow the normal distribution with mean \\(\mu\\) and standard deviation \\(\sigma/\sqrt{n}\\).

Therefore: <br/>
Mean of the sample mean's probability distribution = \\(\mu_{\overline{x}}\\) = \\(\mu\\) = \\(17 \text{ ppb}\\) <br/>
Standard deviation of the sample mean's probability distribution = \\(\sigma_{\overline{x}}\\) = \\(\sigma/\sqrt{n}\\) = \\(14/\sqrt{49}\\) = 2 <br/>

Now, the requried probability \\(p\\) is: 

$$
\begin{aligned}
p = P(\overline{x} < 15) \\[2ex] 
\text{Here: } \overline{x} \sim N \Bigl( \mu, \frac{\sigma}{\sqrt{n}} \Bigr)
\end{aligned}
$$

Converting it to standard normal: 

$$
\begin{aligned}
p &= P(\overline{x} < 15) \\[2ex]
&= P \Bigl( \Bigl( \frac{\overline{x} - \mu}{\sigma/\sqrt{n}} \Bigr) < \frac{15-\mu}{\sigma/\sqrt{n}} \Bigr) \\[2ex]
&= P \Bigl( \Bigl( \frac{\overline{x} - 17}{2} \Bigr) < \frac{15-17}{2} \Bigr) \\[2ex]
&= P \Bigl( \Bigl( \frac{\overline{x} - 17}{2} \Bigr) < -1 \Bigr) \\[2ex]
&= P(z < -1) \\[2ex]
\text{Here: } z &= \frac{\overline{x} - 17}{2} \sim N(0, 1)
\end{aligned}
$$

Looking at the z-table: 

$$
P(z < -1) \approx 0.1587
$$

Therefore:

$$
\begin{aligned}
p &= P(\overline{x} < 15) \\[2ex]
&= P(z < -1) \\[2ex]
&= 0.1587 \\[2ex]
\end{aligned}
$$

Correct answer is **option (B)**.
