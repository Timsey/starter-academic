---
title: Priors and generalisation
subtitle: Implicit priors in deep learning methods
date: 2021-04-06T16:00:00.000Z
summary: A look at the role of priors in deep learning methods.
draft: true
featured: true

authors:
  - admin
tags:
  - Bayesian
categories: []
projects: []

image:
  filename: featured.jpg
  focal_point: Smart
  preview_only: false
  caption: Image by Andrew Wilson and Pavel Izmailov
  alt_text: Image by Andrew Wilson and Pavel Izmailov
---

> *Epistemic status:*  
  
I really like the above figure, taken from Andrew Wilson's and Pavel Izmailov's insightful paper [Bayesian Deep Learning and a Probabilistic Perspective of Generalization (2020)](https://arxiv.org/abs/2002.08791). It conceptually shows the importance of choosing a model's inductive biases for doing inference in modern imaging tasks: choose the range of observations your model can explain too narrowly and you might miss the 'true' model, choose it too widely and your network needs too much data to learn (in the best case). Let's look at this inductive bias more closely.  
  
(The paper itself primarily discusses the advantages of Bayesian marginalisation in modern neural networks - which is not our current topic - and well worth a read for all who have an interest in Bayesian deep learning.)

### Inductive biases

In previous posts we discussed the Bayesian prescription for inference. In this prescription, the prior $p(\mathcal{H}|\mathcal{I})$ over the hypothesis space $\mathcal{H}$ of all hypotheses consistent with your available information $\mathcal{I}$ is the only place inductive biases enter. These hypotheses each directly define a likelihood function $p(\mathcal{D}|\mathcal{H}, \mathcal{I})$ over observations $\mathcal{D}$, and Bayes' theorem tells us how to then compute the posterior $p(\mathcal{H}|\mathcal{D}, \mathcal{I})$ that uniquely describes our state of information about the universe.

Constrast this to modern machine learning practice, where we often don't talk about priors at all. And yet, we speak of our models as still containing various inductive biases. We say a standard Convolutional Neural Network (CNN) has better inductive biases for image data than a Fully-connected Neural Network (FNN), even when we're training these models through Maximum Likelihood Estimation (MLE), with no explicit sign of Bayes or priors anywhere. 

What's happening here, is that we are in fact using prior information - in the Bayesian sense - when training these models. It's just that we're now so far from the Bayesian prescription that it has become hard to notice. Let's explore this.

### Model classes, architectures, and optimisers

- Model class / architecture is a hard prior (weight tying, CNN vs FNN)
- This choice is informed by actual prior information: 'images have translation equivariance, and so do CNNs: use CNNs'.
- In this case, the prior is easier to specify in architecture space (= model class!) than weight space
- Optimisation complicates the picture further: additional inductive biases are induced through learning (non-convexity): still counts as prior though. Does this imply a discrete number of hypotheses possible using this learning system?
