---
layout: post
title: EVT on Modular Surface
comments: true
tags: 
- Ergodic Theory
- Extreme Value Theorem
---

이 글에서는 Pollicott의 2009년 논문 "Limiting distributions for geodesics excursions on the modular surface" [4]의 내용을 정리한다.

- 2021.3.21 수정: 이 논문에서 일부 gap을 발견하였으며, 이를 해소하기 위해서는 statement를 고칠 필요가 있다. Pollicott의 EVT는 본 글에 서술된 식이 아닌, [다음 글]({{ site.baseurl }}/2021/03/21/clt-and-serious-gap-in-pollicott-evt/)에서 서술한 식으로 생각한다. 해당 식을 사용하더라도 본 글의 내용은 크게 달라지지 않는다.



## What is Extreme Value Theorem(EVT)?

우선 EVT가 무엇인지부터 짚고 넘어가자. EVT는 원래 중심극한정리, 큰 수의 법칙 등과 같이 확률론에서 유래된 문제이다. 어떤 random process가 주어져 있을 때, 각 state들은 시간이 지남에 따라 process를 따라서 이동할 것이다. 이때, 이 state들이 그리는 궤적의 'extreme value'의 분포는 어떻게 될까? 즉, 초기 지점에 대한 편차의 최댓값의 분포를 관찰하는 것이다. 더 정확히 적으면 다음과 같다.

> 확률공간의 초기 state $v(0)$에 대해 $t$초 후 state를 $v(t)$라고 하자. 시간 $T$에 관한 함수 $N$에 대해, $T\to\infty$일 때
>
> $$\sup_{0\le t\le T} d(v(t),v(0)) \le N$$
>
> 일 확률은 얼마인가?

여기서 random process를 geodesic flow로 바꿔주면 동역학의 문제와 같이 볼 수 있다. Noncompact space $X$ with finite measure $m$에 대해, $X$의 unit tangent bundle $T^1X$에 Liouville measure $\mu$를 주자. ($d\mu = dmd\theta$로 생각하면 된다) 이제 다음과 같은 문제를 생각한다.

> Geodesic ray 중 시간 $[0,T]$ 동안 최대 거리 $N$의 영역 안에만 머무는 것의 비율은 얼마나 되는가? 즉, $v(t)$가 geodisic일 때 다음의 값은 얼마인가?
>
> $$\lim_{T\to\infty} \mu\left\{ v(0)\in T^1 X : \sup_{0\le t\le T} d(v(t),v(0)) \le N \right\}$$

이와 같은 형태의 문제에 대한 답을 모두 **extreme value theorem(EVT)**라고 부른다.



## Pollicott's EVT and Behavior of Geodesic Excursion

Pollicott은 modular surface $X = \mathbb{H}/SL_2(\mathbb{Z})$ 위의 geodesic flow에 관한 EVT를 해결하였다. Pollicott의 EVT는 다음과 같은 형태를 가진다.

>$$\begin{equation}\lim_{T\to\infty} \mu\left\{ v(0)\in T^1 X : \sup_{0\le t\le T} d(v(t),v(0)) - \log T \le \log\frac{6y}{\pi} \right\} = e^{-\frac{1}{y}}\tag{1}\end{equation}$$

여담으로, 이 EVT를 증명하면 어디에 써먹을 수 있는지를 잠시 보자. Pollicott은 다음과 같은 (almost everywhere) asymptotic behavior를 제시하고 있다. (이는 Sullivan이 1982년에 증명한 내용이다 [1].)

> 거의 모든 $v(0) \in T^1X$에 대해, 다음이 성립한다.
>
> $$\begin{equation} \limsup_{t\to\infty} \frac{d(v(t),v(0))}{\log t} = 1 \tag{2}\end{equation}$$

증명은 간단한 편이다. 천천히 따라가 보자. $\le$ 방향과 $\ge$ 방향으로 나누어 보인다.

- $\le$ 방향은 [Borel-Cantelli lemma](https://en.wikipedia.org/wiki/Borel%E2%80%93Cantelli_lemma)에 의해 보여진다. 이 부분 논문 표현이 조금 명확하지가 않은데 ("trivial direction, following immediately from the Borel-Cantelli lemma"), 아마 EVT를 쓰지 않더라도 Sullivan [1]이 증명한 방식이 충분히 간단하다는 의미인 것 같다.

  우선 $x = i\in \mathbb{H}$를 고정하면, $\limsup\frac{d(v(t),v(0))}{\log t} = \limsup\frac{d(v(t),x)}{\log t}$이므로 $d(v(t),x)$로 식을 고쳐도 상관 없다. 이제 적당한 상수 $C>0$에 대해, 모든 $t$와 충분히 큰 모든 $N$에 대해서 다음이 성립함을 보이자.
  
  $$\begin{equation}\mu(E_{t}) = \mu\left\{ v(0)\in T^1X : d(v(t),x) \ge N \right\} < Ce^{-N}\tag{3}\end{equation}$$
  
  그런데 geodesic flow는 부피를 보존하므로, 다음을 보여도 된다.
  
  $$\mu\left\{ v(0)\in T^1X : d(v(0),x) \ge N \right\} < Ce^{-N}$$
  
  이제 그림을 그려보면, 원하는 집합은 충분히 큰 $N$에 대해 다음과 같다.
  
  <embed src="/svg/evt-on-modular-surface/image01.svg" type="image/svg+xml" />
  
  그 부피는 대략 다음과 같을 것이므로, 나머지 디테일은 적당히 채울 수 있을 것이다.
  
  $$\begin{align*} \mu\left\{ v(0)\in T^1X : d(v(0),x) \ge N \right\} & \approx \int_0^{2\pi} \int_{e^N}^\infty \int_{-1}^1 \frac{1}{y^2} dxdyd\theta \\ & = 4\pi e^{-N} \end{align*}$$
  
  임의의 $\epsilon>0$에 대해, 거의 모든 $v(0)\in T^1 X$에 대해서, $d(v(n),x) \ge (1+\epsilon)\log n$인 양의 정수 $n$이 유한함을 보이자. 그러면 $t$가 커짐에 따라 $\frac{d(v(t),x)}{\log t}$의 변동 폭이 작아지므로 증명이 끝날 것이다. 그런데 $(3)$에서 $t = n$, $N = (1+\epsilon)\log n$으로 두면 $\sum\mu(E_n) < Cn^{-(1+\epsilon)} < \infty$이고, 따라서 Borel-Cantelli lemma에 의해 $\displaystyle\limsup_{n\to\infty} E_n$이 null set이 되어 증명이 끝난다.



- $\ge$ 방향은 기초적인 측도 논의를 통해 보일 수 있다. (논문에는 디테일이 조금 생략되어 있다.) 귀류법을 쓰면, 다음을 만족하는 $\epsilon_1,\epsilon_2>0$이 존재한다.

  $$ \mu\left\{ v(0)\in T^1X : \limsup_{t\to\infty} \frac{d(v(t),v(0))}{\log t} \le 1-\epsilon_1 \right\} \ge \epsilon_2 $$

  이제 위 집합에 속한 각 $v(0)$에 대해, 다음을 만족하는 $T_0, T_1$을 잡을 수 있다. 특히, compact subset $K$ 위에서는 이들을 uniform하게 잡아줄 수 있다.

  $$\sup_{t \ge T_0} \frac{d(v(t),v(0))}{\log t} \le 1 - \frac{\epsilon_1}{2}$$

  $$\sup_{0\le t\le T_0} d(v(t),v(0)) \le \left(1-\frac{\epsilon_1}{2}\right)\log T_1$$

  이제 $K$를 $\mu(K) \ge \frac{\epsilon_2}{2}$가 되도록 잡아주면, 모든 $T \ge \max\\{T_0,T_1\\}$에 대해 다음을 얻는다.

  $$\begin{equation}\mu\left\{ v(0)\in T^1X : \sup_{0\le t\le T} d(v(t),v(0)) \le \left(1-\frac{\epsilon_1}{2}\right)T \right\} \ge \frac{\epsilon_2}{2}\tag{4}\end{equation}$$

  한편, Pollicott의 EVT $(1)$을 보면, 임의의 $y>0$에 대해 어떤 $T_y$가 존재해서, 모든 $T\ge T_y$에 대해 다음이 성립한다.

  $$\begin{equation}\left\lvert \mu\left\{ v(0)\in T^1 X : \sup_{0\le t\le T} d(v(t),v(0)) - \log T \le \log\frac{6y}{\pi} \right\} - e^{-\frac{1}{y}}\right\rvert < \frac{\epsilon_2}{4}\tag{5}\end{equation}$$

  이제 $e^{-\frac{1}{y}}<\frac{\epsilon_2}{4}$가 되도록 $y$를 충분히 크게 잡고, $\frac{\epsilon_1}{2}\log T + \log\frac{6y}{\pi} > 0$이 되도록 $T  \ge \max\\{T_0,T_1,T_y\\}$를 충분히 크게 잡으면 $(4),(5)$에서 모순이 생긴다.



## Galambos' EVT on Continued Fraction

Hyperbolic space의 동역학과 연분수 사이의 연관은 ergodic theory의 가장 기초적인 내용 중 하나이다. Pollicott 또한 다음의 연분수에 관한 Galambos의 EVT [2]를 이용하여 modular surface에서의 EVT를 증명하고 있으며, 사실상 이것이 Pollicott의 EVT의 실질적인 함의라고 할 수 있다.

$$\begin{equation}\lim_{N\to\infty} \mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le \frac{y}{\log 2}N \right\} = e^{-\frac{1}{y}}\tag{6}\end{equation}$$

Galambos의 EVT에 관해서는 [다음 글]({{ site.baseurl }}/2021/03/09/evt-on-continued-fraction/)에서 다룬다. 한편, 앞에서 Sullivan의 asymptotic behavior formula를 증명하는 방식을 따라하면, 연분수에 관해서도 다음과 같은 analogue를 얻을 수 있다.

> Gauss measure $\mu$에 대해, 거의 모든 $x\in[0,1]$에 대하여 다음이 성립한다.
>
> $$\limsup_{N\to\infty} \frac{\max_{1\le n\le N} \log a_n}{\log N} = 1$$

이때 $\ge$ 방향은 똑같이 증명할 수 있지만, $\le$ 방향은 $(3)$의 analogue가 필요하다. 이는 다음과 같이 주어지며, Gauss map의 ergodicity와 Birkhoff ergodic theorem을 이용하여 쉽게 증명할 수 있다.

> 모든 $n,N\in\mathbb{N}$에 대해 다음이 성립한다.
>
> $$\begin{equation}\mu\left\{ x \in [0,1] : a_n \ge N \right\} = \frac{\log(1+\frac{1}{N})}{\log 2}\tag{7}\end{equation}$$

$N$ 대신 $e^N$을 넣으면, $\log(1+e^{-N}) \approx e^{-N}$이므로 같은 형태라는 것을 알 수 있다.



## Proof of Pollicott's EVT

이제 Galambos의 EVT를 이용하여 Pollicott의 EVT를 증명해보자. [지난 글]({{ site.baseurl }}/2021/03/05/relationship-between-continued-fraction-and-modular-surface/)에서 살펴본 geodesic flow와 연분수의 관계를 다시 보자.

<embed src="/svg/evt-on-modular-surface/image02.svg" type="image/svg+xml" />

우리가 원하는 것은 어떤 geodesic이 초기 지점에서 가장 멀리 떨어진 지점까지의 거리에 관한 식이다. 이 geodesic의 양 끝점을 다시 $-y$, $\frac{1}{x}$라고 두자. 가장 멀리 떨어진 지점은 결국 cusp쪽으로의 excursion을 이야기하는 것이고, 이는 각 단계에서 허수축으로 가장 멀리 떨어진 지점으로 근사할 수 있다. 그런데 geodesic이 반원이므로, 이때 허수 성분은 원의 반지름이고, hyperbolic distance는 여기에 log를 취한 값이 될 것이다. 이때 원의 지름이 약 $a_n(x)$이므로, $n$단계에서 최대 excursion의 크기는 약 $\log a_n$으로 근사할 수 있다.

그러면 $n$단계까지 걸리는 시간은 얼마일까? 이는 return-time function $r(x,y)$에 대해 $\sum_{i=0}^{n-1}r(\overline{T}^i(x,y))$로 주어진다. 그런데 지난 글에서 $r(x,y) = -2\log x$로 재정의해도 무관하다고 하였고, 또한 Birkhoff ergodic theorem에 의해 다음을 얻는다. ($\mu$는 Gauss measure)

$$\frac{1}{n}\sum_{i=0}^{n-1}r(\overline{T}^i(x,y)) \xrightarrow{n\to\infty} \int_0^1r(x,y)d\mu(x) = \frac{\pi}{6\log 2}$$

따라서 $n$단계 excursion까지 걸리는 시간은 $\frac{\pi}{6\log 2}n$으로 근사할 수 있다.

이제 Galambos의 EVT를 적용하면, 다음과 같이 Pollicott의 EVT를 보일 수 있다.

$$\begin{align*}
&\lim_{T\to\infty} \mu\left\{ v(0)\in T^1 X : \sup_{0\le t\le T} d(v(t),v(0)) \le \log\left(\frac{6y}{\pi}T\right) \right\} \\
&= \lim_{N\to\infty} \mu\left\{ x\in[0,1] : \max_{1\le n\le N} \log a_n \le \log \left(\frac{y}{\log 2}N\right) \right\} \tag{8}\\&= \lim_{N\to\infty} \mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le \frac{y}{\log 2}N \right\} \\
&= e^{-\frac{1}{y}}
\end{align*}$$

- 2021.3.21 수정: 사실 $(8)$의 등식은 gap이 있다. 우리는 $T$와 $N$ 사이에 asymptotic한 관계만 보였는데, 위 등식에서는 이들이 서로 같은 것처럼 조작하고 있다. 이 부분을 엄밀하게 계산하려면 CLT를 적용해야 하는데, 이는 [다음 글]({{ site.baseurl }}/2021/03/21/clt-and-gaps-in-pollicott-evt/)을 참조한다.



## Further Studies

Pollicott은 $SL_2(\mathbb{Z})$의 finite index subgroup인 principal congruence subgroup $\Gamma = \Gamma(m)$에 대해서도 비슷한 형태의 EVT를 보일 수 있다고 설명한다. $\mathbb{H}/\Gamma(m)$의 geodesic은 연분수를 $\bmod m$으로 보는 것과 analogy를 가진다. 이때 equidistribution을 통해 $(7)$의 analogue를 찾고, mixing condition을 찾아서 Galambos' EVT의 analogue를 찾으면 비슷한 논리를 적용할 수 있다.

한편, Sullivan이 제시한 geodesic excursion의 asymptotic behavior는 사실 principal congruence subgroup뿐만 아니라 모든 Fuchian group $\Gamma$에 대해 $\mathbb{H}/\Gamma$에서도 성립하는 내용이다. (즉, $m(\mathbb{H}/\Gamma)<\infty$인 모든 discrete subgroup $\Gamma \le SL_2(\mathbb{R})$에 대해 성립한다) 그렇다면 Pollicott의 것과 같은 EVT는 어떤 Fuchsian group에 대해서 보여질 수 있을까?



## References

[1] D. Sullivan, *Disjoint spheres, approximation by imaginary quadratic numbers, and the logarithm law for geodesics*. Acta mathematica **149** (1982), 215-237.

[2] J. Galambos, *The distribution of the largest coefficient in continued fraction expansions*, The Quarterly Journal of Mathematics **23** (1972), 147-151.

[3] M. Einsiedler and T. Ward, *Ergodic theory*, Springer London Limited, 2013.

[4] M. Pollicott, *Limiting distributions for geodesics excursions on the modular surface*, Contemporary Mathematics **14** (2009), 177-185.

[5] S. Kwon, and S. Lim, *Limiting distribution of geodesics in a geometrically finite quotients of regular trees*, arXiv preprint arXiv:1901.09514 (2019).