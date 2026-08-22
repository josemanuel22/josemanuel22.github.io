---
title: "Robust training of implicit generative models for multivariate and heavy-tailed distributions with an invariant statistical loss"
collection: publications
category: manuscripts
permalink: /publication/2026-03-10-jmlr
excerpt: 'A sample-based generative modeling framework that characterizes ISL as a proper divergence and extends it to heavy-tailed data with Pareto-ISL and high-dimensional data with random-projection ISL-slicing.'
date: 2026-03-10
publication_year: 2026
venue: 'Journal of Machine Learning Research, 27(122):1–49'
authors:
  - 'José Manuel de Frutos'
  - 'Manuel A. Vázquez'
  - 'Pablo M. Olmos'
  - 'Joaquín Míguez'
paperurl: 'https://www.jmlr.org/papers/volume27/25-1660/25-1660.pdf'
arxiv: '2410.22381'
codeurl: 'https://github.com/josemanuel22/isl-implicit-generative-models'
keywords:
  - invariant statistical loss
  - implicit generative models
  - heavy-tailed distributions
  - Pareto-ISL
  - sliced divergences
  - random projections
  - mode collapse
  - generative modeling
citation: 'José Manuel de Frutos, Manuel A. Vázquez, Pablo M. Olmos, and Joaquín Míguez. (2026). &quot;Robust training of implicit generative models for multivariate and heavy-tailed distributions with an invariant statistical loss.&quot; <i>Journal of Machine Learning Research</i>, 27(122):1–49.'
---

**Authors:** José Manuel de Frutos, Manuel A. Vázquez, Pablo M. Olmos, Joaquín Míguez  
**Journal:** Journal of Machine Learning Research, 27(122):1–49, 2026  
**Links:** [JMLR](https://jmlr.org/papers/v27/25-1660.html) · [PDF](https://www.jmlr.org/papers/volume27/25-1660/25-1660.pdf) · [arXiv](https://arxiv.org/abs/2410.22381) · [Code](https://github.com/josemanuel22/isl-implicit-generative-models)

## Overview

This work develops the theory and practical scope of the **Invariant Statistical Loss (ISL)** for implicit generative modeling. We characterize ISL as a proper divergence over continuous distributions and establish regularity properties that support stable, gradient-based optimization without adversarial training.

We then introduce two extensions. **Pareto-ISL** uses generalized Pareto latent noise to improve modeling of heavy-tailed and extreme events. **ISL-slicing** uses random one-dimensional projections to scale the rank-based loss to multivariate and high-dimensional distributions. The resulting objective can be used as a standalone training criterion or as a pretraining objective before adversarial fine-tuning.

## Topics

invariant statistical loss · implicit generative models · heavy tails · Pareto-ISL · sliced divergences · random projections · mode collapse · generative modeling

## Abstract

The canonical abstract and bibliographic record are available on the [JMLR paper page](https://jmlr.org/papers/v27/25-1660.html).
