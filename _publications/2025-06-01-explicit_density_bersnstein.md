---
title: "Explicit Density Approximation for Neural Implicit Samplers Using a Bernstein-Based Convex Divergence"
collection: publications
category: conferences
permalink: /publication/2025-06-05-bernstein-convex-divergence
excerpt: 'Dual-ISL turns a rank-based discrepancy into a convex objective over model densities and yields an explicit Bernstein-polynomial density approximation for neural implicit samplers.'
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
keywords:
  - dual-ISL
  - explicit density approximation
  - neural implicit samplers
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

## Topics

dual-ISL · explicit density approximation · neural implicit samplers · Bernstein polynomials · convex divergence · likelihood-free learning · sliced divergences · density-ratio approximation

## Abstract

The canonical abstract and conference record are available on [OpenReview](https://openreview.net/forum?id=CyQG7D7FwT) and the [AISTATS Spotlight page](https://virtual.aistats.org/virtual/2026/spotlight/13918).
