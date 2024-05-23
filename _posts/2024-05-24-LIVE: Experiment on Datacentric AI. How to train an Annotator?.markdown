---
title: "How to train an Annotatoer"
layout: post
date: 2024-05-24 01:22
headerImage: false
tag:
- markdown
- elements
projects: true
star: true
category: project
author: Albert Tatjer, Elisa Nguyen
description: 
---

If you see this, the experiment is live and you can take part! following the link [https://annotation-imagenet.netlify.app/](https://annotation-imagenet.netlify.app/)

### What is all the buzz about?
Collecting datasets is not an easy task. The first and most obvious question one can ask is: "What should we collect?". Another, less obvious but fascinating is: "How is the data collected?" Briefly, there are two main approaches browsing and tagging, you can research the details. Sticking with data collected via browsing interfaces, such as ImageNet, the final dataset results of pairs of sample directory, and the class it was selected for.

But... Is there any other interesting data that we could benefit from? in Han et al.[^fn] propose to record  the mouse time series when hovering the sample. With this one can extract the exact pixel that was clicked by the annotator when selecting the sample, and the time spent hovering the sample. They claim that it is "free" to annotate such data, and that it yields a direct accuracy boost with minimal modification.

We ask: _To Be Revealed_ after the experiment is closed down.

### You can read more when the experiment is finished!

[^fn]: Neglected Free Lunch: https://arxiv.org/abs/2303.17595