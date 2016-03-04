---
layout: post
title:  "Dynamic Linear Models"
date:   2016-03-04 17:30:00 +0530
categories: Analytics
---

UNDER CONSTRUCTION
==================

PLEASE TRY AGAIN LATER
======================

Dynamic linear models are a sub set of State Space models where distribution is assumed Gaussian, yet they are incredibly useful.

In this post we will learn the common types of DLM, bit of math behind them and their implimentation in R using dlm and dlmodeler packages.
DLMs are a natural upgrade from Linear regression and their basic understanding is assumed for this post.

PS: This post uses MathJax to display equations and special symbols which do not always show up. So if you feel something is missing try reloading the page and it should show up.

So lets begin.

DLM's are composed of Observations (the $$ y_is $$), and unobserved states (the $$ \theta_is $$).

General form of DLM is:
<div>
$$
y_t = \mathbf Z_t' \mathbf a_t + \epsilon_t        \epsilon_t \sim \mathbf NID(0, \sigma_t^2) \\
\mathbf a_{t+1} = \mathbf T_t\mathbf a_t + \mathbf R_t\eta_t
$$
</div>
First equation is called as equation, and second is called State equation.


Local Level Model
=

Local Linear Trend Model
=

Seasonal Model
=

Explanatory Model
=

Intervention Model
=

Deterministic vs. Stochastic
=

<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
