---
title: From Bayesian inference to modern machine learning
subtitle: How Bayesian inference is hiding in your non-Bayesian models
date: 2021-04-06T16:00:00.000Z
summary: A tour from prescriptive Bayesianism to modern statistical machine learning.
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

> *Epistemic status: I am willing to be quoted on this.*

I really like the above figure, taken from Andrew Wilson's and Pavel Izmailov's insightful paper [Bayesian Deep Learning and a Probabilistic Perspective of Generalization (2020)](https://arxiv.org/abs/2002.08791). It conceptually shows the importance of choosing a model's inductive biases for doing inference in modern imaging tasks: choose the range of observations your model can explain too narrowly and you might miss the 'true' model, choose it too widely and your network needs too much data to learn (in the best case). Let's look at this inductive bias more closely.

(The paper itself primarily discusses the advantages of Bayesian marginalisation in modern neural networks - which is not our current topic - and well worth a read for all who have an interest in Bayesian deep learning.)

 ### The objective Bayesian prescription
In the [previous post](https://www.tbbakker.nl/post/bayes_commentary/) we discussed how objective Bayesian inference prescribes specifying a specific prior distribution $p(\mathcal{H}|\mathcal{I})$ over all (possible) hypotheses $\mathcal{H}$ given your prior information $\mathcal{I}$. This prior defines an inductive bias on the inference problem, and all that remains is to observe data $\mathcal{D}$, compute the likelihood $p(\mathcal{D}|\mathcal{H}, \mathcal{I})$ for all hypotheses $\mathcal{H}$ (typically specified by $\mathcal{H}$ itself), and finally use Bayes' theorem to obtain the posterior distribution $p(\mathcal{H}|\mathcal{D}, \mathcal{I})$, which represents the unique correct description of your current state of information about the world. 

We already noted how staggeringly impossible this is to do exactly, and thus any kind of Bayesian inference done in practice involves approximations. The common modern machine learning recipe - of specifying a parameterised model class, some prior (or no prior!) over these parameters, and using data and some learning rule to update these parameters so that they minimise some risk function - is precisely such an approximation. Here we will see how.

 ### Approximations we all agree are Bayesian
 Let's start slowly: we adhere to the general Bayesian idea that we need some kind of posterior distribution to describe our state of knowledge of some process, but we make some approximations in how we compute this. Two popular methods are Markov Chain Monte Carlo and Variational Inference.
