---
title: "Preparing AWS's instance to run Machine Learning's projects"
categories:
  - Project
tags:
  - machine-learning
  - AWS
  - AMI
  - project
---

Hello there, it's been a while since my previous Real time Object Recognition project. I currently have some cool stuff ongoing and I'll share it to you when it's ready (it won't be long).

At the moment, I'm struggling with a frustrating performing problem. As I told you before in the previous [Project](https://chunml.github.io/ChunML.github.io/project/Real-Time-Object-Recognition-part-one/), the training process requires a powerful desktop which you have to spend a lot of money on, and may take a lot of time and resources. But this headache can be solved with a pre-trained model, like the one I used. And luckily, because using that model for recognizing object is not a big deal (as it took approximately 1.5 ~ 2 seconds per image on my PC), I still somehow felt satisfied.

But life is not that easy. Things get tougher as you keep moving on. Now instead of 2 seconds, I have to wait for minutes for each image to be 100% processed, which is simply unacceptable! Of course, I can just throw $2000 on Amazon for a giant desktop with everything set up, rather than complaining to you on my blog (which may be boring you, I'm sorry). Yeah, I wish I had that money, dude!

No way am I stopping. There must be some way out, I supposed. And I finally found it, Amazon Web Service (AWS).

You can simply think of AWS as a place which offers desktop for rent. Of course, it costs! But it won't cost you as much as buying a powerful giant desktop. Moreover, they even offer 12-month free trial! What a deal! It means you won't have to pay a penny for a thousand-dollar desktop in one year. You know, you are free to have our own choices. But I choose AWS, for now.

And this post is for ones who consider to use AWS for running their own Machine Learning projects, just like me. Setting things up in AWS won't be hard, but takes some time.

Firstly, you have to register for AWS. You can do it by access to [AWS Home Page](https://aws.amazon.com/), then choose "Sign In to the Console", you will be redirected to the page like this:

![Register page](/images/projects/prepare-aws-instance/register.jpg)

After the registration completes, go back to AWS Home Page and sign in with your registered account. Here's what you will see:

![User page](/images/projects/prepare-aws-instance/userpage.jpg)

On the top right, make sure you're choosing N. California region. If it is somewhere else, change it to N. California.

We will use EC2 instance, so choose EC2 (the first one in Compute category). You will see the following page showing up:

![EC2](/images/projects/prepare-aws-instance/ec2.jpg)

Click "Launch Instance". Here's where we will create our new instance, or you can also choose to use pre-configured one. You may wonder why. A new created instance is just like a new computer, with just OS installed. If you want to work with Python, you have to install Python, if you want to work with Caffe, you have to install and configure Caffe. Sounds challenging, right? In my case, although I got a few experiences working with environment configuration on my own PC, I don't feel like doing it all over again, especially on a computer belonging to someone else. So I choose to use the pre-configured one! And I recommend you to do so.

On the next page after clicking "Launch Instance", choose "Community Instance" on the left, and type "cs231n" to the search bar. That's the instance configured by Stanford University, which have Caffe, Torch, Theano, Keras, Lasagne installed, which means it's already up and ready.

![cs231n](/images/projects/prepare-aws-instance/cs231n.jpg)

Click "Select", on the next screen, scroll down to "g2.2xlarge" type. Select it and click "Review and Launch". We are working on Machine Learning projects, which requires a great deal of parallel computing. And a GPU Instance's type will be the best fit for that.

![g22xlarge](/images/projects/prepare-aws-instance/g22xlarge.jpg)

Simply click "Launch" on the next screen. At this step, AWS will require a key-pair authentication. Because this is the first time you launch, just select "Create a new key pair", and type whatever you want to name that key. And click "Launch Instances".

![keypair](/images/projects/prepare-aws-instance/keypair.jpg)

You should then receive a .pem file which holds your key-pair information. Keep it safe because there's no way to get it back once you lose it!

At this point, you may receive an error, telling you that your account in under verification.

![launch_failed](/images/projects/prepare-aws-instance/launch_failed.jpg)

Just give it about 2 hours and try to launch again. Here's what you will see after your account is verified:
 
![launched](/images/projects/prepare-aws-instance/launched.jpg) 

That's it. Let's log in our instance and make sure everything works properly.
