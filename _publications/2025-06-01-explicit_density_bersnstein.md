---
title: "Explicit Density Approximation for Neural Implicit Samplers Using a Bernstein-Based Convex Divergence"
collection: publications
category: conferences
permalink: /publication/2025-06-05-bernstein-convex-divergence
excerpt: 'Dual-ISL provides a convex, likelihood-free and discriminator-free objective for neural implicit samplers, offering a stable alternative to adversarial GAN-style training.'
date: 2026-02-03
publication_year: 2026
venue: '29th International Conference on Artificial Intelligence and Statistics (AISTATS) — Spotlight'
authors:
  - 'José Manuel de Frutos'
  - 'Pablo M. Olmos'
  - 'Manuel A. Vázquez'
  - 'Joaquín Míguez'
paperurl: 'https://arxiv.org/pdf/2506.04700'
arxiv: '2506.04700'
openreview: 'https://openreview.net/forum?id=CyQG7D7FwT'
codeurl: 'https://github.com/josemanuel22/dual-isl'
bibtex: true
keywords:
  - dual-ISL
  - explicit density approximation
  - neural implicit samplers
  - implicit generative models
  - generative adversarial networks
  - GANs
  - GAN training
  - adversarial training
  - GAN alternatives
  - discriminator-free generative modeling
  - mode collapse
  - training stability
  - Bernstein polynomials
  - convex divergence
  - density ratio approximation
  - likelihood-free learning
  - sliced divergences
citation: 'José Manuel de Frutos, Pablo M. Olmos, Manuel A. Vázquez, and Joaquín Míguez. (2026). &quot;Explicit Density Approximation for Neural Implicit Samplers Using a Bernstein-Based Convex Divergence.&quot; <i>AISTATS 2026</i>, Spotlight.'
---

**Authors:** José Manuel de Frutos, Pablo M. Olmos, Manuel A. Vázquez, Joaquín Míguez  
**Venue:** AISTATS 2026 · Spotlight  
**Links:** [AISTATS Spotlight](https://virtual.aistats.org/virtual/2026/spotlight/13918) · [OpenReview](https://openreview.net/forum?id=CyQG7D7FwT) · [arXiv](https://arxiv.org/abs/2506.04700) · [PDF](https://arxiv.org/pdf/2506.04700) · [Code](https://github.com/josemanuel22/dual-isl)

## Overview

We introduce **dual-ISL**, a rank-based objective obtained by reversing the roles of the target and model distributions in ISL. This formulation is convex in the model density and provides a likelihood-free route to training neural implicit samplers while retaining strong regularity properties.

A key result is an **explicit density approximation**: the rank-based discrepancy admits an interpretation as an approximation of the density ratio in a Bernstein polynomial basis. This leads to closed-form truncated density estimates, convergence guarantees, and a natural sliced extension for multivariate data.

## Relation to GANs and adversarial generative modeling

GANs and many other implicit generative models are trained through adversarial objectives because the model density is unavailable. **Dual-ISL addresses the same likelihood-free setting without requiring an adversarial discriminator.** Its convex formulation offers a different route to training neural implicit samplers and is therefore relevant to researchers looking for **GAN alternatives**, **discriminator-free generative modeling**, or more stable objectives for sample-based generators.

The explicit density approximation also provides additional interpretability compared with standard GAN training: the method yields a tractable Bernstein-polynomial approximation linked to the model/target density ratio, while retaining a sample-based training procedure.

## Topics

dual-ISL · neural implicit samplers · implicit generative models · generative adversarial networks (GANs) · GAN training · adversarial training · GAN alternatives · discriminator-free generative modeling · mode collapse · training stability · explicit density approximation · Bernstein polynomials · convex divergence · likelihood-free learning · sliced divergences · density-ratio approximation

## Abstract

The canonical abstract and conference record are available on [OpenReview](https://openreview.net/forum?id=CyQG7D7FwT) and the [AISTATS Spotlight page](https://virtual.aistats.org/virtual/2026/spotlight/13918).

## BibTeX

```bibtex
@inproceedings{defrutos2026explicit,
  title={Explicit Density Approximation for Neural Implicit Samplers Using a Bernstein-Based Convex Divergence},
  author={de Frutos, Jos\'e Manuel and Olmos, Pablo M. and V\'azquez, Manuel A. and M\'iguez, Joaqu\'in},
  booktitle={Proceedings of the 29th International Conference on Artificial Intelligence and Statistics},
  year={2026},
  note={Spotlight}
}
```
