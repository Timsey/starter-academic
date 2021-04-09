---
title: From Bayesian inference to modern machine learning
subtitle: How Bayesian inference is hiding in your non-Bayesian models
date: 2021-04-06T16:00:00.000Z
summary: A tour from prescriptive Bayesianism to modern statistical machine learning.
draft: false
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
  caption: Image by xkcd
  alt_text: Image by xkcd
---

> *Epistemic status: I'm not an expert on many of the machine learning methods mentioned, and the discussion is primarily conceptual. Expect some abuse of notation. Also, I use the word true a lot, which here means something along the lines of 'corresponding to actual states of the universe'.*

In the [previous post](https://www.tbbakker.nl/post/bayes_commentary/) we discussed how objective Bayesian inference prescribes using Bayes' theorem to learn about the world: $p(\mathcal{H}|\mathcal{D}, \mathcal{I}) = \frac{p(\mathcal{H}|\mathcal{I}) p(\mathcal{D}|\mathcal{H}, \mathcal{I})}{p(\mathcal{D}|\mathcal{I})}$.

This first requires specifying a specific prior distribution $p(\mathcal{H}|\mathcal{I})$ over all (possible) hypotheses $\mathcal{H}$ given your prior information $\mathcal{I}$. This prior defines an inductive bias on the inference problem, and all that remains is to observe data $\mathcal{D}$, compute the likelihood $p(\mathcal{D}|\mathcal{H}, \mathcal{I})$ for all hypotheses $\mathcal{H}$ (typically specified by $\mathcal{H}$ itself), and finally use Bayes' theorem to obtain the posterior distribution $p(\mathcal{H}|\mathcal{D}, \mathcal{I})$, which represents the unique correct description of your current state of information about the world. 

We already noted how staggeringly impossible this is to do exactly, and thus any kind of Bayesian inference done in practice involves approximations. The common modern machine learning recipe - of specifying a parameterised model class, some prior (or no prior!) over these parameters, and using data and some learning rule to update these parameters so that they minimise some risk function - is precisely such an approximation. Here we will see how.

 ### Approximations everyone generally agrees are Bayesian enough
Let's start slowly: we adhere to the general Bayesian idea that we need some kind of posterior distribution to describe our state of knowledge of some process, but we make some approximations in how we compute this. 

#### Exact inference
The simplest case is the 'exact inference' setting, where we can actually compute the evidence term $p(\mathcal{D}|\mathcal{I}) = \int p(\mathcal{H}|\mathcal{I}) p(\mathcal{D}|\mathcal{H}, \mathcal{I}) d\mathcal{H}$ exactly. This might for instance be the case when we're talking about computing a posterior $p(\mu, \sigma|\mathcal{D}, \mathcal{I})$ for the mean $\mu$ and standard deviation $\sigma$ of a Normal sampling distribution / likelihood function given some data. If we use a [conjugate prior](https://en.wikipedia.org/wiki/Conjugate_prior) for $\mu, \sigma$, then the posterior can be exactly computed, so we've done exact inference! Right?

Well, note that we just introduced the Normal sampling distribution / likelihood out of the blue. If we were proper Bayesians, we would instead have considered a distribution over possible hypotheses $\mathcal{H}$ consistent with our initial information $\mathcal{I}$, and noted that these hypotheses immediately define their corresponding likelihood $p(\mathcal{D}|\mathcal{H}, \mathcal{I})$: that's what an hypothesis is! It tells us what kind of data we expect to see. In the above example, we've decided to only care about hypotheses that expect our observations to be Normally distributed around some $(\mu, \sigma)$ - different for each hypothesis. What if reality is more complicated? Then we will not discover this, because we haven't included those options in our hypothesis class.[^1] This is a very strong approximation.

In the language of inductive biases, we've biased our inference to only caring about explanations that are described by a Normal posterior. We will find the best explanation of our observations within this class, but we will not find the true explanation if our hypothesis class does not contain it. 

<!-- Note that $\mu, \sigma$ take the role of $\mathcal{H}$ here: in other words, we've restricted our hypothesis space from 'all hypotheses about the world consistent with our prior information $\mathcal{I}$' to 'all hypotheses about $\mu, \sigma$ consistent with our prior information $\mathcal{I}$'. We've essentially made the decision that we'll only focus on the $\mu, \sigma$ inference problem for now: if we later decide that we care about other parts of the world as well, we'll have to make sure to use the observed data $\mathcal{D}$ to update our knowledge of those parts as well. -->

<!-- Looking back at Bayes' theorem, we see that the recipe doesn't change if we change the hypotheses that $\mathcal{H}$ can represent, so we're in principle allowed to restrict the hypothesis space in this way if we only want to describe our state of knowledge about $\mu, \sigma$. This is the setting of most machine learning problems: we focus on one particular setting at a time, ignoring everything we deem unimportant for the problem at hand. -->

Now let's have a look at the chosen prior $p(\mu, \sigma| \mathcal{I})$. We used conjugate priors so that we are able to evaluate the evidence, but this is mostly a convenient mathematical trick: to what degree does such a prior actually describe what our current information $\mathcal{I}$ tells us about $\mu, \sigma$? The conjugate prior for a Normal distribution is another Normal: when is this a good prior?

A full answer would take us on a trip down the rabbit hole of constructing objective prior distributions, which is one of the hard problems mentioned in the previous post. One interesting result, though, is that the Normal prior can be motivated through the [principle of maximum entropy](https://en.wikipedia.org/wiki/Principle_of_maximum_entropy) as the prior that uniquely encodes [knowledge of the first and second moment of a parameter, and no other information](https://sgfin.github.io/2017/03/16/Deriving-probability-distributions-using-the-Principle-of-Maximum-Entropy/). So, if we already have some vague idea of the magnitude of $\mu, \sigma$ and of how far we might be off, then the Normal prior is a pretty good choice: not ideal, but a fairly good description of $\mathcal{I}$.

The 'exact' inference setting we looked at here is an insightful one to consider first, since its approximations - using a constrained hypothesis class and choosing a prior that might not fully reflect all known information - come up in (as far as I know) all practical inference methods. Let's continue by looking at some non-exact methods.

#### Non-exact inference
Two methods used in modern day Bayesian deep learning are [Markov Chain Monte Carlo (MCMC)](https://www.youtube.com/watch?v=1MRY6Ruu6RU) and [Variational Inference (VI)](https://ermongroup.github.io/cs228-notes/inference/variational/). They typically involve more complex hypotheses than those used in exact inference, which means the evidence term cannot be exactly evaluated. Both of these methods try to solve the intractability of the evidence term by introducing an approximation. The below is a brief discussion on the types of approximations these methods make to the prescription of Bayesian inference: see the links for a starting point on a more thorough explanation of the methods.

MCMC tries to generate samples from the posterior by setting up a Markov Chain whose stationary distribution is the posterior.  The set-up avoids having to evaluate the evidence, since the chain can be constructed using the ratio of the posterior at any two points, which means the evidence term cancels.

So what are the approximations? First of all, there are the same hypothesis space and prior approximations we saw in the exact inference case: we typically consider a restricted set of hypotheses, and our choice of prior might not reflect our information exactly. Secondly, the chain generates samples of the posterior. Even if the sampling is from the exact posterior specified, any finite number of samples is not going to be an exact match for that posterior. Thirdly, samples might not be exactly from the posterior specified due to convergence issues with the chain: most improvements to vanilla MCMC methods focus on tackling this problem, as far as I can tell.

VI essentially turns the original inference problem in to an optimisation problem. It tries to approximate the posterior by varying the parameters of another distribution until it fits the posterior adequately. Typically the approximating distribution is chosen from a relatively simple family of distributions, to simplify the procedure. The actual optimisation is typically performed on a lower bound of the evidence term, which has the effect of squeezing the approximate distribution closer to the specified posterior. 

Beyond the two standard approximations of practical Bayesian inference, VI introduces an approximation on the specified posterior, which is then fitted by optimising an approximate objective: two more approximations!

It's quite difficult to characterise the effect of the MCMC and VI approximations on the inductive bias of the inference process.[^2] Their hypotheses classes are typically less restrictive than those used in exact inference, but their convergence dynamics play a large role in the kind of inferences that pop out.[^3] 

Although MCMC and VI introduce quite some approximations, they are two of a relatively rare class of methods that attempt to obtain something that looks like a Bayesian posterior.[^4] Most modern machine learning methods don't do this, so let's see how we can obtain them from the Bayesian prescription.

### Through decision theory to maximum likelihood

In the previous post, we saw that by [Cox's](https://en.wikipedia.org/wiki/Cox%27s_theorem) [theorem](http://www.stats.org.uk/cox-theorems/VanHorn2003.pdf)  our state of knowledge of the world can be described by a probability distribution over all possible hypotheses consistent with our available information. We can then learn from observations through Bayes' theorem, and fundamentally that's all there is to inference: as we said, *all the rest is commentary*.

So how do we get the most common modern day machine learning practice - training some model to maximise its log likelihood - from this prescription? The answer lies in decision theory. 

Note that maximising a likelihood function just returns a single parameter value: the parameter setting that best explains the observed data according to that likelihood function. This is a far cry from the full posterior distribution that we need to describe all our information, and here we have a hint of what happened: we've thrown away information! 

By describing our state of knowledge now with a single parameter value plus some pre-specified model, we have chosen a particular summary of our full state of information. Which summary we choose is a decision we make - they all throw away some information, but different summaries throw away different information - and the maximum likelihood solution corresponds to one such summary.

Can we describe this formally? Yes! We are trying to summarise our posterior distribution $p(\mathcal{H}|\mathcal{D}, \mathcal{I})$ using some single statistic $S$. Any summary will lose some information, and we can define a decision loss function $L(S, \mathcal{H})$ that tells us how much we care about certain information versus other information contained in the full posterior. In other words, this loss function tells us how bad it is to use a particular statistic $S$ in the case that $\mathcal{H}$ is the true hypothesis, and it does this for all hypotheses we're considering. There is some abuse of notation here, so let's say this another way: given some summary statistic $S$, we check for each possible hypothesis $\mathcal{H}$ how bad it would be if we made a decision based on $S$ if $\mathcal{H}$ were true (here each $S$ directly corresponds to a decision). 

As an example, let's say we're considering hypotheses on the probability of earthquakes within the next ten years. Instead of using our full posterior to describe this, we choose to use the mostly likely hypothesis $\mathcal{H}_\text{max}$ as our summary statistic $S$. If $\mathcal{H}_\text{max}$ is the true hypothesis then this is a good choice, since we'll be making decisions based on something true. If $\mathcal{H}_\text{max}$ is not true, then we're making decisions based on something false, and in particular we're throwing away almost all information contained in the posterior distribution that might tell us how wrong we are. In the context of earthquakes, we'd be basing our decisions purely on the (potential) summary 'the most likely earthquake in the next ten years will happen in Japan'. This loses very little information if our actual posterior says there is very low probability on hypotheses that there will be earthquakes somewhere else in the next ten years; otherwise, we've thrown away a lot.

So how bad do we expect such a decision to be? Well, our posterior exactly represents our belief over these various earthquake possibilities, so the expected badness can be computed as the expectation of the loss under our posterior distribution. We write $\mathbb{E}_{p(\mathcal{H}|\mathcal{D}, \, \mathcal{I})} L(S, \mathcal{H})$ for this expectation, and we want to minimise this expected loss over decisions, which here directly correspond to choices of statistics $S$. 

Following the example above, let's see what happens if we decide use a loss function that assigns loss 0 if $S = \mathcal{H}$ and 1 otherwise, writing this as $1 - \delta(S, \mathcal{H})$, where $\delta(.)$ is the delta function.[^5] Intuitively, this loss function cares about exactly choosing the correct hypothesis; and if we're wrong, then we don't care how wrong we are. This is all we need to get to the maximum likelihood formalism:

{{< figure src="bayes_to_ml.png" id="bayestoml" >}}

[Derivation: from Bayes to MAP and MLE](#figure-bayestoml)

Here we have renamed $\mathcal{H}$ to $\theta$ to make the correspondence with typical Maximum A Posteriori estimation (MAP) and Maximium Likelihood Estimation (MLE) clearer. Typically when we write $\theta$ we are referring to the parameters of some model, and in principle $\mathcal{H}$ is more general than this, but in the case that we are working within some predefined model class - a linear model, a neural network - the correspondence is exact.

The upshot: the common MLE recipe of machine learning is exactly Bayesian inference with a (constant) uniform prior, where we have chosen to only care about the most likely hypothesis / parameter value, with no other care as to how wrong we might be. 


[^1]: Machine learning textbooks typically distinguish between the model class and the parameters of the model. In our example, the Normal distribution assumption would be a model, and the various $\mu, \sigma$ values would be considered parameters of that model. This is a type of hierarchy in what I've chosen to just call hypotheses here: any model plus specific parameter setting defines an hypothesis, and in principle we could just as easily do Bayesian inference on that space directly. In practice, the hierarchy can simplify the procedure, but adding the extra level - in my opinion - hides the elegance of the formalism. 

[^2]: For those interested: we can say that vanilla VI tends to posterior mode-seeking behaviour due to the use of the KL-divergence in its objective, and that this goes some way toward [explaining its poor performance when compared to deep ensemble methods](https://arxiv.org/pdf/2002.08791.pdf).

[^3]: This is typical of non-exact methods, especially those that involve optimisation (such as VI): what matters is not just the hypotheses that can in principle be described by the model, but also to what degree the choice of optimisation objective and optimiser introduces preferences for certain types of hypotheses over others. At the risk of speculating, this problem is intuitively only exacerbated by the highly non-convex loss surfaces found in modern Bayesian neural networks.

[^4]: Another such method is the Gaussian Process, which - for the purposes of this blog post - is kind of like the exact inference setting, but now - as far as I can tell - entirely restricted to Normal distributions for likelihood and prior. A Gaussian Process computes a posterior directly on functions, rather than parameters. This can be nice, as it is sometimes easier to translate available information to priors over what functions should look like, rather than what values certain parameters should take.

[^5]: This corresponds to the $L_0$ loss on $S$ and $\mathcal{H}$, which leads to choosing the posterior mode as the summary statistic $S$: i.e. MAP estimation. Alternative choices may be the $L_1$ loss, which corresponds to choosing the posterior median, and the $L_2$ loss, which corresponds to choosing the posterior mean as the statistic.
