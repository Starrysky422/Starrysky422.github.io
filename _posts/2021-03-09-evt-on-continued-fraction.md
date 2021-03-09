---
layout: post
title: EVT on Continued Fraction
comments: true
tags: 
- Ergodic Theory
- Extreme Value Theorem
- Continued Fraction
---

이 글에서는 Galambos의 1972년 논문 "The distribution of the largest coefficient in continued fraction expansions" [1]의 내용을 정리한다.

Galambos의 논문은 [지난 글]({{ site.baseurl }}/2021/03/06/evt-on-modular-surface/)에서 보았던 연분수에 관한 EVT를 증명한다. 이때 $\mu$는 Gauss measure이다.

$$\begin{equation}\lim_{N\to\infty} \mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le \frac{y}{\log 2}N \right\} = e^{-\frac{1}{y}}\tag{1}\end{equation}$$



## $\psi$-Mixing Property

Galambos의 EVT는 본질적으로 Gauss map $T$의 $\psi$-mixing property로부터 얻어지는 결과이다. $\psi$-mixing이 무엇인지 알아보기 전에, $\psi$-mixing보다 약한 조건인 ergodicity와 mixing부터 보자.

$T$가 probability space $(X,\mathcal{M},\mu)$ 위에 주어진 m.p.t.라고 하자. (즉, 모든 $A\in\mathcal{M}$에 대해 $\mu(A) = \mu(T^{-1}A)$) 이때 $T$의 ergodicity는 다음과 같이 주어진다.

> 모든 $\mu(A \Delta T^{-1}A) = 0$인 $A \in \mathcal{M}$에 대해 $\mu(A) = 0$ 또는 $1$이라면 (즉, 모든 $T$-invariant set의 measure가 $0$ 또는 $1$이라면), $T$는 **ergodic**하다.

그리고 더 강한 조건인 $T$의 mixing property는 다음과 같이 주어진다.

> 모든 $A,B\in \mathcal{M}$에 대해, $\mu(A\cap T^{-n}B)\xrightarrow{n\to\infty} \mu(A)\mu(B)$이면 (즉, $A$와 $B$가 *asymptotically independent*하면), $T$는 **mixing**이다.

즉, $T$가 $A$와 $X\setminus A$를 '섞어놓는다'면 ergodic, 모든 $A$와 $B$를 '섞어놓는다'면 mixing이라고 이해할 수 있다. $T$가 mixing일 때 ergodic함의 증명은 $B$ 자리에 $X\setminus A$를 대입하면 쉽게 얻어진다.



한편, 다른 sense에서 mixing을 정의할 수도 있다. 마찬가지로 $(X,\mathcal{M}, \mu)$가 probability space이고, 그 위에 확률변수들(또는 measurable functions) $\mathbf{a} = (a_n)_{n\in\mathbb{N}}$이 주어졌다고 하자. 이때, $\mathcal{A},\mathcal{B}$가 $\mathcal{M}$의 sub-$\sigma$-algebra일 때, 다음 함수를 정의하자:

$$\alpha(\mathcal{A},\mathcal{B}) = \sup_{A\in\mathcal{A}, B\in\mathcal{B}} \left\lvert\mu(A\cap B) - \mu(A)\mu(B)\right\rvert$$

다음과 같은 형태의 집합들을 **cylinder set of rank $k$**이라고 정의하자:

$$I_k = \{x\in X : a_k(x) \in [l,r]\}$$

그리고 $a\le k\le b$인 rank $k$ cyliner set들로 생성되는 $\sigma$-algebra를 $\mathcal{M}^{a,b}$라고 쓰자. 그리고 다시 다음 함수를 정의하자:

$$\alpha(n) = \sup_{t\in\mathbb{N}} \alpha(\mathcal{M}^{1,t}, \mathcal{M}^{t+n,\infty})$$

이때, 만약 $\alpha(n)\xrightarrow{n\to\infty}0$이라면, $\mathbf{a}$가 **mixing** (또는 **$\alpha$-mixing**)이라고 한다. (확률변수 $(a_n)_{n\in\mathbb{N}}$을 $a_n = a_1\circ T^{n-1}$과 같이 두면 앞에서 정의한 mixing의 개념과 비슷하다는 것을 알 수 있다.) 즉, $A,T^{-n}B$가 asymptotically independent하면 $T$를 mixing이라고 한 것과 같이, $a_n$들이 *weakly dependent*하면 이들이 mixing이라고 정의하는 것이다. 이러한 정의는 다음과 같이 다시 쓸 수 있다.

> 어떤 $\alpha(n)\xrightarrow{n\to\infty}0$인 $\alpha$가 존재하여, 모든 $A\in\mathcal{M}^{1,t}, B\in\mathcal{M}^{t+n,\infty}$에 대해 다음이 성립하면 $(a_n)_{n\in\mathbb{N}}$은 $\alpha$-mixing이다.
>
> $$\left\lvert \mu(A\cap B) - \mu(A)\mu(B) \right\rvert \le \alpha(n)$$

$\psi$-mixing은 이 dependency의 rate를 더 약하게 한 것으로 볼 수 있다. 다음과 같은 함수 $\psi$를 정의하자:

$$\psi(\mathcal{A},\mathcal{B}) = \sup_{A\in\mathcal{A}, B\in\mathcal{B}} \left\lvert\frac{\mu(A\cap B)}{\mu(A)\mu(B)} - 1\right\rvert$$

이때 앞에서와 같은 방법으로 $\psi(n)$과 **$\psi$-mixing**을 정의할 수 있다. 이때 자명하게 $\alpha \le \psi$이므로, $\psi$-mixing이면 $\alpha$-mixing이라는 것을 확인할 수 있다. 마찬가지로 이 정의는 다음과 같이 다시 쓸 수 있다.

> 어떤 $\psi(n)\xrightarrow{n\to\infty}0$인 $\psi$가 존재하여, 모든 $A\in\mathcal{M}^{1,t}, B\in\mathcal{M}^{t+n,\infty}$에 대해 다음이 성립하면 $(a_n)_{n\in\mathbb{N}}$은 $\psi$-mixing이다.
>
> $$\left\lvert \mu(A\cap B) - \mu(A)\mu(B) \right\rvert \le \psi(n)\mu(A)\mu(B) \tag{1}$$

이제 Gauss map $T$가 $\psi$-mixing property를 가진다는 것은, $(a_n)_{n\in\mathbb{N}}$을 연분수 전개의 성분으로 두었을 때 이 함수열이 $\psi$-mixing이라는 것으로 이해한다.

사실 $T$는 $\psi$가 exponentially decay하는 것까지 보일 수 있어 exponentially $\psi$-mixing이라는 표현을 쓰고, 논문에서 언급되는 성질도 이쪽이다. 다만 EVT의 증명에는 exponentially decay까지는 필요하지 않다. $T$의 exponentially $\psi$-mixing property의 증명은 추후에 기회가 된다면 다루도록 하겠다.



## Outline of Galambos' EVT

이제 우리가 보여야 하는 EVT를 다시 보자.

$$\lim_{N\to\infty} \mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le \frac{y}{\log 2}N \right\} = e^{-\frac{1}{y}}\tag{2}$$

그런데 [지난 글]({{ site.baseurl }}/2021/03/06/evt-on-modular-surface/)에서 잠깐 보았던, 다음의 성질은 잘 알려져 있고, 그 증명도 Birkhoff ergodic theorem에서 바로 얻어진다.

> 모든 $n,N\in\mathbb{N}$에 대해 다음이 성립한다.
>
> $$\mu(S_{n,N}) = \mu\left\{ x \in [0,1] : a_n \ge N \right\} = \frac{\log(1+\frac{1}{N})}{\log 2}\tag{3}$$

우선 표기의 편의를 위해 $w = \left\lfloor\frac{y}{\log 2}N\right\rfloor$, $p(w) = \frac{\log(1+\frac{1}{w})}{\log 2}$로 두고, $S_{n,w} = A_n$으로 쓰자. 이때 $\log(1+\frac{1}{x}) = \frac{1}{x} + O_x(\frac{1}{x^2})$이므로, $p(w) = \frac{1}{Ny} + O_N(\frac{1}{N^2})$이다.

그런데 만약 $(a_n)_{n\in\mathbb{N}}$가 서로 완전히 독립이었다고 가정하면, Galambos의 EVT는 간단히 증명되었을 것이다.

$$\begin{align*}
\mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le w \right\}
&= \prod_{n=1}^N \mu\left\{ x\in[0,1]: a_n \le w \right\} \tag{4} \\
&= \left( 1- p(w) \right)^N \\
&= \left( 1- \frac{1}{Ny} + O_N\left( \frac{1}{N^2} \right) \right)^N \xrightarrow{N\to\infty} e^{-\frac{1}{y}}
\end{align*}$$

아쉽게도 $(a_n)_{n\in\mathbb{N}}$는 독립이 아니므로, 앞의 $(4)$가 성립하지 않아 포함과 배제를 사용해야 한다.

$$\mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le w \right\} = \sum_{k=0}^N (-1)^k \sum_{1\le i_1 < \dots < i_k \le N} \mu(A_{i_1} \cap \dots \cap A_{i_k}) \tag{5}$$

한편, $(a_n)_{n\in\mathbb{N}}$는 독립은 아니지만 weak dependency, 즉 $\psi$-mixing property를 가진다. 따라서 $(5)$에서 major term들을 제외한 나머지 오차항이 충분히 작아짐을 보이면 그 결과로 원하는 EVT가 보여질 것으로 기대할 수 있다.



## Proof of Galambos' EVT

이제 Galambos의 EVT를 증명할 차례이다. 포함과 배제를 통해 얻은 $(5)$의 우변을 세 개의 부분으로 쪼갤 것이다.

- 우선 $\sum_{k=1}^N$의 tail 부분을 잘라낼 것이다. $\psi$-mixing의 식 $(1)$을 반복해서 적용하면, 다음을 얻을 수 있다.

  $$\mu(A_{i_1}\cap \dots \cap A_{i_k}) \le (1+\psi(1))^{k-1}\prod_{j=1}^k \mu(A_{i_j}) = (1+\psi(1))^{k-1}p(w)^k$$

  따라서 $k$가 커지면 tail의 각 항이 지수적으로 감소하는 한편, $k$에 대해서 항의 개수는 $\binom{N}{k}$개이다. 따라서 적당한 양의 정수 $M$에 대해, 다음을 얻을 수 있다.

  $$\begin{align*}
  &\sum_{k=M+1}^N (-1)^k \sum_{1\le i_1 < \dots < i_k \le N} \mu(A_{i_1} \cap \dots \cap A_{i_k}) \\
  &\le \sum_{k=M+1}^N \binom{N}{k}(1+\psi(1))^{k-1}p(w)^k \\
  &\le \sum_{k=M+1}^N \frac{N^k}{k!}(1+\psi(1))^{k}\left(\frac{2}{Ny}\right)^k \\
  &< \sum_{k=M+1}^\infty \frac{1}{k!}\left(\frac{2+2\psi(1)}{y}\right)^k
  \end{align*}$$
  
  이때 마지막 식은 exponential 함수의 Taylor 급수의 오차항이므로, $M$이 커짐에 따라서 $0$으로 수렴한다. 따라서 급수의 tail 부분은 임의의 양수 $\epsilon$에 대해 $o_M(\epsilon)$으로 쓸 수 있다.
  
- 다음으로 tail을 제외한 나머지 부분을 본다. 이때 만약 $i_j$들이 서로 차이가 많이 난다면, $\psi$-mixing 식 $(1)$을 적용할 때 $n$을 더 큰 수로 잡을 수 있으므로 더 좋은 근사를 할 수 있을 것이다. 그러니 적당한 양의 정수 $m$에 대해, 모든 $j$에 대해 $i_{j+1}-i_j > m$인 항들을 모아서 생각하자.

  $k$를 고정했을 때, 이러한 항의 개수는 $\binom{N-(m-1)(k-1)}{k}$개이므로, 다음을 얻는다.

  $$\begin{align*}
  &\sum_{\substack{1\le i_1 < \dots < i_k \le N \\ i_{j+1} - i_j \ge m}} \mu(A_{i_1} \cap \dots \cap A_{i_k}) \\
  &= \binom{N - (m-1)(k-1)}{k} (1+O_k(\psi(m)))^{k-1}p(w)^k \\
  &= \frac{O_N(N^k)}{k!}(1+O_k(\psi(m)))^{k-1} \left( \frac{1}{Ny} + O_N\left( \frac{1}{N^2} \right) \right)^k \\
  &= \frac{y^{-k}}{k!}(1+O_k(\psi(m)))^{k-1} \left( 1 + O_N\left( \frac{1}{N} \right) \right)^k
  \end{align*}$$
  
- 앞의 두 부분을 제외한 나머지 항들을 생각하자. $k$를 고정했을 때, 이러한 항의 개수는 $\binom{N}{k} - \binom{N-(m-1)(k-1)}{k}$개이고, 이는 $N$에 대한 $(k-1)$차 이하의 다항식으로 나타나므로, 다음을 얻는다.

  $$\begin{align*}
  &\sum_{\substack{1\le i_1 < \dots < i_k \le N \\ \exists i_{j+1} - i_j < m}} \mu(A_{i_1} \cap \dots \cap A_{i_k}) \\
  &= \left( \binom{N}{k} - \binom{N - (m-1)(k-1)}{k} \right) (1+O_k(1))^{k-1}p(w)^k \\
  &= o_N(N^k)(1+O_k(1))^{k-1} \left( \frac{1}{Ny} + O_N\left( \frac{1}{N^2} \right) \right)^k \\
  &= o_N\left( \left(1+\frac{1}{N}\right)^k \right) (1+O_k(1))^{k-1}
  \end{align*}$$

이제 앞의 세 식을 종합하면, 다음을 얻는다.

$$\begin{align*}
&\mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le w \right\} \\
&= \sum_{k=0}^N (-1)^k \sum_{1\le i_1 < \dots < i_k \le N} \mu(A_{i_1} \cap \dots \cap A_{i_k}) \\
&= o_M(\epsilon) + \sum_{k=0}^M (-1)^k \Bigg( \frac{y^{-k}}{k!}(1+O_k(\psi(m)))^{k-1} \left( 1 + O_N\left( \frac{1}{N} \right) \right)^k  \\
& \qquad\qquad\qquad + o_N\left( \left(1+\frac{1}{N}\right)^k \right) (1+O_k(1))^{k-1} \Bigg) \\
& \xrightarrow{N\to\infty} o_M(\epsilon) + \sum_{k=0}^M (-1)^k \frac{y^{-k}}{k!}(1+O_k(\psi(m)))^{k-1} \\
& \xrightarrow{m\to\infty} o_M(\epsilon) + \sum_{k=0}^M (-1)^k \frac{y^{-k}}{k!} \\
& \xrightarrow{M\to\infty} e^{-\frac{1}{y}}
\end{align*}$$

이것으로 Galambos의 EVT의 증명이 마무리된다.

한편, 이 증명에서 우리는 $(3)$과 $\psi$-mixing 이외에는 $T$의 성질을 전혀 사용하지 않았다는 것을 확인할 수 있다. 따라서 Galambos의 EVT는 본질적으로 $T$의 $\psi$-mixing property에서 얻어지는 것이며, 반대로 $\psi$-mixing이 주어진다면 항상 EVT를 해결할 수 있음을 알 수 있다.



## References

[1] J. Galambos, *The distribution of the largest coefficient in continued fraction expansions*, The Quarterly Journal of Mathematics **23** (1972), 147-151.

[2] M. Einsiedler and T. Ward, *Ergodic theory*, Springer London Limited, 2013.

[3] M. Pollicott, *Limiting distributions for geodesics excursions on the modular surface*, Contemporary Mathematics **14** (2009), 177-185.

[4] R. Bradley, *Basic properties of strong mixing conditions. A survey and some open questions*, arXiv preprint (2005) math/0511078.