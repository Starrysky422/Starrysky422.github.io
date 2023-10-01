---
layout: post
title: Two Dimensional Random-Cluster Model
comments: true
tags: 
- Probability Theory
- Percolation Theory
- Random-Cluster Model
- Seminar Talk
---

This post is based on my talk in August 2023 at the Graduate Probability Reading Seminar in percolation and random-cluster model, supervised by [Prof. I. Seo](http://www.math.snu.ac.kr/~insuk.seo/). I, jointly with Jeonghyun Ahn, covered the materials from chapter 6 of Grimmett's textbook [6]---about the planar duality, critical probability, and the first order phase transition of the random-cluster model on the planar square lattice---with some additional remarks on recent progresses made by Duminil-Copin and his coresearchers.


## Our Starting Point
Let a finite graph $G = (V,E)$ and two parameters---the **percolation weight** $p\in[0,1]$ and the **cluster weight** $q\in[1,\infty)$---be given. A **random-cluster measure (RCM)** on $G$ is a probability measure $\phi_{G,p,q}$ on the configuration space $\Omega = \\{0,1\\}^E$ defined by
\\[\tag{1}
	\phi_{G,p,q}(\omega) = \frac{1}{Z_{G,p,q}}\left(\prod_{e\in E} p^{\omega(e)}(1-p)^{1-\omega(e)} \right)q^{k(\omega)},
\\]
where $k(\omega)$ is the number of open clusters (a.k.a. the connected components w.r.t. $\omega$) and the **partition function** $Z_{G,p,q}$ is the scaling constant.

More generally, one can define RCMs on infinite lattices. Let $\LL^d = (\ZZ^d, \EE^d)$ be the $d$-dimensional hypercubic lattice. Then there two ways---that might *not* be equivalent to one another---of defining RCMs on $\LL^d$; one is to pass the RCMs on finite subgraphs $\Lambda \subseteq \LL^d$ to weak limits as $\Lambda \nearrow \LL^d$, and the other is to consider infinite-volume measures whose conditional marginal on finite subgraph $\Lambda \subseteq \LL^d$ is finite-volume measure for almost every outer configuration. Explicit constructions can be found in chapter 4 of [6].

However, one big issue is that such infinite-volume RCM might not be unique. The RCMs may vary as the *boundary conditions* of finite subgraphs change. We can construct two infinite-volume RCMs that are extremal up to stochastic dominance. The minimal one is the **free boundary** measure $\phi_{p,q}^0$ given by the weak limit of finite-volume measures with no boundary conditions, and the maximal one is the **wired boundary** measure $\phi_{p,q}^1$ defined similarily but now the boundaries of finite subgraphs are considered to be joined all together. Luckily, it is known that given $q$, these two measures coincide for almost every $p$, that is, we have the unique RCM for almost every $p$. Also note that the measures $\phi_{p,q}^0$ and $\phi_{p,q}^1$ are invariant under automorphisms of $\LL^d$, tail-trivial, positively associated, and satisfy the *finite energy* property.

Since now we have the RCMs, we can define the quantities of main interest, which are analogous to that of percolation. First, we define the **percolation probabilities**
\\[
	\theta^b(p,q) = \phi_{p,q}^b(0\lrarrow \infty)
\\]
with boundary condition $b=0,1$, and then, the **critical point** 
\\[
	p_c(q) = \sup\\{p: \theta^b(p,q) = 0 \\}.
\\]
Note that the critical point is well-defined and does not depend on the boundary condition as $\theta^b(\blank,q)$ is non-decreasing and we have $\theta^0(p,q) = \theta^1(p,q)$ for almost every $p$.


## Planar Duality
From now on, we concentrate on the planar case $d=2$. The planar case is particularly easy to deal with, and the main reason of it is that we can establish the *planar duality* relationship. Consider the dual lattice $\LL_\mathrm{d}^2 = (\ZZ_\mathrm{d}^2,\EE_\mathrm{d}^2)$, which is the lattice $\LL^2$ shifted by $(\frac{1}{2},\frac{1}{2})$. Then one can relate the random-cluster model on the primal lattice $\LL^2$ with two parameters $p,q$ to that on the dual lattice $\LL_\mathrm{d}^2$ with dual parameters $p_\mathrm{d},q$ in the obvious way described in the picture below, where $p_\mathrm{d}$ is given by 
\\[
	p_\mathrm{d} = \frac{q(1-p)}{p + q(1-p)}.
\\]
More precisely, for every cylinder event $A \subseteq \Omega$ and its dual event $A_\mathrm{d} = \\{\omega_\mathrm{d}: \omega\in A\\}$, we have 
\\[\tag{2}
	\phi_{p,q}^b(A) = \overline\phi_{p_{\mathrm{d}},q}^{1-b}(A_\mathrm{d})
\\]
with boundary condition $b = 0,1$, where the right-hand side is the RCM on the dual lattice.

<p align="center">
<embed src="/svg/two-dimensional-random-cluster-model/image01.svg" type="image/svg+xml" />
<br>
<b>Picture 1.</b> Planar duality
</p>

Note that we have the **self-dual point**
\\[
	p_{\mathrm{sd}}(q) = \frac{\sqrt{q}}{1+\sqrt{q}}
\\]
which is the unique fixed point of the mapping $p \mapsto p_\mathrm{d}$. 


## Criticality at the Self-Dual Point
As in the percolation on the planar square lattice, it is natural to expect that the critical point coincides with the self-dual point, i.e., 
\\[\tag{3}
	p_c(q) = p_\mathrm{sd}(q).
\\]

One part of this equality, $p_c(q) \ge p_\mathrm{sd}(q)$, can be shown by an argument analogous to the percolation theory. The proof goes as follows. Assume to the contrary that $p_c(q) < p_\mathrm{sd}(q)$, and let $p = p_\mathrm{sd}(q)$. Since there exists an infinite open cluster almost surely, we can choose sufficiently large box $\Lambda(n) = [-n,n]^2$ that touches the infinite open cluster with probability $\ge 1-\varepsilon$. Then by FKG inequality, through the so-called *square root trick* following Cox and Durrett, one can show that the infinite open cluster touches the top side of the box, using only the edges outside of the box, with probability $\ge 1-\varepsilon^\frac{1}{4}$. Working on the dual picture as well, we see that with probability $\ge 1-4\varepsilon^\frac{1}{4}$, there are an infinite open path outside of the box touching the top side of the box, one touching the bottom, and infinite dual open paths touching the left and right sides of the dual box. If we let every edge of the box be closed, then for sufficiently small $\varepsilon$, there are two distinct infinite open clusters with positive probability. However, the infinite open cluster is unique almost surely (see chapter 5 of [6]), a contradiction.

<p align="center">
<embed src="/svg/two-dimensional-random-cluster-model/image02.svg" type="image/svg+xml" />
<br>
<b>Picture 2.</b> Illustration of the proof of $p_c(q) \ge p_\mathrm{sd}(q)$ (Adopted from [1])
</p>

However, the other side of the equality had been remained open for a long time. There are three cases that make the problem easier. The first is when $q=1$, which is just a percolation, so we have $p_c(1) = \frac{1}{2}$. The second is when $q=2$, where the problem turns into a matter of the well-known Ising model via the [Edwards-Sokal coupling](https://en.wikipedia.org/wiki/Random_cluster_model#Edwards-Sokal_representation) thus we have $p_c(2) = 2 - \sqrt{2}$. The third is when $q$ is sufficiently large, especially when $q > 25.72$. In this regime, we can relatively easily prove that the random-cluster model exhibits a *first order phase transition* at the critical point, and such phenomenon makes it easy to show the criticality at the self-dual point. The main topic of the rest of this post will be the proof of the first order phase transition in this circumstance. As a remark, it should be mentioned that the equality $p_c(q) = p_\mathrm{sd}(q)$ was proved for every $q\ge 1$ by Beffara and Duminil-Copin [1] in 2012.


## Big Picture
Before we move on to the notion of the order of phase transition, let us illustrate a big picture of random-cluster model and introduce some more important concepts.

There are several equivalent conditions on uniqueness of RCM involving various concepts. Let the **edge density** of random-cluster model be 
\\[
	h^b(p,q) = \phi_{p,q}^b(\text{$e$ is open})
\\]
where $e\in E$ is any edge of the lattice. Since $\phi_{p,q}^b$ is automorphism-invariant, $h^b(p,q)$ does not depend on the choice of the edge $e$. Then one can show that (see chapter 4, 5 of [6]):

> Let $q\in [1,\infty)$ be given. Then, there exists a set $\mathcal{D}_q \subseteq [0,1]$ which is at most countable so that the following are equivalent.
> - $p \not\in \mathcal{D}_q$.
> - The RCM with parameters $p,q$ is unique, i.e., $\phi_{p,q}^0 = \phi_{p,q}^1$.
> - $h^0(p,q) = h^1(p,q)$.
> - $h^b(\blank,q)$ is continuous at $p$ with $b= 0,1$.
> - $\theta^0(p,q) = \theta^1(p,q)$.
> 
> Moreover, if $p \neq p_c(q)$, then the following is also equivalent.
> - $\theta^b(\blank,q)$ is continuous at $p$ with $b=0,1$.

In particular, in the subcritical regime, we have $\theta^0(p,q) = 0$, so there a unique RCM. Hence, taking the planar dual, there is a unique RCM also for all $p \ge p_c(q)\subscr{\mathrm{d}}$. As we have $p_c(q) \ge p_\mathrm{sd}(q)$, we can conclude that we have the unique RCM for all $p$ except possibly at the self-dual point.

One other concept that will be mentioned is the **exponential decay** of connectivity. Recall that the percolation exhibits the exponential decay of the tail distribution of the cluster size, so it is natural to expect that the random-cluster model behaves similarily. In this manner, we can define the following quantity, the exponential decay rate of connectivity (see chapter 5 of [6]).

> Given $p \in [0,1]$ and $q\in[1,\infty)$, there exists a constant $\psi(p,q)\in[0,\infty)$ determined by two coinciding well-defined limits
> \\[
> 	\psi(p,q) = \lim_{n\to\infty} \left[-\frac{1}{n}\log\phi_{p,q}^0(0\lrarrow e_n)\right] = \lim_{n\to\infty} \left[-\frac{1}{n}\log\phi_{p,q}^0(0\lrarrow \partial \Lambda(n))\right]
> \\]
> where $e_n$ is the point $(n,0,\dots,0)\in \ZZ^d$ and $\Lambda(n)$ is the box $[-n,n]^d$.

One important open problem is to prove that $\psi(p,q) > 0$ when $p < p_c(q)$, that is, the exponential decay in the subcritical regime. And a further open problem is, to answer when does the limit 
\\[
	\mu(q) = \lim_{p \nearrow p_c(q)} \psi(p,q)
\\]
called the **mass gap** is strictly positive.

To sum up, we have listed up some main concepts in theory of random-cluster model, that are:
- the uniqueness of RCM, that is, $\phi_{p,q}^0 = \phi_{p,q}^1$;
- the continuous transition, that is, the continuity of $\theta^b(\blank,q)$;
- the continuity of edge densities $h^b(\blank,q)$;
- and the vanishment of the mass gap $\mu(q)$.

Within this picture, now we can introduce what the notion of the order of phase transition is.


## Order of Phase Transition
Phase transitions are divided into two large classes. One is the **first order phase transitions**, which are those involving a latent heat. For instance, the melting of ice and the boiling of water are first order. The other one is the **second order phase transitions**, characterized by an infinite correlation length. The ferromagnetic transition is a typical example of second order phase transitions. Mathematically, these classes are vaguely characterized by three indicators, which might *not* be equivalent to each other.

The first indicator is the *discontinuous transition*. First order phase transitions exhibit discontinuous transition, that is, $\theta^1(p_c(q),q) > 0$. In contrast, second order phase transitions show continuous transition $\theta^1(p_c(q),q) = 0$.

<p align="center">
<embed src="/svg/two-dimensional-random-cluster-model/image03.svg" type="image/svg+xml" />
<embed src="/svg/two-dimensional-random-cluster-model/image04.svg" type="image/svg+xml" />
<br>
<b>Picture 3.</b> Discontinuous and continuous phase transitions
</p>

The second indicator is the *discontinuous edge densities*. A phase transition is of first order if the edge densities $h^b(\blank,q)$ are discontinuous at the critical point $p = p_c(q)$, and is of second order otherwise. Note that the discontinuity of edge densities at the criticality is equivalent to the non-uniqueness of RCM, that is, $\phi_{p_c(q),q}^0 \neq \phi_{p_c(q),q}^1$.

The last indicator is the *non-vanishing mass gap*. The transition is first order if and only if there is a non-vanishing mass gap, that is, $\mu(q) > 0$.

And here comes the relevance of this notion with our problem, the criticality at the self-dual point. Assume that the random-cluster model on $\LL^2$ exhibits first order phase transition for some $q$. Then, by definition, the infinite-volume RCM is not unique at the critical point. However, for the planar square lattice case, such incident can only happen at the self-dual point $p = p_\mathrm{sd}(q)$, so it must coincide with the critical point.

Regarding the order of phase transitions of random-cluster models, there are two major issues. The first is to prove the *sharp transition* between the first and second order in $q$, that is, the existence of the *critical value* $Q(d)$ such that the phase transition is of first order if $q > Q(d)$ and of second order if $q < Q(d)$. And the second issue is to calculate the exact value of $Q(d)$. Unlike what it looks like, even the first problem is extremely difficult, as it is hard to establish certain monotonicity of the indicators. The sharp transition in the planar case with $Q(2) = 4$ was proved by Duminil-Copin and his coresearchers [2,3]; second order for $1\le q\le 4$ in 2015, and first order for $q > 4$ in 2017. For the higher dimensions, it is believed that $Q(d) = 2$ for $d \ge 6$.


## First Order Phase Transition
Although Duminil-Copin et al. proved the strongest form of our problems recently, a smaller regime $q > 25.72$ admits a more intuitive and accessible proof of first order phase transition and criticality at the self-dual point. This will be our main theorem.

Let $a_n$ be the number of self-avoiding walks of length $n$. Then by concatenating two self-avoiding walks, we obtain the submultiplicativity property
\\[
	a_{m+n} \le a_m a_n.
\\]
Hence, with a few lines of analysis, one can show that the limit 
\\[
	\kappa = \lim_{n\to\infty} a_n^{1/n}
\\]
exists and is finite, which is called the **connective constant** of the lattice. The explicit value of $\kappa$ is not known for most of the lattices. The only known case is the planar hexagonal lattice $\HH$, which has $\kappa_\HH = \sqrt{2+\sqrt{2}}$, and it was proved by Duminil-Copin and Smirnov [4] in 2010. For $\LL^2$, we have an old estimate [7] $2.620 < \kappa < 2.696$, and some improvements were made recently.

Define 
\\[
	Q = \left\\{\frac{1}{2}(\kappa + \sqrt{\kappa^2-4})\right\\}^4,
\\]
then we have $21.61 < Q < 25.72$. Let 
\\[
	\psi(q) = \frac{1}{24}\log\left(\frac{(1+\sqrt{q})^4}{q\kappa^4}\right).
\\]
Note that $\psi(q) > 0$ if and only if $q > Q$. We are going to prove the following main theorem.

> Consider the planar square lattice $\LL^2$, and let $q > Q$. Then, the following holds.
> - **(a)** *Criticality at the self-dual point*: $p_c(q) = p_\mathrm{sd}(q)$.
> - **(b)** *Discontinuous transition*: $\theta^1(p_c(q),q) > 0$.
> - **(c)** *Non-vanishing mass gap*: $\mu(q) \ge \psi(q) > 0$. Moreover, for any $\psi < \psi(q)$ and sufficiently large $n$, 
> \\[
> 	\phi_{p_c(q),q}^0(0 \lrarrow \partial\Lambda(n)) \le e^{-n\psi}.
> \\]
> - **(d)** *Discontinuous edge densities*: $h^b(\blank,q)$ is discontinuous at $p_c(q)$ with $b = 0,1$.


## Proof Overview
The key objects in the proof are the *maximal dual circuits surrounding the origin*. The quantity we are interested in is the event that the origin is connected to the infinity point, or the boundary $\partial \Lambda(n)$ of a box. Taking complement of the event, there must exist a dual circuit $\Gamma$ that separates the origin from faraway points. Since there are many of these, we will focus on such circuits that are maximal in some sense, which will be referred as *outer circuits*.

<p align="center">
<embed src="/svg/two-dimensional-random-cluster-model/image05.svg" type="image/svg+xml" />
<br>
<b>Picture 4.</b> A dual circuit surrounding the origin
</p>

Regarding this concept, we can make two estimates. One is a rough circuit counting:
\\[\tag{4}
	(\\#\text{ of dual circuits $\Gamma$ surrounding the origin with length $l$}) \le la_l,
\\]
and this is where the connective constant comes in. This upper bound can be easily justified: if we pick a *basepoint* of $\Gamma$ as the point closest to the right from $(\frac{1}{2},\frac{1}{2})$, then there are at most $l$ such choices, and there are at most $a_l$ dual circuits starting from that point. This is a very rough bound, but it does not matter as we are only interested in exponential scale. The other one, which will be our primary estimate, is that 
\\[\tag{5}
	\phi_{\Lambda(n),p_\mathrm{sd}(q),q}^1 (\Gamma\text{ is an outer circuit}) \le \frac{1}{q}\left(\frac{q}{(1+\sqrt{q})^4}\right)^{|\Gamma|/4}
\\]
for all dual circuit $\Gamma$ surrounding the origin. Combining these two, we obtain an upper bound for the probability of existence of an outer circuit.

From this point, we need a few more technicalities to deduce our main theorem. For part (a) and (b), we can take limit as $\Lambda(n) \nearrow \LL^2$ to obtain the discontinuous transition result. For part (c), which requires an opposite inequality, we will set two more waypoints to reach our destination: the *rectangle crossing* and the *circuit in annulus*. Finally, part (d) immediately follows from (b) and (c) because 
\\[
	\theta^0(p_c(q),q) = 0 < \theta^1(p_c(q),q)
\\]
implies that $\phi_{p_c(q),q}^0 \neq \phi_{p_c(q),q}^1$.


## Notations & Languages
Before we move on, let us define several notations and concepts that will be used in the proof.

Given $n$, let $\Lambda = \Lambda(n)$ be the box $[-n,n]^2 \subseteq \LL^2$ of the primal lattice. Similarily, let $\Lambda_\mathrm{d} = \Lambda(n)\subscr{\mathrm{d}}$ be the dual box $[-n,n-1]^2 + (\frac{1}{2},\frac{1}{2}) \subseteq \LL_\mathrm{d}^2$ of the dual lattice, which is slightly smaller than $\Lambda$. We are going to work in these two boxes.

When we write $\Gamma$, we will always refer to a dual circuit $\Gamma \subseteq \Lambda_\mathrm{d}$ that surrounds the origin, i.e., $0\in \operatorname{int}(\Gamma)$. Given such $\Gamma$, we may partition the edges in $\Lambda$ into three sets:
\\[
	E(\Lambda) = \mathcal{E} \sqcup \mathcal{I} \sqcup \Gamma_\mathrm{d}
\\]
where $\mathcal{E}$ is the set of edges in $\operatorname{ext}(\Gamma)$, and $\mathcal{I}$ is the set of edges in $\operatorname{int}(\Gamma)$.

Given a configuration $\omega$, a dual circuit $\Gamma$ is an **outer circuit (OC)** if 
- **(C)** $\Gamma$ is open in $\omega_\mathrm{d}$, and
- **(E)** the set of vertices right outside of $\Gamma$, that is, 
\\[
	\\{z\in V(\Lambda): z\in\operatorname{int}(\Gamma),\ \|z-x\|_2\le \frac{1}{\sqrt{2}} \text{ for some } x\in V(\Gamma)\\},
\\]
is connected in $\omega$.

We can understand the condition (E) as *we cannot expand the region enclosed by $\Gamma$ anymore*. We write $\operatorname{OC}(\Gamma) \subseteq\\{0,1\\}^{E(\Lambda)}$ for the event that $\Gamma$ is an outer circuit. Note that (C) and (E) are conditions on the edges in $\Gamma_\mathrm{d}$ and $\mathcal{E}$, respectively, and there is no condition imposed on the edges in $\mathcal{I}$. Also note that the conditions on three sets $\mathcal{E}$, $\mathcal{I}$, and $\Gamma_\mathrm{d}$ are independent to each other. For convenience, let $G_\Gamma \subseteq \\{0,1\\}^\mathcal{E}$ be the set of outer configurations satisfying (E).

<p align="center">
<embed src="/svg/two-dimensional-random-cluster-model/image06.svg" type="image/svg+xml" />
<br>
<b>Picture 5.</b> An outer circuit $\Gamma$
</p>

Given a set $F \subseteq E(\Lambda)$ of edges, let $\pi_{F,p,q}$ be the RCM on $F$ but not normalized. More precisely, for a configuration $\omega \in \\{0,1\\}^F$, $\pi_{F,p,q}$ is given by 
\\[
	\pi_{F,p,q}(\omega) = \left(\prod_{e\in F} p^{\omega(e)}(1-p)^{1-\omega(e)}\right)q^{k(\omega,F)}
\\]
where $k(\omega,F)$ is the number of open clusters in $F$. Similarily, we may define the wired boundary RCM $\pi_{F,p,q}^1$ on $F$.


## Step 1: The Primary Estimate
We prove the primary estimate $(5)$ first. Fix $q \ge 1$ and let $p = p_\mathrm{sd}(q)$. From now on, we will omit $p,q$'s in the subscripts. Then we have 
\\[
	\phi\subscr{\Gamma}^1(\operatorname{OC}(\Gamma)) = \frac{1}{Z_\Lambda^1} \sum_\omega 1\subscr{\operatorname{OC}(\Gamma)}(\omega) \cdot \pi_\Gamma^1(\omega)
\\]
where $Z_\Lambda^1$ is the wired boundary partition function on $\Lambda$. As $\operatorname{OC}(\Gamma)$ is determined by two independent conditions (C) and (E), we can rewrite this into 
\\[\tag{6}
	\phi\subscr{\Gamma}^1(\operatorname{OC}(\Gamma)) = \frac{1}{Z_\Lambda^1} (1-p)^{|\Gamma|} \cdot \widetilde{Z}\subscr{\mathcal{E}}^1 \cdot Z\subscr{\mathcal{I}}
\\]
where 
\\[
	\widetilde{Z}\subscr{\mathcal{E}}^1 = \sum_{\omega'\in G_\Gamma} \pi_\mathcal{E}^1(\omega')
\\]
is the wired boundary partition function on $\mathcal{E}$ restricted to $G_\Gamma$, and 
\\[
	Z\subscr{\mathcal{I}} = \sum_{\omega''\in \\{0,1\\}^\mathcal{I}} \pi_\mathcal{I}(\omega'')
\\]
is the partition function on $\mathcal{I}$.

Since we have $q\ge 1$, one can easily deduce the supermultiplicativity of partition functions:
\\[\tag{7}
	Z_\Lambda^1 \ge Z\subscr{\mathcal{E}}^1 \cdot Z\subscr{\mathcal{I}\sqcup \Gamma_\mathrm{d}}^1 \ge \widetilde{Z}\subscr{\mathcal{E}}^1 \cdot Z\subscr{\mathcal{I}\sqcup \Gamma_\mathrm{d}}^1
\\]
This holds because the edges of $\Lambda$ are partitioned into $\mathcal{E} \sqcup \mathcal{I} \sqcup \Gamma_\mathrm{d}$, and we have imposed additional restriction $G_\Gamma$ on $\mathcal{E}$.

Now we relate the two partition functions $Z_\mathcal{I}$ and $Z_{\mathcal{I}\sqcup \Gamma_\mathrm{d}}^1$. Let $\mathcal{I}' = \mathcal{I}\subscr{\mathrm{d}} + (\frac{1}{2},\frac{1}{2})$ be the dual edges $\mathcal{I}\subscr{\mathrm{d}}$ shifted, then we can observe that $\mathcal{I}'$ is contained in $\mathcal{I}\sqcup\Gamma\subscr{\mathrm{d}}$. Hence, again by supermultiplicativity, we obtain 
\\[\tag{8}
	Z\subscr{\mathcal{I}\sqcup \Gamma\subscr{\mathrm{d}}}^1 \ge Z\subscr{\mathcal{I}'}^1 = Z\subscr{\mathcal{I}\subscr{\mathrm{d}}}^1
\\]
as $p = p_\mathrm{d}$.

<p align="center">
<embed src="/svg/two-dimensional-random-cluster-model/image07.svg" type="image/svg+xml" />
<br>
<b>Picture 6.</b> $\mathcal{I}'$ is contained in $\mathcal{I}\sqcup\Gamma_\mathrm{d}$
</p>

Finally, examining the planar duality relationship carefully, we attain that 
<p>$$\begin{align*}
	Z\subscr{\mathcal{I}} 
	&= q^{m-1} \left(\frac{1-p}{p\subscr{\mathrm{d}}}\right)^{|\mathcal{I}|} \cdot Z\subscr{\mathcal{I}_\mathrm{d}}^1(p\subscr{\mathrm{d}},q) \\
	&= q^{m-1 - |\mathcal{I}|/2} \cdot Z\subscr{\mathcal{I}\subscr{\mathrm{d}}}^1 \tag{9}
\end{align*}$$</p>
where $m$ is the number of vertices in $\operatorname{int}(\Gamma)$.

Summing up $(6)$, $(7)$, $(8)$, $(9)$, and a simple double-counting 
\\[
	4m = \\#\\{(v,e): v\in V(\operatorname{int}(\Gamma)),\ e\in E(\Lambda),\ v\sim e\\} = 2\|\mathcal{I}| + |\Gamma|,
\\]
we obtain the primary estimate
<p>$$\begin{align*}
	\phi_{\Lambda}^1(\operatorname{OC}(\Gamma))
	&\le (1-p)^{|\Gamma|} q^{m-1-|\mathcal{I}|/2} \\
	&= \frac{1}{q}\left(\frac{q}{(1+\sqrt{q})^4}\right)^{|\Gamma|/4}.
\end{align*}$$</p>


## Step 2: Passing to the Limit
Using our estimates on dual circuits, we will prove parts (a) and (b) of the main theorem first. Note that 
\\[
	\theta^1(p_\mathrm{sd}(q),q) = \lim_{\Lambda\nearrow\LL^2} \phi_{\Lambda,p_\mathrm{sd}(q),q}^1(0\lrarrow \partial\Lambda).
\\]
If $0 \lrarrow \partial\Lambda$, then there is no open dual circuit surrounding the origin, and thus no outer circuit. Hence, we have 
<p>$$\begin{align*}
	\phi_{\Lambda}^1(0 \lrarrow \partial\Lambda)
	&= \phi_{\Lambda}^1(\nexists \text{outer circuit }\Gamma) \\
	&\ge 1 - \sum_\Gamma \phi_\Lambda^1(\operatorname{OC}(\Gamma)) \\
	&\ge 1 - \sum_\Gamma \frac{1}{q}\left(\frac{q}{(1+\sqrt{q})^4}\right)^{|\Gamma|/4} \\
	&\ge 1 - \sum_l \frac{la_l}{q}\left(\frac{q}{(1+\sqrt{q})^4}\right)^{l/4}.
\end{align*}$$</p>
Since $a_l \sim \kappa^l$, the series in the last line is finite. We would be done if the sum were smaller than $1$. But this might not the case, so we impose an additional trick: we confine our argument to $\Gamma$ outside a large box $\Lambda(N)$. Fixing a large $N$ and enforcing every edge inside $\Lambda(N)$ to be open, there is a constant $c>0$ so that 
<p>$$\begin{align*}
	\phi_{\Lambda}^1(0 \lrarrow \partial\Lambda)
	&\ge c\cdot \phi_{\Lambda}^1(\nexists \text{outer circuit }\Gamma\text{ outside $\Lambda(N)$}) \\
	&\ge c\left\{1 - \sum_{l\ge 4N} \frac{la_l}{q}\left(\frac{q}{(1+\sqrt{q})^4}\right)^{l/4}\right\} \\
	&>0,
\end{align*}$$</p>
hence we obtain $\theta^1(p_\mathrm{sd}(q),q) > 0$. This implies that $p_\mathrm{sd}(q) \ge p_c(q)$, and as we already have the opposite inequality, we can conclude that $p_\mathrm{sd}(q) = p_c(q)$ and $\theta^1(p_c(q),q) > 0$.


## Step 3: Leaping through Waypoints
Before we prove part (c), let us set two waypoints first.

The first waypoint is the *(horizontal) rectangle crossing*. Given a rectangle 
\\[
	R = [0,N]\times[0,M] \subseteq \LL^2,
\\]
we write $C(R)$ for the event that there exists an open path inside $R$ joining two vertical sides of $R$. In particular, denote $R_n = [0,n]\times[0,2n]$ and 
\\[
	\lambda_n = \phi^0(C(R_n)).
\\]
The second waypoint is the *circuit in annulus*. Let $\Delta_n = \Lambda(3n)\setminus\Lambda(n-1)$ be an annulus, and write $A_n$ for the event that there exists a primal open circuit $\Gamma'$ in $\Delta_n$ surrounding the origin.

<p align="center">
<embed src="/svg/two-dimensional-random-cluster-model/image08.svg" type="image/svg+xml" />
<embed src="/svg/two-dimensional-random-cluster-model/image09.svg" type="image/svg+xml" />
<br>
<b>Picture 7.</b> The two waypoints
</p>

The quantity we are interested in is $\phi^0(0\lrarrow\partial\Lambda)$. Note that if we put four copies of $R_n$ inside $\Lambda$ as in the picture below, then we can always find a rectangle crossing among these four whenever $0\lrarrow \partial\Lambda$. Hence, we attain
\\[\tag{10}
	\phi^0(0\lrarrow\partial\Lambda) \le 4\lambda_n.
\\]

<p align="center">
<embed src="/svg/two-dimensional-random-cluster-model/image10.svg" type="image/svg+xml" />
<br>
<b>Picture 8.</b> Connectivity and rectangle crossing
</p>

We will relate the rectangle crossing to the circuit in annulus. In preparation for this, we are going to *stretch* $R_n$ by attaching the copies of it side to side. There exists points $x$ and $y$ on the left and right sides of $R_n$, respectively, such that 
\\[\tag{11}
	\phi^0(x\lrarrow y \text{ in } R_n) \ge \frac{\lambda_n}{(2n+1)^2}.
\\]
Note that subexponential factors do not matter since we are interested in exponential decaying. Attach six copies of $R_n$ horizontally, then considering a long rectangle crossing along alternating $x$ and $y$'s, we obtain that 
\\[\tag{12}
	\phi^0(C([0,6n]\times[0,2n])) \ge \phi^0(x\lrarrow y \text{ in } R_n)^6 \ge \left(\frac{\lambda_n}{(2n+1)^2}\right)^6.
\\]

<p align="center">
<embed src="/svg/two-dimensional-random-cluster-model/image11.svg" type="image/svg+xml" />
<br>
<b>Picture 9.</b> Attaching copies of $R_n$ side to side
</p>

Now, use four copies of the long rectangle $[0,6n]\times[0,2n]$ to construct the annulus $\Delta_n$. Note that if all of the four rectangles admit a rectangle crossing, then there is an open circuit in $\Delta_n$ surrounding the origin. Thus, we have 
\\[\tag{13}
	\phi^0(A_n) \ge \phi^0(C([0,6n]\times[0,2n]))^4 \ge \left(\frac{\lambda_n}{(2n+1)^2}\right)^{24}.
\\]

<p align="center">
<embed src="/svg/two-dimensional-random-cluster-model/image12.svg" type="image/svg+xml" />
<br>
<b>Picture 10.</b> Rectangle crossing and circuit in annulus
</p>

Finally, if $A_n$ occurs, then there must exist a maximal open circuit $\Gamma'$ in $\Delta_n$, and its length must be $\ge 8n$. If we consider $\LL_\mathrm{d}^2$ as the primal lattice, then $\Gamma'$ can be regarded as an outer circuit. As $A_n$ is a finite union of cylinder events, by planar duality $(2)$, we attain 
\\[\tag{14}
	\phi^0(A_n) \le \sum_{l \ge 8n} \frac{la_l}{q} \left(\frac{q}{(1+\sqrt{q})^4}\right)^{l/4}.
\\]

Combining all the inequalities above, we obtain that 
\\[
	\phi^0(0\lrarrow \partial\Lambda) \le 4(2n+1)^2 \left\\{ \sum_{l\ge 8n} \frac{la_l}{q} \left(\frac{q}{(1+\sqrt{q})^4}\right)^{l/4} \right\\}^{1/24},
\\]
and the right-hand side is less than $e^{-n\psi}$ for all $\psi<\psi(q)$ and sufficiently large $n$.

As a remark, it should be mentioned that our two waypoints also play a key role in Beffara and Duminil-Copin's paper [1], but in a much more sophisticated way.


## References
[1] Beffara, V., and H. Duminil-Copin, *The self-dual point of the two dimensional random-cluster model is critical for $q \ge 1$*, Probability Theory Related Fields **153** (2012), 511–542.

[2] Duminil-Copin, H., M. Gagnebin, M. Harel, I. Manolescu, and V. Tassion, *Discontinuity of the phase transition for the planar randomcluster and Potts models with $q > 4$*, Annales de l'ENS **54** (2021),
1363–1413.

[3] Duminil-Copin, H., V. Sidoravicius, and V. Tassion, *Continuity of the phase transition for planar random-cluster and Potts models with $1 \le q \le 4$*, Communications in Mathematical Physics **349** (2017), 47–107.

[4] Duminil-Copin, H., and S. Smirnov, *The connective constant of the honeycomb lattice equals $\sqrt{2+\sqrt{2}}$*, Annals of Mathematics **175** (2012), 1653–1665.

[5] Grimmett, G., *Percolation*, Springer, 1999.

[6] Grimmett, G., *The Random-Cluster Model*, Springer, 2006.

[7] Slade, G., *Bounds on the self-avoiding-walk connective constant*, Journal of Fourier Analysis and Applications Special Issue (1995), 525-533.