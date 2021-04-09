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
