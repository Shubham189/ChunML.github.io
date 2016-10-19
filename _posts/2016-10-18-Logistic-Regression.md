---
title: "Machine Learning Part 6: Logistic Regression"
categories:
  - Tutorial
tags:
  - machine-learning
  - logistic-regression
  - classification
  - essential
---
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
Hello there, I am back with you today. In the 6th post on Machine Learning tutorials series, I will tell you about Logistic Regression, a very important and must-know algorithm. Before I go any further, there is one thing I want you to be clear at first. The algorithm's name, Logistic Regression, is somehow confusing a little bit, but we are not dealing with a regression problem, but a **classification problem**.

But what is the difference between regression problems and classification problems? - You may ask. I am not a statistical expert, and you may not want any detailed academic explanations, so I will make it simply like below.

A regression problem is where you have a **continuous** dataset of label \\(y\\), and your goal is to make predictions for unlabeled data. Because \\(y\\) is continuous, it can take any value between a specific range. Concretely, if our problem's output range is \\(1 ~ 10\\), then \\(y\\) can be any value between that range, such as \\(1.2, 2.5\\) or even \\(4.23424324\\), etc. A regression problem's graph will mostly look like the graph I showed you in [Linear Regression](https://chunml.github.io/ChunML.github.io/tutorial/Linear-Regression/) tutorial:

![Update 4](/images/tutorials/linear-regression/7.jpg)

A classification problem, as you may guess, is where our labels \\(y\\) can only take a particular value, or we can say that \\(y\\) is a discrete dataset. For example, if we want to solve a spam mail detecting problem, obviously we will have only two labels which is either *spam* or *non-spam*. Another example, you are a magician who is trying to guess the suit of a randomly picked card, so you only have four choices among Hearts, Diamonds, Clubs and Spades, right? So we are now dealing with a different problem from the one we did before. Our graph will now look like this:

![Graph_1](/images/tutorials/logistic-regression/graph_1.png)

Okay, so I hope you know can see the difference between a regression problem and a classification problem. Let's see how we will do to deal with a classification problem. To make it easily for you to understand, it is better that we should now consider a two-class classification problem like above.

### Activation Function

You still remember how Machine Learning actually works? It is important for any Machine Learning algorithms to have a way to compute the Predictions from the feature data \\(X\\) which we called Activation Functions. In the case of Linear Regression, the activation function is just as simple as below:

$$
h_\theta(X) = \theta_0 + \theta_1X_1 + \theta_2X_2 + \dots + \theta_nX_n
$$

As you can see, the function above is suitable for regression problems, as it doesn't apply any restriction onto the output. Obviously, this function won't work well with our classification problem. But we can also see that, Logistic Regression is somehow similar to Linear Regression (that is why there is *Regression* in its name), so we may be able to solve the Logistic Regression if we somehow find a way to restrict the output value of the function above.

One simple way we can think about is, to use a threshold value. The idea is like below:

$$
h_\theta(X^{(i)}) = \cases{ 1 & \text{if } h_\theta(X^{(i)}) \ge 0.5 \cr 0 & \text{if } h_\theta(X^{(i)}) \lt 0.5}
$$

And we will obtain a graph like this:

![Graph_2](/images/tutorials/logistic-regression/graph_2.png)

Seems OK, huh? At least we can ensure that the activation function now only outputs \\(0\\) or \\(1\\). But in fact, using a threshold directly on regression's activation function is not a good idea at all. The reason is, now we have a sharp change in our graph, which means that the value of \\(y\\) will change immediately in an unpredictable way, which results in a bad Model in the end.

So now we know what to do next. We need an activation function which not only restricts the output value but also contains no sharp change. That shouldn't be a big problem, in fact, we have quite a lot of functions which can satisfy both conditions. And the one which is mostly used is **Sigmoid** function, which has the form as below:

$$
g(z)=\frac{1}{1+e^{-z}}
$$

And the graph of sigmoid function looks like this:

![Graph_3](/images/tutorials/logistic-regression/graph_3.png)

Perfect, right? That is exactly what we need. So how are we supposed to apply this to our case. It's very simple, we just do like below:

$$
z = \theta^TX = \theta_0 + \theta_1X_1 + \theta_2X_2 + \dots + \theta_nX_n
$$  

$$
h_\theta(X) = g(z) = \frac{1}{1+e^{-z}} = \frac{1}{1+e^{-\theta^TX}}
$$

Next, I want to talk a little bit about the output of the function about, \\(h_\theta(X)\\). \\(h_\theta(X)\\) is interpreted as the probability that \\(y=1\\) on input \\(X\\), which can be expressed in mathematical terms like this:

$$
h_\theta(X) = P(y=1|x;\theta)
$$

And obviously, since we always have:

$$
P(y=1|x;\theta)+P(y=0|x;\theta)=1
$$

So we can also rewrite the probability that \\(y=0\\) like this:

$$
1 - h_\theta(X) = P(y=0|x;\theta)
$$

So we have done with sigmoid function, the function which we chose as our Activation Function. To recall a little, sigmoid function is a great choice here because it can satisfy both conditions: restricting the output's values and ensuring there is no sharp changes in graph.

### Cost function
After choosing the activation function, let's move to our next target: the Cost Function. As you may remember, the cost function evaluate our Model performance based on the difference between its Predictions and the actual Labels. In the case of Linear Regression, our cost function looks like this:

$$
J(\theta)=\frac{1}{2m}\sum_{i=1}^m(h_\theta(X^{(i)})-y^{(i)})^2
$$

Can we use the same cost function in Logistic Regression? The answer is: definitely **NO**. You got the right to ask me why. Well, in the learning process, what the computer tries to do is to minimize the cost function. Therefore, our cost function must be some kind of convex functions so that we can find the minimum by using Gradient Descent. In the case of Logistic Regression, if we use the same cost function like above, we will end up with a non-convex function. And for sure, the computer has no way to find the minimum.

So we are likely to find a new form of cost function which can both evaluate our Model's performance and tends to converge to some minimum. I don't want to talk deeper into how they found the appropriate cost function for Logistic Regression because it requires a lot of mathematical explanations. To make it as easily to understand as possible, you can see that our activation function contains an exponential element \\(e^{-z}\\), and one way to linearize that kind of function is to use logarithm. That is why the cost function for Logistic Regression was defined like below, and called the log-likelyhood cost function or the cross-entropy cost function:

$$
J(\theta)=-\frac{1}{m}\sum_{i=1}^m[y^{(i)}\log(h_\theta(X^{(i)})) + (1 - y^{(i)})\log(1 - h_\theta(X^{(i)}))]
$$

Let's talk a little bit about the cost function above. First, note that now we divide the sum by \\(\frac{1}{m}\\), because our new cost function is no longer a quadratic function. And don't forget the **minus** sign, either! It's very easy to explain why there is minus sign there. The logarithm of a number whose value is from \\(0\\) to \\(1\\) is a minus number, so adding a minus sign will make sure our cost function will always greater than or equal to \\(0\\).

Next, you can see that our new defined cost function has two seperate part: \\(y^{(i)}\log(h_\theta(X^{(i)}))\\) and \\((1 - y^{(i)})\log(1 - h_\theta(X^{(i)}))\\). Since the Label \\(y\\) can only be \\(0\\) or \\(1\\), so one of the two terms above will be \\(0\\). So we have a cost function which can cover both two cases: \\(y=0\\) and \\(y=1\\). Furthermore, our new cost function can also accumulate the output errors in each case properly, as explained above.

### Gradient Descent

So I have just talked about the cost function used in Logistic Regression problems. After we have a cost function, we will compute Gradien Descent. Do you still remember what Gradien Descent is? We need to compute Gradient Descent in order to update the parameter \\(\theta\\) (After assuring our cost function is convex, we need a way to go downhill, right?). So, let's compute Gradient Descent. Our new cost function seems very complicate this time, which you may think that it would take a day to compute all its partial derivatives. Don't worry, things are not that bad. In fact, computing the log-likelihood cost function's partial derivatives is very easy, all you have to do is using the *chain rule* which I mentioned before in earlier post. Writing it our here will make this post long and boring, so I leave it for you, lol. Here, I just want to show you the result. And it may make you surprised. Yeah, it looks just like what we had with Linear Regression:

* For weights (\\( \theta_1, \ldots, \theta_n\\))

$$\frac{\partial}{\partial \theta_j}J(\theta) = \frac{1}{m}\sum_{i=1}^m(h_\theta^{(i)}(x^{(i)})-y^{(i)}).x_j^{(i)}$$

* For bias (\\( \theta_0 \\))

$$\frac{\partial}{\partial \theta_0}J(\theta) = \frac{1}{m}\sum_{i=1}^m(h_\theta^{(i)}(x^{(i)})-y^{(i)})$$

As I mentioned above, you can compute the partial derivatives yourselves (I highly recommend you to do so, though). And with a little patience, I'm quite sure that you will have the same result.

So now you know everything you need to know about Logistic Regression: the sigmoid function, the log-likelihood cost function and its gradient descent. Note that not only Linear Regression and Logistic Regreesion, knowing these three terms also help you understand and use any other Machine Learning algorithms as well (even those complicated algorithms such as Neural Network!). 

### Summary

So today, we have talked about Logistic Regression. We talked about the difference between a regression problem and a classification problem. We talked about the activation function, the cost function used in Logistic Regression and how to compute its gradient descent as well. In the next post, I will continue with **Regularization**, another very important technique that you must know to deal with Overfitting problem, as you will use that technique nearly in every Machine Learning problem you may face in the future! So stay updated, and I will be back with you soon!

