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

![Image_1](/images/tutorials/what-is-machine-learning/9.jpg)

