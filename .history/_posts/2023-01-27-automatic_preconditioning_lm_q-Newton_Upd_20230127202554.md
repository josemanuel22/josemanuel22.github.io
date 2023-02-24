---
layout: post
title: Automatic Preconditioning by Limited Memory Quasi-Newton Updating
date:   2023-01-27
description: Summary and main concepts of the paper
tags: optimization, numerical-methods, gradient-descent, preconditioning
categories: sample-posts
---

## Conjugate Gradient (CG)

Suppose we have some quadratic function,
\begin{equation}
f(x) = \frac{1}{2}x^{T}Ax-b^{T}x+c,
\end{equation}
for $$x\in \mathbb{R}^{n}$$ with $$A\in\mathbb{R}^{n\times n}$$ and $$b,c\in \mathbb{R}^{n}$$.

- The gradient of $$f$$ will be, $$\nabla f(x) = Ax - b$$. Minimizing the previous convex problem is equivalent to solve $$Ax = b$$.

- $$-\nabla f$$ is the vector pointing the direction of steepest descent. We start with a initial guess $$x_0$$ and we compute $$-\nabla f(x_{0})$$, then we move in that direction by a step size $$\alpha$$.

- We are interested in finding the best $$\alpha$$. This is, we are want to find the $$\alpha$$ such that it brings us to the minimum of $$f$$ constrainted to the direction $$d_{0}=-\nabla f(x_{0})$$.

- Computing $$\alpha$$ is equivalent to minimizing the function $$g(\alpha) = f(x_{0}+ \alpha d_{0})$$. The minimum of this function occurs when $$g'(\alpha)=0$$. So we get that $$\alpha$$ is,
\begin{equation}
\alpha = - \dfrac{d_{i}^{T}(Ax_{x_{i}} + b)}{d_{i}^{T}Ad_{i}}.
\end{equation}

- The second point in our iterative algorithm will be, $$x_{1}  = x_{0} - \alpha \nabla f(x_{0})$$.

- So we find a new direction $$d_1$$ to move in that is conjugate (w.r. $A$) to the previous one $$d_0$$. So $$d_{1} = -\nabla f(x_1) + \beta_{0}d_{0}$$. We can derive $$\beta_{0}$$ from conjugacy, $$d_{1}^{T}Ad_{0}=0$$.
\begin{equation}
\beta_{0}= \frac{\nabla f(x_{1})^{T}Ad_{0}}{d_{0}^{T}Ad_{0}}
\end{equation}
Iterating this process will keep giving us new conjugate directions.

## Preconditioned conjugate gradient method