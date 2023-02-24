---
layout: post
title: Automatic Preconditioning by Limited Memory Quasi-Newton Updating
date:   2023-01-27
description: Summary and main concepts of the paper
tags: optimization, numerical-methods, gradient-descent, preconditioning
categories: sample-posts
---

## Conjugate Gradient (CG)

- Suppose we have some quadratic function,
\begin{equation}
f(x) = \frac{1}{2}x^{T}Ax-b^{T}x+c,
\end{equation}
for $$x\in \mathbb{R}^{n}$$ with $$A\in\mathbb{R}^{n\times n}$$ and $$b,c\in \mathbb{R}^{n}$$.

- The gradient of $$f$$ is, $$\nabla f(x) = Ax - b$$. Minimizing the previous convex problem is equivalent to solve $$Ax = b$$.