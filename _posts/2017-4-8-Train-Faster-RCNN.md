---
title: "How To Prepare Data And Train Your Own Faster R-CNN Model"
header:
  teaser: projects/train-faster-rcnn/TBD.png
categories:
  - Project
tags:
  - machine-learning
  - deep-learning
  - caffe
  - faster r-cnn
  - faster rcnn
  - gpu
  - training
  - data preparation
  - object detection
---
<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
Hi guys! So I've been away for three months to do a project for my company, and unfortunately, in another prefecture. During that time, I received quite a lot of comments from you guys abou what I wrote before. Some said that my blog posts did help them a lot and told me to keep writing.
To be honest, I was really really happy to hear that. And as long as my blog can be helpful, I will continue to write more and more posts (hope that they will be useful, too).
Besides, I also received comments from you guys about the problems you came across while you were following my instructions. And I'm so sorry that I was so messed up with my work that I couldn't be any helpful during the past three months.

So, let's get down to business. Among those comments I received, some of you asked me about how to train a Faster R-CNN model, using your own dataset. Obviously, you wouldn't make most out of it if you just stick with the pre-trained model. So this post I'm gonna guide you through steps to train your own Faster R-CNN model.

Before we get started, make sure you have already set things up. It means that you have cloned from Faster R-CNN Github repository, compiled and successfully run the demo. Or, you probably want to take a look at my previous post, where I covered all the necessary steps I have just mentioned:

* [Compiling and Running Faster R-CNN on Ubuntu (CPU Mode)](https://chunml.github.io/ChunML.github.io/project/Running-Faster-RCNN-Ubuntu/){:target="_blank"}

In case you have a PC with GPU, which is strongly recommended... No, it's not just recommended. GPU is definitely a MUST if you want to train Faster R-CNN. And below is the link to setup Faster R-CNN with GPU and the problem I faced, which caused me unable to use cuDNN with Faster R-CNN:

* [Solving problem when running Faster R-CNN on GTX 1070](https://chunml.github.io/ChunML.github.io/project/Problem-Faster-RCNN-GPU/){:target="_blank"}

So now let's suppose you have successfully compiled and run the demo file. Next we will talk about how to make one step further: to train your own model.

### Train Faster R-CNN with PASCAL VOC 2007 dataset

One problem we may face when it comes to train Faster R-CNN is that the data preparation is somehow tiresome. So, it's a good idea to start training using the well-known PASCAL VOC datasets.
The first reason is, the PASCAL VOC datasets contain everything we need: the images and all associated annotations. The second reason is, PASCAL VOC datasets were officially used in Object Detection/Localization challenges to evaluate competitors' model, and of course, Faster R-CNN is among those, so the source code provided by its authors is, obviously enough, implemented to use PASCAL VOC dataset (version 2007) by default.
It means that using PASCAL VOC dataset, we can start to train the model without having to modify a single line of code! After make sure that the training code actually works, we can make further steps to train our own dataset.

