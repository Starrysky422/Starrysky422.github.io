---
layout: post
title: Free Energy of Percolation and its Differentiability
comments: true
tags: 
- Probability Theory
- Percolation Theory
- Seminar Talk
---

This post is based on my talk in June 2023 at the Graduate Probability Reading Seminar in percolation and random-cluster model, supervised by [Prof. I. Seo](http://www.math.snu.ac.kr/~insuk.seo/). I covered the materials from chapter 4 of Grimmett's textbook [3]---about the free energy $\kappa$ of percolation on square lattices and its differentiability properties---with some additional remarks on historical background and recent progresses.


## Our Starting Point
Given a graph $G$ and probability $p\in [0,1]$, an **(edge) percolation** on $G=(V,E)$ is a random configuration $\omega: E\to \\{0,1\\}$ where $\omega(e) = 1$ with probability $p$ for each $e\in E$ in the independent manner. We say the edge $e$ is **open** if $\omega(e) = 1$, and **closed** otherwise. We write $\PP_p$ for the probability distribution of $\omega$, and $\EE_p$ for the corresponding expectation. Especially, we will mainly consider a percolation on the $d$-dimensional square lattice $G = \LL^d$, where $V(\LL^d) = \ZZ^d$ and $E(\LL^d) = \EE^d$.

<p align="center">
<embed src="/svg/free-energy-of-percolation-and-its-differentiability/image01.svg" type="image/svg+xml" />
</p>

The main concern of percolation theory is connectivity. For each vertex $x\in \ZZ^d$, denote the open cluster (a.k.a. the connected component w.r.t. $\omega$) containing $x$ by $C(x)$. In particular, we write $C = C(0)$. Note that the percolation on $\LL^d$ is translation invariant. Then, we can define some key quantities of percolation theory, the **percolation probability**
\\[
	\theta(p) = \PP_p[ \card{C} = \infty ]
\\]
and the **critical probability**
\\[
	p_c = p_c(\LL^d) = \sup\\{ p: \theta(p) = 0 \\}.
\\]
Also, we define the main figure of this post, the **number of open clusters per vertex**, or the **free energy**
\\[
	\kappa(p) = \EE_p\frac{1}{\card{C}}
	= \sum_{n=1}^\infty \frac{1}{n} \PP_p[\card{C} = n].
\\]
Note that $\kappa(0) = 1$, $\kappa(1) = 0$, and $\kappa$ is monotonically decreasing.

The free energy $\kappa$ is one of the principal characters of percolation theory. One reason is that $\kappa$ is endowed with strong differentiability properties which can be utilized for various arguments in percolation theory. We will look into these properties, and our main goal is to prove:
> $\kappa \in C^1(0,1)$.


## The 'Law of Large Numbers'
Before we move on, let us examine one possible justification of the name of $\kappa$, the 'number of open clusters per vertex.' While it is quite apparent from its definition, we can also validate it in the following way:
> Let $B(n) = [-n,n]^d$ be the box with side-length $2n$ centered at the origin, and denote the number of open clusters in $B(n)$ by $K_n$.
> 
> Then, 
> \\[\tag{1}
> 	\frac{1}{\card{B(n)}}K_n \to \kappa(p)
> \\]
> as $n\to \infty$, $\PP_p$-a.s. and in $L^1(\PP_p)$.

Since $L^1(\PP_p)$ convergence directly follows from $\PP_p$-a.s. convergence and the dominated convergence theorem, all we have to show is $\PP_p$-a.s. convergence.

The idea for its proof is quite simple. Let $C_n(x)$ be the open cluster in $B(n)$ containing $x$, then we have an easy identity
\\[
	K_n = \sum_{x\in B(n)} \frac{1}{\card{C_n(x)}}
\\]
as the contribution of vertices in an open cluster to the sum is exactly $1$ for each cluster. Noting that $\card{C(x)} = \card{C_n(x)}$ unless $x$ is connected to $\bd B(n)$, and such 'boundary effect' is negligible as $\card{\bd B(n)} \ll \card{B(n)}$, we may replace $\card{C_n(x)}$ in the above sum by $\card{C(x)}$. However, since $1/\card{C(x)}$ is bounded and stationary under translations of $\LL^d$, (we can convince ourselves that) with an aid of a suitable ergodic theorem, we have 
\\[
	\frac{1}{B(n)}\sum_{x\in B(n)} \frac{1}{\card{C(x)}} \to \EE_p\frac{1}{\card{C}} = \kappa(p)
\\]
as $n\to\infty$, $\PP_p$-a.s.

We can justify the above 'replacement' as follows. As $C_n(x)$ is always contained in $C(x)$, we have 
\\[
	\sum_{x\in B(n)}\frac{1}{\card{C(x)}} \le \sum_{x\in B(n)}\frac{1}{\card{C_n(x)}}.
\\]
For the other half, note that 
\\[
	\sum_{x\in B(n)}\frac{1}{\card{C_n(x)}} - \sum_{x\in B(n)}\frac{1}{\card{C(x)}} \le \sum_{x \lrarrow \bd B(n)}\frac{1}{\card{C_n(x)}},
\\]
and the right-hand side is exactly the number of open clusters in $B(n)$ incident with $\bd B(n)$, which is at most $\card{\bd B(n)} \ll \card{B(n)}$.


## Combinatorial Expression for $\kappa$
One way to deal with $\kappa$ is to represent it combinatorially. If $C$ is finite, then $C$ is a finite connected subgraph of $\LL^d$ containing $0$, which will be referred to as an **animal**. Let an animal $A \subseteq \LL^d$ with $n$ vertices be given. If $C = A$, then all edges of $A$ must be open, and all the other edges that are incident with $A$ must be closed. Hence,
\\[
	\PP_p[C = A] = p^m (1-p)^b
\\]
with $m = \card{E(A)}$ and $b = \card{\Delta(A)}$ where $\Delta(A)$ is the **edge boundary** of $A$, which is the set of edges not in $A$ incident with $A$.

<p align="center">
<embed src="/svg/free-energy-of-percolation-and-its-differentiability/image02.svg" type="image/svg+xml" />
</p>

Now, let $a_{nmb}$ be the number of animals $A$ with $n = \card{A}$, $m = \card{E(A)}$, and $b = \card{\Delta(A)}$. Then, we have 
\\[\tag{2}
	\PP_p[\card{C} = n] = \sum_{m,b} a_{nmb} p^m(1-p)^b
\\]
and
\\[\tag{3}
	\kappa(p) = \sum_{n,m,b} \frac{1}{n}a_{nmb} p^m(1-p)^b.
\\]
Since $a_{nmb}$ is a purely combinatorial quantity, we just have turned the matter of $\kappa$ into a graph-counting problem! This methodology can also be applied to other characters, such as $\theta(p)$ and the **mean (finite) cluster size** $\chi^f(p) = \EE_p[\card{C} \vert \card{C} < \infty]$.

The sum in $(2)$ is indeed a finite sum, as we have the following trivial bounds for $n,m,b$'s of an animal $A$:
\\[\tag{4}
	n-1 \le m \le dn
	\quad\text{and}\quad 
	2d \le b \le 2dn.
\\]
We can check each of the inequalities with simple reasoning. Thus, the probability $\PP_p[\card{C} = n]$ is actually a polynomial in $p$, so is smooth in $p$. However, $\kappa(p)$ is represented as an infinite series of polynomials in $p$. Hence, we may expect that the differentiability of $\kappa$ is closely related to the 'slow growth of $a_{nmb}$,' or, the decay of the tail probability $\PP_p[\card{C} \ge n]$. We will return to these simple bounds later in our arguments.


## Historical Remarks
The free energy $\kappa$ has several differentiability properties.

In the subcritical phase $[0,p_c)$, it is known that $\kappa$ is $C^\omega$. That is basically because the tail distribution $\PP_p[\card{C} \ge n]$ of cluster size exponentially decays in the subcritical phase. One can show the analyticity of $\kappa$ with a little bit of complex analysis, and the proof can be found in chapter 6 of [3].

On the other hand, in the supercritical regime $(p_c,1]$, as $\PP_p[n \le \card{C} < \infty]$ decays rapidly (but subexponentially), with some elementary analysis, we can show that $\kappa$ is $C^\infty$. The proof can be found in chapter 8 of [3]. It had been highly believed for a long time that $\kappa$ is also $C^\omega$ in the supercritical regime, while the $d=2$ case is relatively simple thanks to the planar duality. The analyticity of $\kappa$ was settled by a very recent result [2] by Georgakopoulos and Panagiotis in 2018.

Meanwhile, the behavior of $\kappa$ at the critical point $p_c$ is quite different. In 1964, Sykes and Essam [1] conjectured that $\kappa$ is twice differentiable but *not* thrice differentiable at $p = p_c$. This problem is remaining open, while it was proved that $\kappa$ is twice differentiable at $p = p_c$ in the $d=2$ case by Kesten [4] in 1981.

The character $\kappa$ plays a central role in many arguments in probability theory, and its first emergence can be found from the "proof" of $p_c(\LL^2) = 1/2$ by Sykes and Essam in 1964. The reasoning goes like this. By the planar duality, for $G = \LL^2$, one can show the identity 
\\[
	\kappa(p) = \kappa(1-p) + 1 - 2p
\\]
holds by Euler's formula combined with $(1)$. Hence, if the conjecture that $\kappa$ admits a unique singularity at $p = p_c$ is true, then it must be $1/2$ due to the symmetry of the equation around $1/2$. This gives vindication of the fact that $p_c(\LL^2) = 1/2$, but unfortunately, this argument has never been made rigorous, and all known proofs of $p_c(\LL^2) = 1/2$ use different methods.

As a further remark, we may consider a **site percolation** on a graph, that is, a percolation on the vertices instead of the edges, and define the analogous free energy $\kappa^{\operatorname{site}}$. In particular, if we consider the site percolation on the planar triangular lattice $\mathbb{T}$, then $\mathbb{T}$ is self-dual in the site percolation sense, so we obtain a similar identity
\\[
	\kappa_{\mathbb{T}}^{\operatorname{site}}(p) = \kappa_{\mathbb{T}}^{\operatorname{site}}(1-p) + p - 3p^2 + 2p^3.
\\]
Meanwhile, a work [5] by Zhang in 2003 shows that $\kappa_{\mathbb{T}}^{\operatorname{site}}$ is not thrice differentiable at $p = p_c^{\operatorname{site}}(\mathbb{T})$, so we can conclude that $p_c^{\operatorname{site}}(\mathbb{T}) = 1/2$. (Of course, this would be an overkill.)


## 'Large-Deviation' Estimate for $a_{nmb}$
Now we state the proof of continuous differentiability of $\kappa$. As most of the argument is just an elementary computation, we will omit several details.

Recall the following theorem from elementary analysis.
> Let $(f_n): [0,1]\to \RR$ be a sequence of differentiable functions. Suppose that as $n\to\infty$, 
> - $(f_n(x_0))$ converges to a real number $y_0$ for some $x_0 \in [0,1]$, and 
> - $(f_n')$ converges uniformly to a function $g$. 
> 
> Then, $(f_n)$ converges pointwise to a differentiable function $f$ such that $f' = g$.

Keeping this in mind, note that the derivatives of the summands in the series representation $(3)$ of $\kappa$ are given by 
\\[\tag{5}
	\frac{d}{dp}\frac{1}{n}\PP_p[\card{C} = n]
	= \sum_{m,b} \frac{1}{n} a_{nmb} \left(\frac{m}{p} - \frac{b}{1-p}\right)p^m(1-p)^b.
\\]
Hence, to show the differentiability of $\kappa$, we need to show that the term on the right-hand side of $(5)$ decays sufficiently quickly. To do this, we will prove the following 'large-deviation' estimate for $a_{nmb}$, which will provide a sort of 'polynomial decay' of the terms.

> For sufficiently small $\varepsilon > 0$, for all $n \ge 1$ and $p \in (0,1)$, we have 
> \\[\tag{6}
> 	\sum_{m,b: \abs{\frac{m}{p}-\frac{b}{1-p}} > d\varepsilon n} a_{nmb} p^m (1-p)^b
> 	\le 3d^2 n^2 e^{-\frac{1}{3}n \varepsilon^2 p^2 (1-p)}.
> \\]

To begin, note that the sum 
\\[
	\sum_{nmb} a_{nmb}p^m (1-p)^b
\\]
is equal to the probability that $C$ is finite, so we have an inequality 
\\[
	a_{nmb} \le p^{-m} (1-p)^{-b}
\\]
for all $n,m,b$ and $p\in(0,1)$. Minimizing the right-hand side by putting $p = m/(m+b)$, we obtain that 
\\[
	a_{nmb} \le \left(\frac{m+b}{m}\right)^m \left(\frac{m+b}{b}\right)^b.
\\]
Applying this to the left-hand side of $(6)$, we can see that 

$$\begin{aligned}
	(LHS)
	&\le \sum_{m,b: \abs{\frac{m}{p}-\frac{b}{1-p}} > d\varepsilon n} \left(\frac{m+b}{m}\right)^m \left(\frac{m+b}{b}\right)^b p^m (1-p)^b \\
	&\le 2d^2 n^2 \max \left\{ \left(\frac{m+b}{m}\right)^m \left(\frac{m+b}{b}\right)^b p^m (1-p)^b \right\} \\
	&\le 2d^2 n^2 \max_{n-1 \le m \le dn} e^{-\frac{1}{2} m\varepsilon^2 p^2 (1-p) (1+O(\varepsilon))} \\
	&\le 3d^2 n^2 e^{-\frac{1}{3} n\varepsilon^2 p^2 (1-p)}
\end{aligned}$$

where the maximum in the second line is taken over those $n,m,b$'s satisfying 
\\[
	\abs{\frac{m}{p}-\frac{b}{1-p}} > d\varepsilon n
\\]
and the trivial bounds $(4)$, and the third inequality holds by some elementary calculus.


## The Proof of $\kappa \in C^1(0,1)$
Using the previous estimate, we will prove that given $0 < p_1 < p_2 < 1$, the series 
\\[
	\sum_n \frac{d}{dp}\frac{1}{n}\PP_p[\card{C} = n]
	= \sum_n \sum_{m,b} \frac{1}{n} a_{nmb} \left(\frac{m}{p} - \frac{b}{1-p}\right)p^m(1-p)^b
\\]
converges uniformly on $[p_1,p_2]$. This yields that $\kappa$ is $C^1$ on $(0,1)$. We may manually check the continuous differentiability at each of the points $p = 0,1$ with a few more lines of computation.

Let us write 
\\[
	A_{nmb} = \frac{1}{n} a_{nmb} \left(\frac{m}{p} - \frac{b}{1-p}\right)p^m(1-p)^b
\\]
for a shorthand. Fix sufficiently large $N$, and assume that $n \ge N$ and $p\in [p_1,p_2]$. Note that by the trivial bounds $(4)$, we have 
\\[
	\abs{\frac{m}{p} - \frac{b}{1-p}} \le \frac{m+b}{p(1-p)} \le \frac{3dn}{p(1-p)}.
\\]
Applying the large-deviation estimate for 
\\[
	\varepsilon = a\sqrt{\frac{\log n}{n}}
\\]
where $a>0$ is a constant that will be chosen later, we obtain that 

$$\begin{aligned}
	\abs{\frac{d}{dp}\frac{1}{n}\PP_p[\card{C} = n]}
	&\le \sum_{m,b: \abs{\frac{m}{p}-\frac{b}{1-p}} \le d\varepsilon n} \abs{A_{nmb}} + \sum_{m,b: \abs{\frac{m}{p}-\frac{b}{1-p}} > d\varepsilon n} \abs{A_{nmb}} \\
	&\le \frac{1}{n} d\varepsilon n \PP_p[\card{C} = n] + \frac{1}{n} 3d^2 n^2 e^{-\frac{1}{3} n\varepsilon^2 p^2 (1-p)} \frac{3dn}{p(1-p)} \\
	&= da \sqrt{\frac{\log N}{N}} \PP_p[\card{C} = n] + \frac{9d^3}{p(1-p)} n^{2 - \frac{1}{3}a^2 p^2(1-p)} \\
	&\le da \sqrt{\frac{\log N}{N}} \PP_p[\card{C} = n] + \gamma n^{2 - \eta a^2}
\end{aligned}$$

where $\gamma, \eta > 0$ are constants that only depends on $d$, $p_1$, and $p_2$. Now, choosing $a$ so that $2 - \eta a^2 < -2$, we may conclude that 

$$\begin{aligned}
	\sum_{n\ge N} \abs{\frac{d}{dp}\frac{1}{n}\PP_p[\card{C} = n]}
	&\le \sum_{n\ge N} da \sqrt{\frac{\log N}{N}} \PP_p[\card{C} = n] + \sum_{n\ge N} \gamma n^{2 - \eta a^2} \\
	&\le da \sqrt{\frac{\log N}{N}} + \gamma \sum_{n\ge N} n^{-2},
\end{aligned}$$

and this converges to $0$ uniformly as $N \to \infty$.


## References
[1] Essam, J. W., and M. F. Sykes, *Exact critical percolation probabilities for site and bond problem in two dimensions*, Journal of Mathematical Physics **5** (1964), 1117-1127.

[2] Georgakopoulos, A., and C. Panagiotis, *Analyticity results in Bernoulli Percolation*, arXiv preprint arXiv:1811.07404 (2018).

[3] Grimmett, G., *Percolation*, Springer, 1999.

[4] Kesten, H., *Analyticity properties and power law estimates of functions in percolation theory*, Journal of Statistical Physics **25** (1981), 717-756.

[5] Zhang, Y., *A singularity at the criticality for the free energy in percolation*, arXiv preprint math/0301160 (2003).