---
layout: post
title: Automatic Preconditioning by Limited Memory Quasi-Newton Updating
date:   2023-01-27
description: Summary and main concepts of the paper
tags: optimization, numerical-methods, gradient-descent, preconditioning
categories: sample-posts
header-includes:
  - \usepackage{algorithm2e}
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

- So we find a new direction $$d_1$$ to move that is conjugate (w.r. $$A$$) to the previous one $$d_0$$. So $$d_{1} = -\nabla f(x_1) + \beta_{0}d_{0}$$. We can derive $$\beta_{0}$$ from conjugacy, $$d_{1}^{T}Ad_{0}=0$$.
\begin{equation}
\beta_{0}= \frac{\nabla f(x_{1})^{T}Ad_{0}}{d_{0}^{T}Ad_{0}}
\end{equation}
Iterating this process will keep giving us new conjugate directions.

## Preconditioned conjugate gradient method

- The convergence analysis shows that convergence speed is fast when the condition number of $$A$$ is close to $$1$$. We can accelerate the convergence rate by replacing the system $$Ax=b$$ by the preconditioned system,
\begin{equation}
M^{-1}Ax = M^{-1}b.
\end{equation}

- The symmetric positive definite matrix $$M$$ must be chosen s.t. the new system is solved with less computational work than the original one. That means that $$M^{-1}A$$ has a more 'favourable' conditional number than $$A$$.

## Hessian-Free Newton Method

We now have all the prerequisite background to understand the Hessian-free optimization method. The general idea behind the algorithm is as follows:
{% highlight c++ linenos %}
    i=0, x[i]=x[0] be our initial guess;
    while(Stoping test not satisfied)
        At x[n] compute gradient of f(x[n]) and H(f)(x[n]) and consider taylor expansion of f:
        f(x+ Δx) ≈ f(x) + ∇f(x)ᵀ Δ x + Δxᵀ H(f) Δx.
        \State Compute x[n+1]  with C.G. for quadratic functions on the Taylor expansion.

{% endhighlight %}

## Automatic Preconditioning by limited Memory Quasi-Newton Updating

- We wish to accelerate the C.G. iteration used in Hessian-free Newton methods for nonlinear optimization. We want to solve the following problem,

\begin{equation}
A_{k}x = b_{k},\quad k=1,...,t,
\end{equation}

where $$A_{k}$$ is the Hessian of the objective function at the current iterate. $$A_{k}$$ vary slowly, and $$b_{k}$$ are arbitrary. 

- Also interested in solving finite element problems, so a sequence of linear systems,
\begin{equation}
Ax = b_{i}, \quad i=1, ..., t.
\end{equation}
Both cases the coefficient matrices are symmetric and positive define.

- We deal with the large scale unconstrained optimization problem,
\begin{equation}
\min{f(x)},
\end{equation}
where $$f$$ is a $$C^{2}$$ of $$n$$ variables.

- Among the iterative methods for large scale unconstrained optimization,
when the Hessian matrix is possibly dense, limited memory quasi-Newton
methods are often the methods of choice.

- They generate a sequence $${x_k}$$, according to the following scheme:
\begin{equation}
x_{k+1} = x_{k} + \alpha p_{k}, \quad k = 0, ...
\end{equation}
with $$p_{k} = -H_{k}\nabla f(x)$$, where $$H_{k}$$ is an approximation of the inverse of the Hessian matrix and $$\alpha_k$$ is a steplength.

- Instead of computing $$H_{k}$$ at each iteration $$k$$, these methods update  $$H_{k}$$ in a simple manner, in order to obtain the new approximation $$H_{k+1}$$ to be used in the next iteration.

- Moreover, instead of storing full dense $$n \times n$$ approximations, they only save a few vectors of length
$$n$$, which allow to represent the approximations implicitly.

- L-BFGS method is usually considered very efficient. Well suited for large scale problems because
the amount of storage is limited and controlled by the user. 

- This method is based on the construction of the approximation of the inverse of the Hessian matrix, by exploiting curvature information gained only from the most recent iterations.

- So we have the following algorithm:

{% highlight c++ linenos %}
    Solve (x[1], r[1]) <- A[1]x = b[1] with unpreconditioned CG-method;
    for(i=2, ..., k) {
        Compute/store: s[i]=x[i+1]-x[i],  y[i] =r[i+1]-r[i],  i = l[1], ..., l[m];
        Define BFGS matrix H[k] using (s[i], y[i]); (quasi-Newton preconditioner)
        (x[i], r[i]) <- Use H[k] preconditioned CG-method to solve A[i]x = b[i];
{% endhighlight %}

