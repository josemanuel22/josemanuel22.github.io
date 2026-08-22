---
title: "Beyond GANs: Rank-Based and Discriminator-Free Training of Implicit Generative Models"
date: 2026-08-22
description: "How rank statistics, discriminator-free objectives, convex divergences, and sample-based f-divergence estimation connect to GAN training, mode collapse, and implicit generative models."
tags:
 - Generative-modeling
 - GANs
 - Implicit-generative-models
 - Rank-statistics
 - F-divergences
 - Machine-learning
---
Generative adversarial networks (GANs) are one of the most influential ways to train **implicit generative models**: models that can generate samples but do not necessarily provide a tractable likelihood. Their central idea is elegant. A generator learns to produce samples while a discriminator learns to distinguish generated data from real data.

This adversarial formulation has been enormously successful, but it also introduces a difficult optimization problem. Training becomes a coupled min-max game, and practical issues such as instability, sensitivity to hyperparameters, **mode collapse**, and mode dropping are well known.

A large part of my recent research asks a related question:

> **Can we train and compare implicit generative models directly from samples, without relying exclusively on an adversarial discriminator?**

The answer we have been exploring is based on **rank statistics**. Instead of learning a discriminator that separates real and generated observations, we use the relative ordering of samples to build statistical discrepancies between distributions. This viewpoint has led to several related methods: the Invariant Statistical Loss (ISL), its multivariate and heavy-tailed extensions, dual-ISL, and rank-statistic approximations of *f*-divergences.

This post gives a high-level view of how these ideas fit together and how they relate to GANs, adversarial training, and divergence-based generative modeling.

## GANs, implicit generative models, and the training problem

Suppose a generator transforms a latent random variable \(Z\) into a sample

$$
X = G_\theta(Z).
$$

The model distribution is therefore available through simulation: draw \(Z\), pass it through \(G_\theta\), and obtain samples from the generated distribution. What may be unavailable is a closed-form density for \(X\).

GANs solve this problem by introducing another neural network, the discriminator, and learning through an adversarial objective. In broad terms, the discriminator estimates how real and generated data differ, while the generator tries to eliminate that difference.

There are many powerful variants of this idea: **f-GANs**, Wasserstein GANs (WGANs), MMD-GANs, and many others. They differ in the discrepancy they optimize and in how that discrepancy is estimated.

Our work starts from another possibility: perhaps the discrepancy between real and generated distributions can sometimes be estimated **directly from ranks**, without first training a discriminator or explicitly estimating a density ratio.

## ISL: training an implicit generator without a discriminator

Our first step in this direction was the **Invariant Statistical Loss (ISL)**, introduced in:

**Training Implicit Generative Models via an Invariant Statistical Loss**  
AISTATS 2024 · [paper page](/publication/2024-05-01-aistats-1) · [PMLR](https://proceedings.mlr.press/v238/frutos24a.html) · [code](https://github.com/josemanuel22/ISL)

The basic intuition is simple. If two one-dimensional distributions agree, then rank statistics constructed from samples of the two distributions exhibit a characteristic uniform behavior. We can therefore transform the problem of matching two distributions into the problem of making an induced **rank distribution close to uniform**.

This gives a sample-based loss that can be differentiated through a smooth rank approximation and used to train a neural generator.

The important distinction from a GAN is that **there is no learned discriminator**. The generator receives a statistical training signal derived directly from the relative positions of real and generated samples.

Conceptually, this replaces

$$
\text{generator} \leftrightarrow \text{discriminator}
$$

with something closer to

$$
\text{generator} \rightarrow \text{rank-based statistical discrepancy}.
$$

The objective is therefore relevant to researchers looking for **discriminator-free alternatives to GAN training**, sample-based generative objectives, or non-adversarial methods for implicit generative models.

## From one dimension to high dimensions and heavy tails

A natural limitation of rank statistics is that ordering is straightforward in one dimension but not in \(\mathbb{R}^d\). Our later work develops two extensions that address broader generative settings:

**Robust training of implicit generative models for multivariate and heavy-tailed distributions with an invariant statistical loss**  
JMLR 2026 · [paper page](/publication/2026-03-10-jmlr) · [JMLR](https://jmlr.org/papers/v27/25-1660.html) · [code](https://github.com/josemanuel22/isl-implicit-generative-models)

The first extension is **ISL-slicing**. Instead of trying to define a global ordering in high dimension, we project the data onto many one-dimensional directions and compute rank-based discrepancies in those projections. This connects ISL to the broader family of sliced statistical distances.

The second extension is **Pareto-ISL**, motivated by heavy-tailed data and extreme events. Standard latent distributions such as Gaussians may make it difficult to represent sufficiently heavy tails. Pareto-ISL combines the statistical loss with generalized Pareto latent noise in order to better capture these regimes.

This paper also studies the relationship between ISL and adversarial optimization more directly. ISL can be used as a fully non-adversarial objective, but it can also serve as a **pretraining criterion before adversarial fine-tuning**. This creates a hybrid strategy: first move the generator toward the data distribution using a stable statistical objective, and only then introduce an adversarial discriminator if desired.

That perspective is particularly relevant to **GAN training stability** and **mode collapse**. The goal is not to claim that adversarial training should always be removed, but to provide an alternative training signal that does not depend on the discriminator-generator game.

## dual-ISL: a convex view and explicit density approximation

A second direction emerged by reversing the role of the distributions in the rank construction. This leads to **dual-ISL**:

**Explicit Density Approximation for Neural Implicit Samplers Using a Bernstein-Based Convex Divergence**  
AISTATS 2026 Spotlight · [paper page](/publication/2025-06-05-bernstein-convex-divergence) · [OpenReview](https://openreview.net/forum?id=CyQG7D7FwT) · [code](https://github.com/josemanuel22/dual-isl)

The resulting formulation has an important property: it can be interpreted as a **convex objective over the model density**. Even though the generator remains implicit and we train from samples, the rank-based construction reveals an explicit approximation to the underlying density ratio in a **Bernstein polynomial basis**.

This leads to an unusual combination:

- likelihood-free training of a neural implicit sampler,
- a convex divergence formulation,
- and an explicit truncated density approximation obtained from rank statistics.

From a GAN perspective, dual-ISL lives in the same broad setting—learning a generator from samples—but again avoids an adversarial discriminator. It is therefore relevant to searches around **GAN alternatives**, **stable likelihood-free generative training**, and **discriminator-free implicit models**.

## Rank statistics for *f*-divergences

The connection to classical GAN theory becomes even more direct when we move from a particular loss to general ***f*-divergences**.

In:

**Approximating *f*-Divergences with Rank Statistics**  
ICML 2026 · [paper page](/publication/2026-01-25-rank_f-div) · [arXiv](https://arxiv.org/abs/2601.22784) · [OpenReview](https://openreview.net/forum?id=6dI31vzkqT) · [code](https://github.com/josemanuel22/rsfdiv)

we show that rank histograms can be used to construct a family of approximations to *f*-divergences directly from samples, without explicit density-ratio estimation.

For a resolution parameter \(K\), the discrepancy between two distributions induces a rank histogram. Applying a discrete *f*-divergence to that histogram yields a rank-statistic divergence. As \(K\) increases, this provides increasingly fine information about the difference between the underlying distributions.

This matters for generative modeling because *f*-divergences are central to many statistical learning objectives, including **f-GAN-style formulations**. The rank-statistic construction provides a different route to estimating these discrepancies: rather than training a variational critic or estimating the density ratio directly, we work with sample ranks.

The framework also extends to high-dimensional data through random projections, producing **sliced rank-statistic *f*-divergences**.

This paper is not, by itself, a new GAN architecture. Its relevance to GANs is more general: it provides tools for **comparing real and generated distributions**, constructing divergence-based generative objectives, and estimating quantities closely connected to those used in f-GANs.

## A common thread: ranks instead of adversaries

The four papers can be viewed as different parts of the same program:

| Question | Rank-based approach |
| --- | --- |
| Can an implicit generator be trained without a discriminator? | **ISL** |
| Can this scale to multivariate or heavy-tailed distributions? | **ISL-slicing and Pareto-ISL** |
| Can the objective reveal an explicit density approximation? | **dual-ISL** |
| Can we estimate general *f*-divergences directly from samples? | **Rank-statistic *f*-divergences** |

The common idea is that **ranks carry distributional information while remaining accessible from samples**.

This makes rank-based methods attractive in settings where:

- the model density is unavailable or inconvenient to evaluate,
- one wants to avoid training an additional discriminator,
- adversarial optimization is unstable,
- mode collapse or mode dropping is a concern,
- the target distribution is heavy-tailed,
- or the goal is to estimate a divergence between two sample sets.

## Are these methods replacements for GANs?

Not necessarily.

GANs remain extremely flexible and powerful, especially in high-dimensional perceptual domains. The point of this line of work is not that every GAN should be replaced by a rank-based objective.

A better way to view the methods is as **alternative statistical tools for the same underlying problem**: learning or comparing implicit distributions when we mainly have access to samples.

Depending on the application, the rank-based objective can be:

- the complete training criterion,
- a pretraining loss before adversarial fine-tuning,
- an auxiliary discrepancy,
- or simply an estimator used to compare real and generated distributions.

That flexibility is, for me, one of the most interesting aspects of the framework.

## Papers and code

The sequence of papers is:

1. **Training Implicit Generative Models via an Invariant Statistical Loss** — AISTATS 2024  
   [PMLR](https://proceedings.mlr.press/v238/frutos24a.html) · [project page](/publication/2024-05-01-aistats-1) · [code](https://github.com/josemanuel22/ISL)

2. **Robust training of implicit generative models for multivariate and heavy-tailed distributions with an invariant statistical loss** — JMLR 2026  
   [JMLR](https://jmlr.org/papers/v27/25-1660.html) · [project page](/publication/2026-03-10-jmlr) · [code](https://github.com/josemanuel22/isl-implicit-generative-models)

3. **Explicit Density Approximation for Neural Implicit Samplers Using a Bernstein-Based Convex Divergence** — AISTATS 2026 Spotlight  
   [OpenReview](https://openreview.net/forum?id=CyQG7D7FwT) · [project page](/publication/2025-06-05-bernstein-convex-divergence) · [code](https://github.com/josemanuel22/dual-isl)

4. **Approximating *f*-Divergences with Rank Statistics** — ICML 2026  
   [arXiv](https://arxiv.org/abs/2601.22784) · [project page](/publication/2026-01-25-rank_f-div) · [code](https://github.com/josemanuel22/rsfdiv)

Taken together, these works explore a simple question from several angles: **how much of generative modeling can be done by comparing samples statistically, rather than learning the comparison through an adversarial discriminator?**
