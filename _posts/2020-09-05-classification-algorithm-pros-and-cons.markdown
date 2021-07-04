---
layout: post
title: "Pros and Cons of Common Classification Algorithms"
date: 2020-09-05 12:07:00 +0530
categories: 
---
*Source: [Reddit](https://www.reddit.com/r/learnmachinelearning/comments/imbppq/5_best_machine_learning_algorithms_for/)*

Note: <br/>
_Many of these can be considered opinions rather than facts._ <br/>
_Many of these I do not agree with._
<br/> <br/> 

<table>
  <caption>Pros and Cons of Common Classification Algorithms</caption>
  <thead><tr><th>Classifier</th><th>Pros</th><th>Cons</th></tr></thead>
  <tbody>

    <tr><td rowspan=6><b>Naive Bays Classifier</b></td><td>• Simple, easy and fast </td><td> • Expects every feature to be independent (hence "Naive"). <br/> This is rarely true. </td></tr>
    <tr><td>• Not sensitive to irrelevant features </td><td></td></tr>
    <tr><td>• Works great in practice </td><td></td></tr>
    <tr><td>• Needs less training data </td><td></td></tr>
    <tr><td>• For both multi-class and binary classification </td><td></td></tr>
    <tr><td>• Works for continuous and discrete data  </td><td></td></tr>

    <tr><th></th><th>Pros</th><th>Cons</th></tr>
    <tr><td rowspan=4><b>Decision Trees</b></td><td>• Easy to understand </td><td> • Might suffer from overfitting. </td></tr>
    <tr><td>• Easy to generate rules </td><td>• Does not easily work with non-numerical data. </td></tr>
    <tr><td>• There are almost no hyperparameters to be tuned </td><td> • Low prediction accuracy as compared to other algorithms. </td></tr>
    <tr><td>• Complex decision trees models can be significantly simplified by its visualization </td><td> • When there are many class labels, calculations can be complex. </td></tr>

    <tr><th></th><th>Pros</th><th>Cons</th></tr>
    <tr><td rowspan=6><b>Support Vector Machines</b></td><td>• Fast algorithm </td><td> • Dosn't perform well with large datasets </td></tr>
    <tr><td>• Effective in high dimensional spaces </td><td>• Not so simple to program </td></tr>
    <tr><td>• Great accuracy </td><td>• Dosen't perform so well, when the data comes with more noise i.e. target classes are overlapping </td></tr>
    <tr><td>• Power and flexibility from kernels </td><td> </td></tr>
    <tr><td>• Works very well with a clear margin of sepration </td><td> </td></tr>
    <tr><td>• Many applications </td><td> </td></tr>

    <tr><th></th><th>Pros</th><th>Cons</th></tr>
    <tr><td rowspan=5><b>Random Forest</b></td><td>• Overfitting problem does not exists </td><td> • Complexity </td></tr>
    <tr><td>• Can be used for feature engineering, i.e. for identifying the most important features</td><td>• Requires a lot of computational resources </td></tr>
    <tr><td>• Runs very well on large data sets</td><td>• Time consuming </td></tr>
    <tr><td>• Extremely flexible and have very high accuracy</td><td>• Need to choose the number of trees </td></tr>
    <tr><td>• No need for preparation of input data</td><td></td></tr>

    <tr><th></th><th>Pros</th><th>Cons</th></tr>
    <tr><td rowspan=5><b>K-Nearest Neighbours</b></td><td>• Simple to understand and easy to impliment </td><td> • Computationally expensive testing phase </td></tr>
    <tr><td>• Zero to little training time</td><td>• Can have skewed class distributions </td></tr>
    <tr><td>• Works easily with multi-class datasets </td><td>• The accuracy can be decreased when it comes to high dimensional data </td></tr>
    <tr><td>• Has good predictive power</td><td>• Needs to define value for the parameter K </td></tr>
    <tr><td>• Does well in practice</td><td> </td></tr>

  </tbody>
</table>