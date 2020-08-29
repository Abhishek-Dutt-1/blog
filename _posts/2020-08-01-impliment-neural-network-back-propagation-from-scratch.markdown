---
layout: post
title:  "Implimenting Neural Network with Backpropagation from Scratch"
date:   2020-08-01 10:37:00 +0530
---

We will be creating a 2 layer neural netowrk for binary classification.

Input layer:
- 13 neurons, since each \\(i^{th}\\) input vector \\(x^{[i]}\\) is a (13, 1) dimensional vector.

<br/>
Hidden layer:
- 1 hidden layer with 8 neurons
- Dimensions of its weight matrix \\(W1\\) = (8, 13)
- Dimensions of its bias vector \\(b1\\) = (8, 1)
- Activation function: \\(\text{ReLU}()\\)
- Ouput: \\(a1 = \text{ReLU}( W1 \cdot x^{[i]} + b1) \\)
- Output \\(a1\\)'s dimesnions: (8, 1)

<br/>
Output layer:
- 1 output layer with 1 neuron
- Dimensions of its weight matrix \\(W2\\) = (1, 8)
- Dimensions of its bias vector \\(b2\\) = (1, 1)
- Activation function: \\(\text{Sigmoid}\\)
- Output: \\(\hat{y}^{[i]} = \text{Sigmoid}(W2 \cdot a1 + b2) \\)
- Output \\(\hat{y}^{[i]}\\)'s dimesnions: (1, 1)

<br/>
Notice that dimensions for each layer are as follows:
- Weight matrix: (neurons in this layer, neurons in the previous layer)
- Bias vector: (neurons in this layer, 1)
- Output vector: (neurons in this layer, 1)

<br/>
Loss function:
- We will use the Cross Entropy (CE) loss funtion

Definitions needed for computing Cross Entropy loss for \\(C\\) classes:
- \\(y^{[i]}\\) is the one-hot vector indicating the true class for \\(x^{[i]}\\)
  - \\(y_i\\) is the \\(i^{th}\\) component of \\(y^{[i]}\\)
- \\(\hat{y}^{[i]}\\) is the predicted probabilites of \\(x^{[i]}\\) for each of the \\(C\\) classes
  - \\(\hat{y}_i\\) is the \\(i^{th}\\) component of \\(\hat{y}^{[i]}\\)


<br/>
For \\(C\\) classes, Cross Entropy loss for one input \\(x^{[i]}\\) is given by: 
<div>$$ \text{CE} = -\sum_{i=1}^C y_i \cdot \log(\hat{y}_i) $$</div>
Here, for each input vector \\(x^{[i]}\\): <br/>
- \\(y_i\\) is the true probability that \\(x^{[i]}\\) belongs to the \\(i^{th}\\) class
- \\( \hat{y}_i \\) is the predicted probability that \\(x^{[i]}\\) belongs to the \\(i^{th}\\) class

This simplifies for a binary case \\((C=2)\\):
<div>$$ 
\begin{aligned}
\text{CE} &= -\sum_{i=1}^2 y_i \cdot \log(\hat{y}_i)  \\[2ex]
\implies \text{CE} &= - y_1 \cdot log(\hat{y}_1) - (1-y_1) \cdot log(1-\hat{y}_1)  \\
\end{aligned}
$$</div>

<br/>

### Forward Propagation:

Putting together everything discussed so far:
- We start with an input vector: \\(x^{[i]}\\)
- Output of 1st layer: \\(a1 = \text{ReLU}( W1 \cdot x^{[i]} + b1) \\)
- Output of 2nd layer: \\(\hat{y}^{[i]} = \text{Sigmoid}(W2 \cdot a1 + b2) \\)
- Finally, loss between actual and predicted: \\(\text{loss} = \text{CE}(y^{[i]}, \hat{y}^{[i]})\\)
  - \\(y^{[i]}\\) is the vector whose \\(i^{th}\\) component (\\(y_i\\)) gives the true probability of \\(x^{[i]}\\) belonging to \\(i^{th}\\) class
  - Since in our case, an input vector \\(x^{[i]}\\) can belong to only one class, \\(y^{[i]}\\) is a one-hot vector

```python
def forward(self):
  a1 = self.ReLU( np.dot(self.W1, self.X) + self.b1 )
  yHat = self.Sigmoid( np.dot(self.W2, a1) + self.b2 )
  loss = self.cross_entropy(self.y, yHat)

  self.

```


### Backpropagation:

As we saw in forward pass, starting with input vector x, we reach loss. <br/>
For backpropagation we will need to compute the derivative of \\(loss\\) with all the variables (i.e. \\(Z2, W2, b2, Z1, W1, b1\\)). <br/>
However, since we will use chain rule, we need to caluclate the derivative of loss wrt intermediate __functions__ and variables too.

We also need to compute the derivative of loss with intermediate variables (y^[i], Z1, Z2) becuase of the chain rule.

We compute derivatives in following order: <br/>
d y_1 , since loss = CE(y, y_1) <br/>
d Z2, since y_1 = sigmoid(Z2) <br/>
d W2, since Z2 = W2*a1 + b2 <br/>
d b2, since Z2 = W2*a1 + b2 <br/>
d a1, since Z2 = W2*a1 + b2  <br/>
d Z1, since a1 = ReLU(Z1) <br/>
d W1, since Z1 = W1*x + b1 <br/>
d b1, since Z1 = W1*x + b1 <br/>

loss = CE(y, Sigmoid(W2 * RELU(W1 * x+b1) + b2))
loss = CE(Sigmoid)   : since yHat = sigmoid

We will compute derivatives of functions wrt to thier inputs.  
Lets call all inputs as 'a' for this purpose.  

#### Derivative of loss:
<div>$$ \text{loss} = \text{CE}(y^{[i]}, a) $$</div>
Derivative of \\(\text{loss}\\) wrt \\(a\\):
<div>$$
\begin{aligned}
\frac{\partial \, \text{loss}}{\partial a} &= \frac{\partial}{\partial a} \left( - y_1 \cdot log(a) - (1-y_1) \cdot log(1-a) \right)  \\
&= -\frac{y_1}{a} - (1-y_1) \cdot \frac{-1}{1 - a} \\
&= -\frac{y_1}{a} + \frac{1-y_1}{1 - a} \\
\end{aligned}
$$</div>

#### Derivative of Sigmoid:
<div>$$ \text{Sigmoid}(a) = \frac{1}{1+e^{-a}} = (1+e^{-a})^{-1} $$</div>
Derivative of \\(\text{Sigmoid}\\) wrt \\(a\\):
<div>$$
\begin{aligned}
\frac{\partial \, \text{Sigmoid}}{\partial a} &= \frac{\partial}{\partial a} (1+e^{-z})^{-1} \\[2ex]
&= (-1) \cdot (1+e^{-z})^{-2} \cdot (-e^{-z}) = \frac{e^{-z}}{(1+e^{-z})^2} \\[2ex]
&= \frac{1}{1+e^{-z}} \cdot \frac{e^{-z}}{1+e^{-z}} = \frac{1}{1+e^{-z}} \cdot \frac{1+e^{-z}-1}{1+e^{-z}} \\[2ex]
&= \frac{1}{1+e^{-z}} \cdot 1 - \frac{1}{1+e^{-z}} \\[2ex]
&= \text{Sigmoid}(z) \cdot (1 - \text{Sigmoid}(z))
\end{aligned}
$$</div>

#### Derivative of Loss wrt z:
Since Z2 = W2*a1 + b2  
Derivative of Loss wrt Z2:
<div>$$
\begin{aligned}
\frac{\partial \text{Loss}}{\partial z} &= \frac{\partial \text{Loss}}{\partial a} * \frac{\partial a}{\partial z} \\[2ex]
&= \left(-\frac{y}{a} + \frac{1-y}{1 - a} \right) \cdot a(1-a) \\
\end{aligned}
$$</div>
Multiplying and dividing the first fraction by \\((1-a)\\) and the second fraction by \\(a\\):
<div>$$
\begin{aligned}
\frac{\partial \text{Loss}}{\partial z} &= \left(-\frac{y(1-a)}{a(1-a)} + \frac{a(1-y)}{a(1 - a)} \right) \cdot a(1-a) \\[2ex]
&= - y + ay + a - ay \\[2ex]
&= a - y \\
\end{aligned}
$$</div>

#### Derivative of Z wrt W:
Since Z = W*x+b
<div>$$
\begin{aligned}
\frac{\partial Z}{\partial W} &= \frac{\partial}{\partial W} (W*x+b) \\[2ex]
 &= x
\end{aligned}
$$</div>

#### Derivative of Loss wrt W:
By chain rule dL/dW = dL/da * da/dZ * dZ/dW
dL/dW = (a-y)x

[TODO] Derive this directly too

#### Derivative of Loss wrt b:
Z = Wx + b  
dZ/db = 1  
dLoss/db = dLoss/da * da/dz * dz/db  
= a-y  

[TODO] Derive this directly too


Putting all these definitions in code:

```python
def backpropagation(self, yHat):
  def dRelu(x):
    x[x<=0] = 0
    x[x>0] = 1
    return x
      
  dyHat = -(y/yHat) + (1-y)/(1-yHat)  # dLoss/dSigmoid = dLoss/da
  dSigmoid = yHat * (1 - yHat)        # dSigmoid/dz = da/dz
  dZ2 = dyHat * dSignoid              # dLoss/dZ2 = dLoss/dSigmoid * dSigmoid/dZ2 = a-y

  dA1 = np.dot(dZ2, W2.T)             # <---------- Where did this come from
  dW2 = np.dot(A1.T, dZ2)
  db2 = np.sum(dZ2, axis=0)

  dZ1 = dA1 * dReLU(Z1)
  dW1 = np.dot(X, dZ1)
  db1 = np.sum(dZ1, axis=0)

  W1 = W1 - learning_rate * dW1
  b1 = b1 - learning_rate * db1
  W2 = W2 - learning_rate * dW2
  b2 = b2 - learning_rate * db2
```

<script type="text/tikz">
  \begin{tikzpicture}
    \draw (0,0) circle (1in);
  \end{tikzpicture}
</script>

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

<link rel="stylesheet" type="text/css" href="http://tikzjax.com/v1/fonts.css">
<script src="https://tikzjax.com/v1/tikzjax.js"></script>