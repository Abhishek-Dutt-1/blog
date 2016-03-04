---
layout: post
title:  "Dynamic Linear Models"
date:   2016-03-04 17:30:00 +0530
categories: Analytics
---
Dynamic linear models are a sub set of State Space models where distribution is assumed Gaussian, yet they are incredibly useful.

In this post we will learn the common types of DLM, bit of math behind them and thier implimentation in R using dlm and dlmodeler packages.
DLMs are a natural upgrade from Linear regression and their basic understanding is assumed for this post.

PS: This post uses MathJax to display equations and special symbols which does not always show up. So if you feel something is missing try reloading the page and it should show up.

So lets begin.

DLM's are composed of Observations (the Ys), and unobserved states (the Xs)



<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
