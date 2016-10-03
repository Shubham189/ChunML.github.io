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
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$

### Cost Function


### Gradient Descent


### Parameter Update
