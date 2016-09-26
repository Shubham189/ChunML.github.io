---
title: "Real Time Object Recognition (Part 1)"
categories:
  - Project
tags:
  - machine-learning
  - VGG
  - object recognition
  - learning
---

Technology sometimes seems like magic, especially when we don't have any idea about how it was done, or we even think it can't be done at all.
When I was a kid, I was a huge fan of Sci-Fi Films, which were on every TV channel in the 1990s in my country. They did inspire me a lot, help grow up an "engineering mindset" in me.
Being an engineer sometimes makes me feel so great, because I can mostly understand many things that seem to be magical to other ones. But to be honest, there are still be lots of things out there can make me feel like a fool. Let me tell you one of them.

It was sometime in 2015, I watched a demo video from a startup company in Japan. It was about Object Recognition using Deep Learning. At that time, I didn't even have any idea about what Machine Learning is, not to mention Deep Learning! 
My thought then? "That was impossible. How did they do that?"
I kept questioning myself for a while. I just couldn't get it out of my mind. But unfortunately, because my first thought was "That was impossible", or at least "That was impossible to me", I gave it up, left the mystery unrevealed.
It was not until I paid serious attention to Machine Learning that I somehow made the mystery become clear. As I was working around with Convolutional Neural Network, then I suddenly thought of the mystery I gave up one year ago. I mean, that was really exciting and crazy. (Feels like Mission 6 accomplished to me, lol)

Seems like a pretty long beginning (I didn't mean to write a preface for my book or something, though). So I am here to share my work. In fact, it was not something impresssive (especially when comparing to outstanding projects out there). But I really hope this post can help, especially for ones who have enthusiasm in Machine Learning and once came accross something like me before.

In this project, I will try to reproduce the result I saw in the demo video one year ago. Concretely, I will move the camera around a table, with many objects put on it. The computer will try to recognize each object, and print the object's label in the output of the camera.

Writing it all in one post may hurt, so I separate this project into two parts like below:

* Part 1: Go through the folder containing the images, recognize object in each.
* Part 2: Real time object recognition through input from camera

So, let's get down to business.

Firstly, let's talk a little bit about how Machine Learning works. I had post about what Machine Learning exactly is, and how it exactly works here: [What is Machine Learning?](https://chunml.github.io/tutorial/Machine-Learning-Definition/).
The main part of any Machine Learning system, is the Model. It contains the algorithms and all the associated parameters. A good Model will produce a good prediction. Because of that, the training process (i.e. the process which produces the Model) can be heavily computational and take a lot of resources (you know, RAM and memories to store the parameters).
Fortunately, a great work from [François Chollet]({% https://github.com/fchollet %}) helps make this problem become much more relaxing than ever. I mean that you won't have to spend a great deal of money on a giant computer (with powerful CPU and GPUs), you won't have to spend time on training the data yourself. Because François Chollet provides us the pretrained Model on the most outstanding CNN architectures. Sounds cool, right? And I will use the VGG16 Model for this project.

(to be continued...)
