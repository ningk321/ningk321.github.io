---
title: "CCLM: CLass-Conditional Label Noise Modelling"
layout: post
date: 2023-06-25 23:59
headerImage: false
tag:
- markdown
- elements
projects: true
star: true
category: project
author: Albert Tatjer, Bhalaji Nagarajan, Ricardo Marques, Petia Radeva
description: 
---

Published @[IbPRIA](http://www.ibpria.org/2023/) and awarded the __Best Paper Award__. [Here](https://link.springer.com/chapter/10.1007/978-3-031-36616-1_1) for the complete paper.

### Why?
Learning with Noisy Labels (LNL) is concerned with training models when the data sample, label pairs are potentially noisy. In a future where this problem is solved, one could leverage search engines, low-fidelity tagging systems like social networks... to create gigantic datasets and actually learn from them.

### How?
The current training pipline in LNL is to model the sample label noise, and then according to what is the resulting probability of a sample being noisy, the dataset is split into the _hopefully_ mostly clean set and the _hopefully_ mostly noisy set. Afterwards, a flavour of semi-supervised learning is used to take advantage of the data available.

### So...?
Our paper focuses on the Label Noise Modelling step. It is known that there is a simplicity bias[^fn] in Deep Learning, and often believed that it is one of the key reasons that makes it work so well. In label noise modelling, we try to take advantage of it. The model is trained conventionally for some epochs (~10 for CIFAR-10), called the **warm-up** phase. Afterwards, we hope that the model has learned a "meaningful representation" but it hasn't memorized the noise in the data, it is known that networks learn easier patterns first, and then more complex ones (similar to what is going on in the .gif). Finally, with the warmed-up network, it is typically assumed that all the loss of all the samples follow a bi-modal normal distribution. Thus, in the **modelling** phase, we fit a 2-mode Gaussian Mixture Model to extract the two sub-pupulations. The idea behind it is that the sub-population with higher loss is going to have the noisy samples (the network hasn't had time to learn the complex noise yet), and the sub-pupulation with lower loss is going to be mostly clean. Then with a hyperparameter threshold, we split the data according to these probabilities, and follow along with semi-supervised learning. This process is repeated at every epoch. The following image illustrates the sample loss distribution. We can see that the core assumption we made is reasonable.


<figure>
    <img src="/assets/images/loss_evolution.gif"
         alt="Classification boundary evolution gif">
    <figcaption>Evolution of the classification boundary over training epochs. From extracted from https://cs.stanford.edu/people/karpathy/convnetjs/demo/classify2d.html.</figcaption>
</figure>

<figure>
    <img src="/assets/images/per_sample_all.png"
         alt="Sample loss all">
    <figcaption>The sample loss distribution after warm-up for all the sample in CIFAR-100. The typical assumption seems to hold.</figcaption>
</figure>


### Our proposal
We realize that there are some classes that are harder to learn than others. How would that affect the loss as an indicator of sample cleanliness? Our proposal is to change the assumption that _all the samples follow a bi-modal normal distribution_ with _all the samples of a class follow a bi-modal normal distribution, which can be different for every class_. You might be scratching your head now, what does "class" mean?? In this context, a class is a group of samples with the same (potentially noisy) label. The two following pictures help showcase how the proposed assumption is less constraining and more realistic.

### Results
In the paper we show how our extremely simple proposal improves classification accuracy, and other interesting metrics such as classiness, defined as the standard deviation of the accuracy over the classes.


<figure>
    <img src="/assets/images/per_sample_otter.png"
         alt="Sample loss otter">
    <figcaption>The sample loss distribution for the samples labelled "otter" after warm-up. The typical assumption seems to hold.</figcaption>
</figure>

<figure>
    <img src="/assets/images/per_sample_road.png"
         alt="Sample loss road">
    <figcaption>The sample loss distribution for the samples labelled "road" after warm-up. The typical assumption seems to hold.</figcaption>
</figure>


[^fn]: https://arxiv.org/abs/2006.07710