---
title: "Machine Learning Part 3: Linear Regression"
categories:
  - Tutorial
tags:
  - machine-learning
  - linear-regression
  - cost-function
  - gradient-descent
---
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
Here we are again, in the third post of Machine Learning's tutorials. Today I'm gonna tell you about Linear Regression, the most common and understandable learning algorithm. This time I will dig more deeper so that after this post, you will know what actually happened during the learning process. So no more Dogs and Cats today, but algebraic stuff. Yeah, we're gonna work with matrices, from now on. But don't worry, it's not gonna be so hard today.
As I told you before, we got some training data containing Features and Labels. Features are somewhat distinct which can be used to distinguish between things.

![Image_1](/images/tutorials/what-is-machine-learning/5.jpg)

Remember this? To recall a little bit, I called 'X' Features, 'y' Labels, and 'a' Prediction. It may get your attention here, but it's just a naming convention, which X is always in uppercase, and y is lowercase.

So after collecting a great deal of training data (X, y), we have them learned by the computer. Then we show the data which the computer has never seen before, which contains only X this time, and the computer will give us a prediction, called 'a'.

I just helped you to recall about what Machine Learning is. But I think it would be better if you have a further look about Machine Learning on my first post here: [Whate  is Machine Learning?](https://chunml.github.io/ChunML.github.io/tutorial/Machine-Learning-Definition/)

So from the image above, the first thing coming to our minds is, how the computer can compute *y* from *X* during the learning process, and how it can compute prediction *a* from *X*?

Well, we will continue from what we were doing on the first post. The answer to the question above is: we need an learning algorithm. And in order to make an algorithm work, we need something called Activation Function.

### Activation Function

![Image_1](/images/tutorials/what-is-machine-learning/9.jpg)

Here's where we left off in the first post. The reason why I mentioned it to you because you will face the term Activation Function not only in Linear Regression, or Logistic Regression in later post, but also in the more complicated algorithms which you will learn in the future. So, what is Activation Function? That's a function which takes *X* as variable, and we use it to compute the prediction *a*.

In case of Linear Regression, the Activation Function is so simple that it's not considered an Activation Function at all!

$$
\begin{align*}
  h_\theta(X^{(i)})=\theta_0+\sum_{j=1}^m\theta_jX_j^{(i)}=\theta_0+\theta_1X_1^{(i)}+\theta_2X_2^{(i)}+\cdots+\theta_nX_n^{(i)}
\end{align*}
$$

I'll explain the equation above. First, the superscript and the subscript on each *X*, what do they mean? Imagine we have a training dataset which has 10 examples, each example has 4 features, so the superscript will indicate the *ith* example, and the subscript will indicate the *jth* feature. You will be used to this convention soon, so don't worry if you can't get that right now.

For the sake of simplicity, let's consider an example, where we have 10 examples, each example only contains one feature. So the Activation Function will look like this:

$$
\begin{align*}
  h_\theta(X^{(i)})=\theta_0+\theta_1X_1^{(i)}
\end{align*}
$$

Does it look similar to you? Yeah, that's exactly a linear equation with one variable which you learned a lot at high school. If we plot it on the coordinate plane, we will obtain a straight line. That's the idea of Linear Regression.

Imagine our training data look like this:

| X       | y           |
| ------------- |-------------| 
| 1      | 5 | 
| 2      | 7 |
| 3      | 9 |
| 4      | 11 |
| 5      | 13 |
| 6      | 15 |
| 7      | 17 |
| 8      | 19 |
| 9      | 21 |
| 10      | 23 |

If we plot them on the coordinate plane, we will obtain something like this:

Image_1

So, our mission now, is to find an appropriate function which can best fit those points. In case of Linear Regression with one variable, because the activation function is actually a straight line, so we will have to find a straight line which can almost go through all those points, intuitively.

But, how do we start? Well, we will start by randomizing all the parameters, which means \\( \theta_0,\theta_1 \\). So let's set them both one. Now we can compute *a* by activation function: \\(a=1+x\\). Now if we plot *X*, *y*, and the straight line \\(a=1+x\\), we will have something like this:

Image_2

Obviously, the straight line we obtain from \\(a=1+x\\) doesn't fit our training data well. But that's OK because we just began by randomizing the parameters, and no learning was actually performed. So here comes the next question: how can we improve the activation function so that it can fit the data better? Or I can say it differently: how can we make the computer learn to fit the data? The answer is: we will compute something called Cost Function.

### Cost Function


### Gradient Descent


### Parameter Update
