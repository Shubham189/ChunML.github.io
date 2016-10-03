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
| 1      | 7 | 
| 2      | 8 |
| 3      | 7 |
| 4      | 13 |
| 5      | 16 |
| 6      | 15 |
| 7      | 19 |
| 8      | 23 |
| 9      | 18 |
| 10      | 21 |

If we plot them on the coordinate plane, we will obtain something like this:

![Training_data](/images/tutorials/linear-regression/1.jpg)

So, our mission now, is to find an appropriate function which can best fit those points. In case of Linear Regression with one variable, because the activation function is actually a straight line, so we will have to find a straight line which can almost go through all those points, intuitively.

But, how do we start? Well, we will start by randomizing all the parameters, which means \\( \theta_0,\theta_1 \\). So let's set them both to *1*. Now we can compute *a* by activation function: \\(a=1+x\\). Now if we plot *X*, *y*, and the straight line \\(a=1+x\\), we will have something like this:

![Randomized_function](/images/tutorials/linear-regression/2.jpg)

Obviously, the straight line we obtain from \\(a=1+x\\) doesn't fit our training data well. But that's OK because we just began by randomizing the parameters, and no learning was actually performed. So here comes the next question: how can we improve the activation function so that it can fit the data better? Or I can say it differently: how can we make the computer learn to fit the data? 

Obviously, we must think of some way to evaluate how well the current function is performing. One way to accomplish this task is to compute Cost Function, which takes the difference between the Label and the prediction as its variable. And among many types of Cost Function, I will introduce to you the Mean Squared Error Function, which is the most appropriate approach for Linear Regression, and yet maybe the simplest one for you to understand.

### Mean Squared Error Function

Firstly, let's see what Mean Squared Error Function (MSE) looks like:

$$
\begin{align*}
  J(\theta)=\frac{1}{2m}\sum_{i=1}^m(h_\theta(X^{(i)})-y^{(i)})^2=\frac{1}{2m}\sum_{i=1}^m(a^{(i)}-y^{(i)})^2
\end{align*}
$$

Now everything has just become clear. It computes the mean value of the squared errors, which are the differences between the  Prediction \\( h_theta(X^{(i)}) \\) and the Label \\( y^{(i)} \\). You can see that if the value of \\( J(\theta) \\) is large, it means that the difference between the Prediction and the Label is also large, which causes the straight line can not fit the training data well. In contrast, if the value of \\( J(\theta) \\) is close to zero, it means that the Prediction and the Label lie very closely in the coordinate plane, which we can tell that the straight line obtained from the activation function fits the training data pretty well.

Here you may have a question: why don't we just take mean value of the difference between Prediction and Label? Why must we use the squared value instead? Well, there's no "must" here. In this case the squared error works just fine, so it was chosen. There's no problem if we just use the difference instead. But let's consider this case. Imagine you have \\( a^{(1)}=2 \\), \\( y^{(1)}=4 \\) and \\( a^{(2)}=5 \\), \\( y^{(1)}=3 \\). What will happen in both cases?

No squared error:
$$J(\theta) = \frac{1}{2x2}((2-4)+(5-3)) = \frac{1}{2x2}(-2+2) = 0$$

With squared error:
$$J(\theta) = \frac{1}{2x2}((2-4)^2+(5-3)^2) = \frac{1}{2x2}(4+4) = 2$$

As you can see, the MSE will accumulate the error without caring the sign of the error, whereas the Mean Error is likely to omit the error like the example above. Of course, in another place, using the Mean Error instead of MSE will somehow make some sense, but that's beyond the scope of this post, so I'll talk about it when I have chance.

So, through MSE value, we can somehow evaluate how well the activation function is performing, or how well the straight line obtained by the same function is fitting our training data. Then what will we do in the next step? We'll come to a new concept called, Gradien Descent. Keep going, you're half way there!

### Gradient Descent


### Parameter Update
