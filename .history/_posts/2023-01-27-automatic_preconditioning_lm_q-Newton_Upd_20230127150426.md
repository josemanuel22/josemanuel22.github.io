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

- The gradient of $$f$$ will be, $$\nabla f(x) = Ax - b$$. Minimizing the previous convex problem is equivalent to solve $$Ax = b$$.

- $$-\nabla f$$ is a vector pointing the direction of steepest descent. We start with a initial guess $$x_0$$ and we compute $$-\nabla f(x_{0})$$, then we move in that direction by a step size $$\alpha$$.

- Find the best $$\alpha$$, this $$\alpha$$ brings us to the minimum of $$f$$ constrainted to move in the direction $$d_{0}=-\nabla f(x_{0})$$.

- Computing $$\alpha$$ is equivalent to minimizing the function $$g(\alpha) = f(x_{0}+ \alpha d_{0})$$. Minimum of this function occurs when $$g'(\alpha)=0$$. So we get that  $$\alpha$$ is,
\begin{equation}
\alpha = - \dfrac{d_{i}^{T}(Ax_{x_{i}} + b)}{d_{i}^{T}Ad_{i}}
\edn{equation}
