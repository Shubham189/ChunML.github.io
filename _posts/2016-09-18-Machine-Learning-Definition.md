---
title: "ML Tutorial: What is Machine Learning?"
categories:
  - Tutorial
tags:
  - machine-learning
  - model
  - feature
  - learning
---

{% include base_path %}

You've been hearing about machine learning in the last few years, especially on the day on which AlphaGo was hotter than Donald Trump. You felt excited, you wanted to know what it is, or even more, you wanted to dig into it. But you just still can't get it? Let me help you this time. 

### So, the very big question, and maybe the biggest reason which led you here: What exactly is Machine Learning?

Well, I've got no intention to repeat something that was already written on Wikipedia (you're tired of it, right?). So my definition of Machine Learning is: we don't teach the computers to work anymore, we teach them how to learn, to do things itself!

Still confused? Let's see something cool instead.

<img src="{{ "1.jpg" | prepend: "/images/" | prepend: base_path }}">

So as you can see in the picture, we have a model (the big one in the middle), an input which takes care of something call (Feature, Label) and an output which gives us something call Activation. So what the hell are all these things?

Let's imagine you want the computer to do you a favor: to tell you whether there is a dog in an image. So it becomes much clearer when I match up everything like the image below:

Images_2

Firstly, what is Features?
If this is the first time you hear it, then congratulations, you will see this keyword everywhere, everywhen from now on (as long as you keep up with Machine Learning, of course). So let's make it simple. Look at the dog. He has four legs (like the other dogs on Earth), his nose is black, he is hanging out his tongue, he has a tail, ... Yeah, those are what come up when you see this dog, and importantly, you will see those in other dogs too. So it turns out to be some distinct features
which make human's brain know it just saw a dog. Wait a minute, did I just say Features? Well, I hope you get the point here. So, Features are something distinct that make something different than the others. Human's brain recognises something by their Features, so why don't we teach the computer that trick? (Come on, don't be that selfish man)

I know you're excited now. Ready to move on? So what about Label? Well, it's much simpler than the Feature. Label is a name of guys who have specific features. So we call guy who have four legs, one black nose, one long tongue and one long tail a DOG. Well, I just can't make it simpler. So what about the other guys? At this time, I just call them "Not a dog". Maybe you will ask me why I don't make it more specific, just like "a Cat", "a Bird" or something. You will have the answer at
the end of this post. So please stay patient :) There is a lot of fun ahead, I promise.
