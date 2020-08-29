---
layout: post
title: "Estimating p-values from simulations"
date: 2020-08-10 20:42:00 +0530
---
<hr/>
### Introduction

Following are 4 very similar questions about calculating \\( p \\)-value where probability distribution is given using simulations.
<br/> <br/>
<hr/>

### Question 1

*Source: [Khan Academy](https://www.khanacademy.org/math/ap-statistics/tests-significance-ap/idea-significance-tests/e/estimating-p-values-and-making-conclusions)*

A class found a report suggesting that teenagers' foot lengths are approximately normally distributed with a mean of \\( \text{23 cm} \\) and a standard deviation of \\( \text{2.6 cm} \\). They wondered if this held true at their school, so they took a random sample of \\(n = 9\\) students. The mean foot length of students in their sample was \\( \bar x=24.\bar6\text{ cm} \\).

To see how likely a sample like theirs was to occur by random chance alone, the class performed a simulation. They simulated \\(50\\) samples of \\(n = 9\\) lengths from a normal population with a mean of \\( \text{23 cm} \\) and standard deviation of \\( \text{2.6 cm} \\). They recorded the mean of the lengths in each sample. Here are the sample means from their \\(50\\) samples:

![image]({{site.baseurl}}/assets/images/p-value-sim-q1.png)

They want to test \\( H_0: \mu=23 \text{ cm} \\) vs. \\( H_\text{a}: \mu \neq 23 \text{ cm} \\) where \\( \mu \\) is the true mean foot length.

**Based on these simulated results, what is the approximate \\(p\\)-value of the test?** <br/>
*Note: The sample result was \\( \bar x=24.\bar{6} \text{ cm} \\).*

Choose 1 answer: <br/>
(A) \\(p\text{-value}\approx 0.02\\) <br/>
(B) \\(p\text{-value}\approx 0.04\\) <br/>
(C) \\(p\text{-value}\approx 0.06\\) <br/>
(D) \\(p\text{-value}\approx 0.08\\) <br/>

### Solution
Its given that the foot lengths are normally distrubuted, but this information is not used in this question. Instead observations are simulated to estimated the probabilty density.

Things to note: <br/>
- Since alternate hypothisis is a \\( \neq \\), this will be a two tail test. <br/>
- Sample result was \\( \bar x=24.\bar{6} \text{ cm} \\), so we need to find the probability of a more extreme result in both directions. <br/>
    - i.e. we need to count the number of observations that are \\(1.6 \text{ cm}\\) above or \\(1.6 \text{ cm}\\) below the null hypothesis mean. <br/>
    - i.e. we need to count the number of observations that are greater than \\(24.6 \text{ cm}\\) or less than \\(21.4 \text{ cm}\\). <br/>

From the graph, we can see that out of \\( 50 \\) total observations, there are \\( 2 \\) observations above \\(24.6 \text{ cm}\\) and \\( 2 \\) observations below \\(21.4 \text{ cm}\\).

Hence, the required probability \\(= p\\)-value \\( = \frac{2+2}{50} = 0.08\\)

<hr/>

### Question 2

*Source: [Khan Academy](https://www.khanacademy.org/math/ap-statistics/tests-significance-ap/idea-significance-tests/e/estimating-p-values-and-making-conclusions)*

An employee at an aquarium monitors how much their sea otters eat. The amount of food a particular otter eats daily is approximately normally distributed with a mean of \\(17\\) pounds and a standard deviation of \\(1\\) pound. They suspected this otter was not eating enough, so they took a random sample \\(n=10\\) days and observed a sample mean of \\(\bar x=16.5\\) pounds of food per day.

To see how likely a sample like this was to occur by random chance alone, the employee performed a simulation. They simulated \\(40\\) samples of \\(n=10\\) values from a normal population with a mean of \\(17\\) pounds and a standard deviation of \\(1\\) pound. They recorded the mean of the values in each sample. Here are the sample means from their \\(40\\) samples:

![image]({{site.baseurl}}/assets/images/p-value-sim-q2.png)

They want to test \\(H_0: \mu=17 \text{ lbs}\\) vs. \\(H_\text{a}: \mu < 17 \text{ lbs}\\) where \\(\mu\\) is the true mean amount of food per day.

**Based on these simulated results, what is the approximate \\(p\\)-value of the test?** <br/>
*Note: The sample result was \\( \bar x=16.5 \text{ lbs} \\).*

Choose 1 answer: <br/>
(A) \\(p\text{-value}\approx 0.025\\) <br/>
(B) \\(p\text{-value}\approx 0.04\\) <br/>
(C) \\(p\text{-value}\approx 0.10\\) <br/>
(D) \\(p\text{-value}\approx 0.125\\) <br/>

### Solution

Its given that the food that this particular otter eats is normally distrubuted, but this information is not used in this question. Instead observations are simulated to estimated the probabilty density.

Things to note: <br/>
- Since alternate hypothisis is a \\( < \\), this will be a one tail test. <br/>
- Sample mean was \\( \bar x=16.5 \text{ lbs} \\), so we need to find the probability of getting a result less than or equal to \\( \bar x=16.5 \text{ lbs} \\). <br/>

From the graph, we can see that out of \\( 40 \\) total samples, there are \\( 5 \\) samples equal to or below \\(16.5 \text{ lbs}\\).

Hence, the required probability \\(= p\\)-value \\( = \frac{5}{40} = 0.125\\)

<hr/>

### Question 3

*Source: [Khan Academy](https://www.khanacademy.org/math/ap-statistics/tests-significance-ap/idea-significance-tests/e/estimating-p-values-and-making-conclusions)*

A large school district knows that \\(75\%\\), percent of students in previous years rode the bus to school. Administrators wondered if that figure was still accurate, so they took a random sample of \\(n=80\\) students and found that \\(\hat p=65\% \\) of those sampled rode the bus to school.

To see how likely a sample like this was to happen by random chance alone, the school district performed a simulation. They simulated \\(120\\) samples of \\(n=80\\) students from a large population where \\(75\%\\), percent of the students rode the bus to school. They recorded the proportion of students who rode the bus in each sample. Here are the sample proportions from their \\(120\\) samples:

![image]({{site.baseurl}}/assets/images/p-value-sim-q3.png)

They want to test \\(H_0: p=75\%\\) vs. \\(H_\text{a}: p \neq 75\%\\) where \\(p\\) is the true proportion of students in this district that ride the bus to school.

**Based on these simulated results, what is the approximate \\(p\\)-value of the test?** <br/>
*Note: The sample result was \\(\hat p=65\%\\).*

Choose 1 answer: <br/>
(A) \\(p\text{-value}\approx 0.07\\) <br/>
(B) \\(p\text{-value}\approx 0.058\\) <br/>
(C) \\(p\text{-value}\approx 0.04\\) <br/>
(D) \\(p\text{-value}\approx 0.0\bar3\\) <br/>

### Solution

Things to note: <br/>
- Since alternate hypothisis is a \\( \neq \\), this will be a two tail test. <br/>
- Sample result was \\( \hat p=65\% \\), so we need to find the probability of a more extreme result in both directions. <br/>
    - i.e. we need to count the number of observations that are \\( 10\% \\) above or \\( 10\% \\) below the null hypothesis proportion. <br/>
    - i.e. we need to count the number of observations that are greater than \\( 85\% \\) or less than \\( 65\% \\). <br/>

From the graph, we can see that out of \\( 120 \\) total observations, there are \\( 3 \\) observations above \\( 85\% \\) and \\( 4 \\) observations below \\( 65\% \\).

Hence, the required probability \\(= p\\)-value \\( = \frac{3+4}{120} = 0.058\\)

<hr/>

### Question 4

*Source: [Khan Academy](https://www.khanacademy.org/math/ap-statistics/tests-significance-ap/idea-significance-tests/e/estimating-p-values-and-making-conclusions)*

An economist read a report that claimed that \\( 60\% \\), percent of residents in her large city owned their homes. She wondered if that figure was still accurate, so she took a random sample of \\( n=50 \\) residents in the city and observed that \\( \hat p=70\% \\) of those sampled owned their homes.

To see how likely a sample like this was to happen by random chance alone, the economist performed a simulation. She simulated \\( 100 \\) samples of \\( n=50 \\) residents from a large population where \\( 60\% \\) of the residents owned their homes. She recorded the proportion of residents who owned their homes in each sample. Here are the sample proportions from her \\( 100 \\) samples:

![image]({{site.baseurl}}/assets/images/p-value-sim-q4.png)

She wants to test \\( H_0: p=60\%\\) vs. \\( H_\text{a}: p \neq 60\% \\) where \\( p \\) is the true proportion of residents in this city that own their homes.

**Based on these simulated results, what is the approximate ppp-value of the test?** <br/>
*Note: The sample result was \\( \hat p=70\% \\).

Choose 1 answer: <br/>
(A) \\(p\text{-value}\approx 0.05\\) <br/>
(B) \\(p\text{-value}\approx 0.08\\) <br/>
(C) \\(p\text{-value}\approx 0.14\\) <br/>
(D) \\(p\text{-value}\approx 0.21\\) <br/>

### Solution

Things to note: <br/>
- Since alternate hypothisis is a \\( \neq \\), this will be a two tail test. <br/>
- Sample result was \\( \hat p=70\% \\), so we need to find the probability of a more extreme result in both directions. <br/>
    - i.e. we need to count the number of observations that are \\( 10\% \\) above or \\( 10\% \\) below the null hypothesis proportion. <br/>
    - i.e. we need to count the number of observations that are greater than or equal to \\( 70\% \\) or less than or equal to \\( 50\% \\). <br/>

From the graph, we can see that out of \\( 100 \\) total observations, there are \\( 8 \\) observations above or equal to \\( 70\% \\) and \\( 13 \\) observations below or equal to \\( 50\% \\).

Hence, the required probability \\(= p\\)-value \\( = \frac{8 + 13}{100} = 0.21\\)