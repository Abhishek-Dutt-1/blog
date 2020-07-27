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

Dynamic linear models are a sub set of State Space models where distributions are assumed Gaussian, yet they are incredibly useful.

In this post we will learn the common types of DLM, bit of math behind them and their implimentation in R using dlm and dlmodeler packages.
DLMs are a natural upgrade from Linear regression and their basic understanding is assumed for this post.

PS: This post uses MathJax to display equations and special symbols which do not always show up. So if you feel something is missing try reloading the page and it should show up.

So lets begin.

DLM's are composed of Observations (the $$ y_ts $$), and unobserved states (the $$ \mathbf a_ts $$).

General form of DLM is:
<div>
$$
\begin{align}
y_t & = \mathbf Z_t' \mathbf a_t + \epsilon_t & \epsilon_t  \sim NID(0, \sigma_\epsilon^2) \\
\mathbf a_{t+1} & = \mathbf T_t\mathbf a_t + \mathbf R_t\eta_t  & \eta_t \sim NID(0, Q_t) \\
\end{align}
$$
</div>
First equation is called as Observation or Measurent equation, and second is called State equation.

Time series are composed of various components which include level, trend, season and regression.
These components can be added up to give a model of time series under observation.
These components are modeled as special cases of the genreral equation above.

Local Level Model
=
(aka Random walk plus noise model)

Level component in a DLM could be compared to the intercept (aka the constant) in a regression model. 
However level in DLM is time varying, where as intercept in regression is constant.
The 'local' in the Local level model comes form this variation with time. 
Hence the level in DLMs is 'local' and not 'global'. 

Local Level Models are represented as:
<div>
$$
\begin{align}
              y_t & = \mathbf \mu_t + \epsilon_t          & \epsilon_t \sim NID(0, \sigma_\epsilon^2) \\
\mathbf \mu_{t+1} & = \mathbf \mu_t + \mathbf R_t\eta_t   & \eta_t \sim NID(0, Q_t) \\
\end{align}
$$
</div>
If the variance in the second equation is taken as zero (deterministic case), it becomes a horizontal line and if the variance is non-zero (stochastic case) the equation defines a random walk, hence the name Random walk plus noise (noise refers to non-zero variance of observations $$ y_ts $$).

TODO:: Add a picture showing a use case

This model can be used to model the constant component of a time series.
If the time series also has an inclined trend, a trend component can be added to this local level model, such a model is unsurprisingly called a Local linear trend model.

TODO:: Hyperparameters

TODO:: Diagnostic tests

Local Linear Trend Model
=
Local Linear models are obtained by adding a slope component $$ \mathbf v_t $$ to the Local level models.
<div>
$$
\begin{align}
              y_t & = \mathbf \mu_t + \epsilon_t \qquad                   &&  \epsilon_t \sim NID(0, \sigma_\epsilon^2) \\
\mathbf \mu_{t+1} & = \mathbf \mu_t + \mathbf \nu_t + \mathbf R_t\eta_t   &&  \eta_t \sim NID(0, Q_t) \\
\mathbf \nu_{t+1} & = \mathbf \nu_t + \zeta_t                             &&  \zeta_t \sim NID(0, \sigma_\zeta^2)
\end{align}
$$
</div>


Seasonal Model
=
Seasonal models are used to capture recurring patterns in a time series, such as increase in sales during holiday seasons etc.

Seasonality in a time series is modeled using as many as state variables as the frequency of the data.
Frequency (aka seasonality) refers to the number of time periods after which pattern is supposed to repeat. e.g. for a monthly data frequency should be 12, 52 for weekly data and 4 for quarterly data.

Takin the example of quarterly data, a seasonal model (with Local level model) is represented as:

<div>
$$
\begin{align}
            y_t & = \mathbf a_t + \epsilon_t            & \epsilon_t \sim NID(0, \sigma_\epsilon^2) \\
\mathbf a_{t+1} & = \mathbf a_t + \mathbf R_t\eta_t     & \eta_t \sim NID(0, Q_t) \\
\end{align}
$$
</div>

Explanatory Model
=

Intervention Model
=

Deterministic vs. Stochastic
=

Forecast and Smoothening
=

<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
