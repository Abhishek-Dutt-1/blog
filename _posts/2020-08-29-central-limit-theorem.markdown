---
layout: post
title:  "Central Limit Theorem"
date:   2020-08-29 10:16:00 +0530
categories: probability
---
[Central Limit Theorem]({{site.baseurl}}{% post_url 2020-08-29-central-limit-theorem %}) | [CLT: Practice Questions - I]({{site.baseurl}}{% post_url 2020-08-29-q1-central-limit-theorem %}) | [CLT: Practice Questions - II]({{site.baseurl}}{% post_url 2020-08-29-q2-central-limit-theorem %}) <br/>

<hr/>
### Definition:

When sampling is done from a population of mean \\(\mu\\) and finite standard deviation \\(\sigma\\), the sampling distribution of the sample mean \\(\overline{X}\\) will tend to a normal distribution with mean \\(\mu\\) and standard deviation \\(\frac{\sigma}{\sqrt{n}}\\) as the sample size \\(n\\) becomes large:

$$
\overline{X} \sim N \Biggl(\mu, \frac{\sigma}{\sqrt{n}} \Biggr) \text{ as } n \to \infty
$$

or equivalently:

$$
\Biggl( \frac{\overline X - \mu}{\sigma/\sqrt{n}} \Biggr) \text{ is standard normal as } n \to \infty
$$


**In simple language:**

\\(X_1, X_2, ..., X_m\\) are \\(m\\) **random samples**, each of size \\(n\\) taken (with replacement) from a population whose overall mean and variance are \\(\mu\\) and \\(\sigma^2\\) respectively.

Note: each of these \\(X_i\\) is a **set** of \\(n\\) elements, not a single value.
<br/> <br/> <br/> 


Let \\(\overline X_1, \overline X_2, ..., \overline X_m\\)  be the means of samples \\(X_1, X_2, ..., X_m\\). <br/>
Then \\(\overline X_i\\), the **sample mean** of the \\(i^{th}\\) random sample \\(X_i\\) is given by:

$$
\overline X_i = \frac{ \sum_{j=1}^{n} x_{ij} } {n}
$$

Here, \\(x_{ij}\\) is the \\(j^\text{th}\\) element of the \\(i^\text{th}\\) sample \\(X_i\\).
<br/> <br/> <br/> 


Basically, **sample mean** itself is a random variable called \\(\overline{X}\\), and \\(\overline X_1, \overline X_2, ..., \overline X_m\\) are some of the values that the \\(\overline{X}\\) can takes.

Probability distribution of this random variable is also called the **Sample distribution**.
<br/> <br/> <br/> 


And the **mean of the sample means** \\(\overline{X}\\), i.e. it is the **mean of the means** of the \\(m\\) random samples:

$$
\mu_{\overline{X}} = \frac{\sum_{i=1}^m \overline{X_i}}{m}
$$

Then, according to CLT, for large \\(n\\), **probability distribution** of \\(\overline{X}\\) starts looking like a normal distribution with mean \\(\mu\\) and standard deviation \\(\frac{\sigma}{\sqrt{n}}\\). <br/>
i.e. 

$$
\mu_{\overline{X}} \to \mu \text{ for large } n 
$$

_(Where \\(\mu\\) is the overall population mean and \\(\sigma\\) is the population standard deviation.)_ <br/>


<hr/>

### Relation with Students t-distribution:

To use the Centeral Limit Theorem, we need to know the **population standard deviation** \\(\sigma\\). <br/>
When \\(\sigma\\) is not known, we use its estimator: the **sample standard deviation** \\(S\\). <br/>
In such case, the distribution of standard statistic (where \\(S\\) is used in place of \\(\sigma\\)):

$$
\Biggl( \frac{\overline X - \mu}{S/\sqrt{n}} \Biggr)
$$

is no longer standard normal distribution.

If the population is known to be normally distributed, then this static has a **t-distribution** with \\(n-1\\) degrees of freedom.

**In Simple Language:**

Continuing with the notation developed above, \\(S\\) is the **standard deviation of the means** of the \\(m\\) random samples.

It is calculated as the square root of (Bessel-corrected) variance of the means (\\(S^2\\)):

$$
S^2 = \frac{1}{m-1} \cdot \sum_{i=1}^m (\overline X_i - \mu_{\overline{X}})^2
$$

then:

$$
\Biggl( \frac{\overline X - \mu}{S/\sqrt{n}} \Biggr) \sim \text{ t-distribution with } n-1 \text{ degrees of freedom}
$$