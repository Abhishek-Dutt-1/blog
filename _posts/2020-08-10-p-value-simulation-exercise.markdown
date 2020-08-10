---
layout: post
title: "Estimating p-values from simulations"
date: 2020-08-10 20:42:00 +0530
---

### Question 1: 
A nutritionist suspected that her company's clients had below average cholesterol. They obtained a random sample of \\(8\\) clients of the same age and gender. These clients had a mean cholesterol level of \\( \bar x=4.28 \text{ mmol/L} \\) (millimoles per liter).

To see how likely a sample like this was to happen by random chance alone, the nutritionist performed a simulation. They simulated \\(60\\) samples of \\(n=8\\) cholesterol levels from a normal population with a mean of \\(4.6 \text{ mmol/L}\\) and a standard deviation of \\(0.5 \text{ mmol/L}\\) (these are generally accepted values for people with the same age and gender of those in the sample). 

They recorded the mean of the cholesterol levels in each sample. Here are the sample means from their \\(60\\) samples:

---

<canvas id="myChart" width="200" height="200"></canvas>


---

They want to test \\(H_0: \mu=4.6 \text{ mmol/L}\\) vs. \\(H_\text{a}: \mu<4.6 \text{ mmol/L}\\) where \\(\mu\\) is the mean cholesterol level for all clients like those sampled.

Based on these simulated results, what is the approximate ppp-value of the test?

Source: [Khan Academy](https://www.khanacademy.org/math/ap-statistics/tests-significance-ap/idea-significance-tests/e/estimating-p-values-and-making-conclusions)


<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/2.9.3/Chart.bundle.min.js" integrity="sha512-vBmx0N/uQOXznm/Nbkp7h0P1RfLSj0HQrFSzV8m7rOGyj30fYAOKHYvCNez+yM8IrfnW0TCodDEjRqf6fodf/Q==" crossorigin="anonymous"></script>

<script>
var ctx = document.getElementById('myChart').getContext('2d');
var myChart = new Chart(ctx, {
    type: 'bar',
    data: {
        labels: ['Red', 'Blue', 'Yellow', 'Green', 'Purple', 'Orange'],
        datasets: [{
            label: '# of Votes',
            data: [12, 19, 3, 5, 2, 3],
            backgroundColor: [
                'rgba(255, 99, 132, 0.2)',
                'rgba(54, 162, 235, 0.2)',
                'rgba(255, 206, 86, 0.2)',
                'rgba(75, 192, 192, 0.2)',
                'rgba(153, 102, 255, 0.2)',
                'rgba(255, 159, 64, 0.2)'
            ],
            borderColor: [
                'rgba(255, 99, 132, 1)',
                'rgba(54, 162, 235, 1)',
                'rgba(255, 206, 86, 1)',
                'rgba(75, 192, 192, 1)',
                'rgba(153, 102, 255, 1)',
                'rgba(255, 159, 64, 1)'
            ],
            borderWidth: 1
        }]
    },
    options: {
        scales: {
            yAxes: [{
                ticks: {
                    beginAtZero: true
                }
            }]
        }
    }
});
</script>