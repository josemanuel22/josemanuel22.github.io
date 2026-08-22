---
title: "Robust training of implicit generative models for multivariate and heavy-tailed distributions with an invariant statistical loss"
collection: publications
category: manuscripts
permalink: /publication/2026-03-10-jmlr
excerpt: 'A stable, discriminator-free alternative to adversarial GAN training for implicit generative models, extended to multivariate and heavy-tailed distributions with Pareto-ISL and ISL-slicing.'
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
bibtex: true
keywords:
  - invariant statistical loss
  - implicit generative models
  - generative adversarial networks
  - GANs
  - GAN training
  - adversarial training
  - GAN alternatives
  - discriminator-free generative modeling
  - mode collapse
  - training stability
  - heavy-tailed distributions
  - Pareto-ISL
  - sliced divergences
  - random projections
  - generative modeling
citation: 'José Manuel de Frutos, Manuel A. Vázquez, Pablo M. Olmos, and Joaquín Míguez. (2026). &quot;Robust training of implicit generative models for multivariate and heavy-tailed distributions with an invariant statistical loss.&quot; <i>Journal of Machine Learning Research</i>, 27(122):1–49.'
---

**Authors:** José Manuel de Frutos, Manuel A. Vázquez, Pablo M. Olmos, Joaquín Míguez  
**Journal:** Journal of Machine Learning Research, 27(122):1–49, 2026  
**Links:** [JMLR](https://jmlr.org/papers/v27/25-1660.html) · [PDF](https://www.jmlr.org/papers/volume27/25-1660/25-1660.pdf) · [arXiv](https://arxiv.org/abs/2410.22381) · [Code](https://github.com/josemanuel22/isl-implicit-generative-models)

## Overview

This work develops the theory and practical scope of the **Invariant Statistical Loss (ISL)** for implicit generative modeling. We characterize ISL as a proper divergence over continuous distributions and establish regularity properties that support stable, gradient-based optimization without adversarial training.

We then introduce two extensions. **Pareto-ISL** uses generalized Pareto latent noise to improve modeling of heavy-tailed and extreme events. **ISL-slicing** uses random one-dimensional projections to scale the rank-based loss to multivariate and high-dimensional distributions. The resulting objective can be used as a standalone training criterion or as a pretraining objective before adversarial fine-tuning.

## Relation to GANs, mode collapse, and training stability

**Generative adversarial networks (GANs)** are implicit generative models typically trained through an adversarial discriminator–generator game. This paper studies a different route: ISL trains the generator through a sample-based statistical objective and therefore does **not require a discriminator or adversarial min-max optimization**.

This connection is especially relevant for researchers searching for **stable GAN training**, **alternatives to GAN losses**, or methods to reduce **mode collapse / mode dropping**. ISL can be used as a fully non-adversarial training criterion, or as a stable pretraining objective before later adversarial fine-tuning. The multivariate and heavy-tailed extensions make the framework applicable beyond the low-dimensional settings in which discriminator-free objectives are often studied.

## Topics

invariant statistical loss · implicit generative models · generative adversarial networks (GANs) · GAN training · adversarial training · GAN alternatives · discriminator-free generative modeling · mode collapse · training stability · heavy tails · Pareto-ISL · sliced divergences · random projections · generative modeling

## Abstract

The canonical abstract and bibliographic record are available on the [JMLR paper page](https://jmlr.org/papers/v27/25-1660.html).

## BibTeX

```bibtex
@article{defrutos2026robust,
  title={Robust training of implicit generative models for multivariate and heavy-tailed distributions with an invariant statistical loss},
  author={de Frutos, Jos\'e Manuel and V\'azquez, Manuel A. and Olmos, Pablo M. and M\'iguez, Joaqu\'in},
  journal={Journal of Machine Learning Research},
  volume={27},
  number={122},
  pages={1--49},
  year={2026}
}
```
