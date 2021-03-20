---
layout: post
title: CLT and serious gap in Pollicott's EVT
comments: true
tags: 
- Ergodic Theory
- Extreme Value Theorem
---

이 글에서는 Pollicott의 2009년 논문 "Limiting distributions for geodesics excursions on the modular surface" [1]의 gap과 이를 해소하기 위한 시도에 관해 다룬다.



## 'Proof' of Pollicott's EVT

[지난 글]({{ site.baseurl }}/2021/03/06/evt-on-modular-surface/)에서 살펴본 Pollicott EVT의 증명을 돌아보자. Pollicott은 geodesic flow에 관한 자신의 EVT가 연분수에 관한 Galambos의 EVT와 실질적으로 같음을 보임으로써 EVT를 증명하였다.

<embed src="/svg/clt-and-serious-gap-in-pollicott-evt/image01.svg" type="image/svg+xml" />

조금 더 자세히 적으면, geodesic coding을 볼 때, $n$단계에서 시간은 return-time function $r(x,y)$에 대해 $\sum_{i=0}^{n-1}r(\overline{T}^i(x,y))$로 주어지고, geodesic excursion은 대략 geodesic의 높이로 볼 수 있을 것이다. 일단 앞으로의 표기의 편의를 위해 $T_n = \sum_{i=0}^{n-1}r(\overline{T}^i(x,y))$로 적자. 이때 시간 $T_n$은 ergodic theorem에 의해 $\frac{\pi}{6\log 2}n$으로 근사되고, 높이는 약 $\log a_n$이므로 Galambos EVT의 두 항을 Pollicott EVT의 두 항으로 바꿔치기 할 수 있다는 것이다.

$$\begin{align*}
&\lim_{T\to\infty} \mu\left\{ v(0)\in T^1 X : \sup_{0\le t\le T} \exp(d(v(t),v(0))) \le \frac{6y}{\pi}T \right\} \\
&= \lim_{N\to\infty} \mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le \frac{y}{\log 2}N \right\}\\
&= e^{-\frac{1}{y}}
\end{align*}$$

그런데 이거, 전혀 당연하지가 않다. 애초에 연분수와 geodesic excursion에 관한 두 항들은 각각 서로 같은 것이 아니라, *asymptotic하게만* 같은 것이다. 이 둘의 오차가 얼마나 날지도 모르는데 단지 $T\to\infty$라고 해서 이를 갈아치워도 되는 것일까? 그리고 우리가 한 논의는 '$n$번째 단계'에 대해서만 한 것이기에, discrete한 시간 단위에서만 성립하는 논의이지 모든 $T$에 대해서 할 수 있는 논의가 아니다. 즉, $N\to\infty$를 $T\to\infty$로 고쳐도 되는 것일까?

정리하면, Pollicott 논문의 gap을 메우기 위해 필요한 논의는 다음 세 가지로 요약할 수 있다.

- **Step 1**: $\frac{y}{\log 2}N$을 $\frac{6y}{\pi}T_N$으로 고쳐도 되는가
- **Step 2**: $\max_{1\le n\le N} a_n$을 $\sup_{1\le t\le T_N} \exp(d(v(t),v(0)))$으로 고쳐도 되는가
- **Step 3**: $N\to\infty$($T_N\to\infty$)를 $T\to\infty$로 고쳐도 되는가

결론을 스포일러하자면, Step 1은 중심극한정리를 전제하면 해결되고, Step 3는 잘 해결되지만, Step 2에서 문제가 조금 심각해진다.



## Central Limit Theorem

우선 Step 1을 해결하기 위해, 중심극한정리(CLT)가 무엇인지 알아보자. 고전적인 CLT는 다음과 같이 주어진다.


> $(X_n)\subscr{n\in\mathbb{N}}$이 같은 확률분포를 따르고 서로 독립(i.i.d.)이라고 하자. 확률분포의 기댓값이 $\mu$, 분산이 $\sigma^2$일 때, 표본평균 $\overline{X}_n = \frac{1}{n}\sum\subscr{i=1}^n X_i$의 분포는 정규분포 $N(\mu,\sigma^2)$으로 수렴한다.

이때 분포가 수렴한다는 것은, 누적확률분포함수가 pointwise하게 수렴한다는 의미이다. 즉, $Z \sim N(\mu,\sigma^2)$일 때, 모든 $x$에 대해 다음이 성립한다.

$$P(\overline{X}_n \le x) \xto{n\to\infty} P(Z \le x)$$

물론 우리의 문제 상황에서는 i.i.d. 조건이 성립하지 않는다. $T_n = \frac{1}{n}\sum_{i=0}^{n-1}r(\overline{T}^i(x,y))$에 대해 CLT를 적용하고 싶은데, $\overline{T}$가 m.p.t.이므로 $r(\overline{T}^i(x,y))$의 확률분포는 서로 같겠으나, 이들이 서로 독립인 것은 아니다. 하지만 이들의 종속성은 매우 약할 것으로 기대할 수 있다. 확률변수 사이의 mixing을 다른 말로 *asymptotically independent*라고 했던 것처럼, 확률변수들 사이에 적당한 mixing 조건이 주어지면 이들에 대해서도 CLT를 얻을 수 있다.

Modular surface의 geodesic flow에 관해서 CLT가 성립함이 알려져 있다고 하니, 이후 내용에서는 다음을 가정하자.

> 어떤 상수 $\sigma>0$에 대해, 다음 확률변수의 분포는 $N\to\infty$일 때 정규분포 $N(0,1)$로 수렴한다.
>
> $$Z_N = \frac{T_N - \frac{\pi}{6\log 2}N}{\sigma\sqrt{N}}$$



## Step 1: $N$ to $T_N$

본격적인 증명 전에, Galambos의 EVT에 관한 간단한 note를 언급한다. Galambos의 EVT는 다음과 같은 형태였다.

$$\lim_{N\to\infty} \mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le \frac{y}{\log 2}N \right\} = e^{-\frac{1}{y}}$$

이때 부등식 우변의 $\frac{y}{\log 2}N$에 $o(N)$의 오차가 생겨도 같은 결과를 얻을 수 있다. 이는 $y$ 자리에 $y\pm\epsilon$을 넣어서 EVT를 적용한 뒤, $\epsilon\to0$으로 샌드위치를 적용하면 간단히 보일 수 있다. 따라서 앞으로는 다음과 같은 형태의 Galambos EVT를 생각한다.

$$\lim_{N\to\infty} \mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le \frac{y}{\log 2}N + o(N) \right\} = e^{-\frac{1}{y}}\tag{1}$$

Step 1에서 CLT가 필요한 이유는 무엇일까? 이는 $N$과 $T_N$ 사이의 asymptotic behavior의 오차를 다루기 위해서이다. CLT가 주어지면 $T_N$의 분포를 안다는 것이고, 이는 asymptotic behavior의 오차가 큰 영역의 measure를 원하는만큼 줄일 수 있다는 것이다. 그리고 오차가 작은 영역에서는 $(1)$의 EVT를 이용해서 오차를 무시할 수 있다.

더 엄밀하게 적어보자. 우선 $\epsilon>0$을 고정하자. 이때 CLT에 의해, 어떤 $C>0$과 $N_0$이 존재하여, 모든 $N\ge N_0$에 대해 다음이 성립하게 할 수 있다.

$$\mu(B_N) \ge 1 - \epsilon \quad\text{ where }\quad B_N = \left\{ x\in[0,1] : \lvert Z_N \rvert \le \frac{C}{\sigma} \right\}$$

이때 집합 $B_N$을 $T_N$에 대해 다시 적으면 다음과 같다.

$$B_N = \left\{ x\in[0,1] : \left\lvert T_N - \frac{\pi}{6\log 2}N \right\rvert \le C\sqrt{N} \right\}$$

즉, $T_N$이 그 기댓값 $\frac{\pi}{6\log 2}N$과 크게 차이나는 영역을 $\epsilon$의 measure로 컨트롤할 수 있다는 것이다. 이 부분은 마지막에 $\epsilon\to0$을 취해주면 되니, 더 이상 신경 쓸 필요가 없다.

이제 나머지 부분을 보자. 우리가 관심이 있는 집합은 다음과 같다.

$$A_N = \left\{ x\in[0,1] : \max_{1\le n\le N}a_n \le \frac{6y}{\pi}T_N \right\}$$

그런데 우리가 $B_N$ 안에서는 $T_N$의 오차를 조절할 수 있으니, 다음의 두 집합 $A_N'$, \\(A_N''\\)을 이용하여 $A_N$을 샌드위치할 수 있다.

$$A_N'\cap B_N \subseteq A_N\cap B_N \subseteq A_N''\cap B_N$$

$$\begin{align*} \text{ where }\quad
A_N' &= \left\{ x\in[0,1] : \max_{1\le n\le N}a_n \le \frac{y}{\log 2}N - \frac{6yC}{\pi}\sqrt{N} \right\}, \\
A_N'' &= \left\{ x\in[0,1] : \max_{1\le n\le N}a_n \le \frac{y}{\log 2}N + \frac{6yC}{\pi}\sqrt{N} \right\}
\end{align*}$$

이제 $(1)$의 EVT를 적용하면, 어떤 $N_1$이 존재해서 모든 $N \ge N_1$에 대해 다음이 성립한다.

$$\lvert \mu(A_N') - e^{-\frac{1}{y}} \rvert < \epsilon , \quad \lvert \mu(A_N'') - e^{-\frac{1}{y}} \rvert < \epsilon$$

이를 종합하면, 모든 $N \ge \max\\{N_0,N_1\\}$에 대해 다음이 성립하게 된다.

$$\lvert \mu(A_N) - e^{-\frac{1}{y}} \rvert < 3\epsilon$$

따라서 다음을 얻게 되어 Step 1의 증명이 끝난다.

$$\lim_{N\to\infty} \mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le \frac{6y}{\pi}T_N \right\} = e^{-\frac{1}{y}}$$

물론 논의를 조금 수정하면, 이 식의 부등식 우변에도 $o(N)$의 오차항을 추가할 수 있다.



## Step 3: $T_N$ to $T$

일단 Step 2를 무사히 잘 해결했다고 치고, Step 3를 먼저 보자. 즉, 우리에게 다음의 EVT가 주어져있다고 생각하자.

$$\lim_{N\to\infty} \mu\left\{ v(0)\in T^1 X : \sup_{0\le t\le T_N} \exp(d(v(t),v(0))) \le \frac{6y}{\pi}T_N + o(N) \right\} = e^{-\frac{1}{y}} \tag{2}$$

이제 우리가 원하는 것은, 위 극한을 모든 $T$에 대해 확인하여 $N\to\infty$를 $T\to\infty$로, $T_N$을 $T$로 고치는 것이다.

이 부분도 Step 1과 비슷한 아이디어를 적용하여 해결할 수 있다는 것을 알 수 있다. 여기서도, 우리가 관심이 있는 집합은 다음의 집합이다.

$$A_T = \left\{ v(0)\in T^1X : \sup_{0\le t\le T}\exp(d(v(t),v(0))) \le \frac{6y}{\pi}T \right\}$$

한편 $(T_N)$이 단조증가하므로, $T_N \le T < T_{N+1}$인 $N$을 유일하게 찾을 수 있다. 그리고 이 $N$에 대해, 다음과 같은 두 집합을 생각하자.

$$\begin{align*}
&\left\{ v(0)\in T^1X : \sup_{0\le t\le T_N}\exp(d(v(t),v(0))) \le \frac{6y}{\pi}(T_N + r(\overline{T}^N(x,y))) \right\}, \\
&\left\{ v(0)\in T^1X : \sup_{0\le t\le T_{N+1}}\exp(d(v(t),v(0))) \le \frac{6y}{\pi}(T_{N+1}-r(\overline{T}^N(x,y))) \right\}
\end{align*}$$

이때 집합 $A_T$에서 부등식의 양 변이 모두 $T$에 대해 단조증가하는 형태이므로, $A_T$는 위의 두 집합 사이에 샌드위치 된다는 것을 알 수 있다. 따라서 $r(\overline{T}^N(x,y))$의 오차만 조절할 수 있다면, Step 1과 같은 논의를 할 수 있는 것이다. 물론 우리는 $r(\overline{T}^N(x,y))$의 분포를 알고 있으므로 (그리고 이는 $N$에 대해 불변이므로), 고정된 $\epsilon>0$에 대해 다음이 항상 성립하는 상수 $C$를 찾을 수 있다.

$$\mu(B_N) \ge 1-\epsilon \quad\text{ where }\quad B_N = \left\{ v(0)\in T^1X : r(\overline{T}^N(x,y)) \le C \right\}$$

이제 앞의 두 집합에서 $r(\overline{T}^N(x,y))$를 $C$로 고치면 $(2)$의 EVT를 적용할 수 있으므로, 이 뒤의 논의는 Step 1과 거의 같아진다.



## Step 2: $\max a_n$ to $\sup \exp(d(v(t),v(0)))$...?

마지막으로 문제가 많은 Step 2를 보자. 우리에게는 다음의 EVT가 주어져 있다.

$$\lim_{N\to\infty} \mu\left\{ x\in[0,1] : \max_{1\le n\le N} a_n \le \frac{6y}{\pi}T_N + o(N) \right\} = e^{-\frac{1}{y}}\tag{3}$$

그리고 이로부터 다음과 같은 EVT를 얻어내야 한다.

$$\lim_{N\to\infty} \mu\left\{ v(0)\in T^1 X : \sup_{0\le t\le T_N} \exp(d(v(t),v(0))) \le \frac{6y}{\pi}T_N \right\} = e^{-\frac{1}{y}} \tag{4}$$

앞의 논의와 같은 방법을 유지한다면, 우리에게 주어진 과제는 $\sup_{0\le t\le T_N}\exp(d(v(t),v(0)))$을 $o(N)$ (또는 $o(N)$ except on $\epsilon$-set)의 정확도로 $\max_{1\le n\le N}a_n$으로 근사하는 것이다.

그런데 이게 잘 안 된다. 일단, $\sup\exp(d(v(t),v(0)))$은  $\max a_n$이 아니라 $\max\frac{a_n}{2}$ 스케일이다. 앞의 geodesic excursion 그림을 다시 가져오자.

<embed src="/svg/clt-and-serious-gap-in-pollicott-evt/image02.svg" type="image/svg+xml" />

위 그림에서, geodesic의 $y$좌표의 최댓값은 원의 반지름에 해당하므로, 약 $\frac{a_n}{2}$이다. 그리고 $\exp(d(v(t),v(0)))$은 유클리드 거리와 비슷하므로, 곧 $\frac{a_n}{2}$와 비슷하다는 것을 알 수 있다. 따라서 사실 우리가 보일 EVT의 상수는 다음과 같이 수정되어야 한다.

$$\lim_{N\to\infty} \mu\left\{ v(0)\in T^1 X : \sup_{0\le t\le T_N} \exp(d(v(t),v(0))) \le \frac{3y}{\pi}T_N \right\} = e^{-\frac{1}{y}} \tag{4$'$}$$

이걸 수정하려면 지난 포스팅에서 Pollicott의 EVT를 사용하는 부분을 모두 수정해야 하겠지만... Sullivan의 asymptotic behavior를 증명할 때 문제가 되는 부분은 없으니 그대로 두도록 하자.

또 다른 문제도 생기는데, 이는 $\log \frac{a_n}{2}$는 $d(v(t),v(0))$이 아니라, $v(t)$와 $(i,i)$ 사이의 수직방향 거리만을 어림하는 것이기 때문이다. 따라서 총 세 군데의 오차가 발생하는데, (1) $(i,i)$와 $v(0)$ 사이의 거리, (2) $v(t)$와 $(i,i)$ 사이의 각도방향 거리, (3) $v(t)$와 $(i,i)$ 사이의 수평방향 거리의 오차가 생기게 된다.

그런데 우리는 (1) $(i,i)$와 $v(0)$ 사이의 거리를 만족스럽게 컨트롤할 수가 없다. 이는 $v(0)$가 $T^1X$ 전체에 분포할 수 있기 때문이다. $\epsilon$-set의 아이디어를 이용하여, $T^1X$의 compact subset을 잡고 그 안의 $v(0)$에 대해서만 논의를 진행해볼 수도 있을 것이다. 하지만 이 경우, 삼각부등식을 생각하면 $d(v(t),v(0))$의 어림에 $d(v(0),(i,i)) = O(1)$의 오차가 생기는데, 이는 $\exp(d(v(t),v(0)))$의 어림에서 $O(N)$의 오차가 되어 EVT를 적용할 수 없게 된다.

따라서 우리는 두 가지 중 하나를 선택해야 하는데, 하나는 각 $v(0)$마다 (오차항이 달라지므로) $T_N$ 앞에 붙는 상수를 다르게 선택하는 것이고, 다른 하나는 EVT를 $d(v(t),(i,i))$에 관한 식으로 고치는 것이다. 물론 전자는 더이상 EVT라고 볼 수 없으므로, 후자를 선택하면 이제 우리는 다음과 같은 EVT를 보여야 한다.

$$\lim_{N\to\infty} \mu\left\{ v(0)\in T^1 X : \sup_{0\le t\le T_N} \exp(d(v(t),(i,i))) \le \frac{3y}{\pi}T_N \right\} = e^{-\frac{1}{y}} \tag{4$''$}$$

이제 나머지 오차를 보자. 그런데 우리는 (2) $v(t)$와 $(i,i)$ 사이의 각도방향 거리 역시 만족스럽게 컨트롤할 수가 없다. 이는 마찬가지로 $v(t)$의 방향이 조금 틀어지면 $O(1)$의 거리 오차가 생겨서, $\exp(d(v(t),v(0)))$의 어림에서 $O(N)$의 오차로 이어지기 때문이다. 따라서 우리는 더이상 $T^1X$ 위의 distance $d$를 생각할 수 없고, $d$를 $X$ 위의 distance로 보아야 한다.

마지막 (3) $v(t)$와 $(i,i)$ 사이의 수평방향 거리의 오차는 다행히도 컨트롤이 가능하다. 삼각부등식을 생각하면, hyperbolic distance에서 $O(e^{-a_n/2})$의 오차가 생기게 된다. 이제 $\exp$를 취하면, $e^x \approx 1+x$이므로, $O(\frac{a_n}{2}(e^{e^{-a_n/2}}-1)) = O(a_ne^{-a_n/2})$의 오차가 생긴다. Galambos EVT를 이용하면 $a_n$이 $O(N)$보다 큰 영역의 measure를 $\epsilon$-set으로 제한할 수 있고, 나머지 영역에서는 오차가 $O(Ne^{-N/2}) = o(N)$이 되므로, EVT를 보일 수 있다.



## Re-stated Pollicott's EVT

앞의 증명을 종합하면, gap을 제거한 Pollicott의 EVT는 다음과 같이 state되어야 한다.

> $$\lim_{T\to\infty} \mu\left\{ v(0)\in T^1 X : \sup_{0\le t\le T} d(v(t),x) - \log T \le \log\frac{3y}{\pi} \right\} = e^{-\frac{1}{y}}\tag{5}$$
>
> 이때 $x=(i,i)\in T^1X$이고, $d$는 $X$ 위의 거리함수다.

위 수정된 정리를 이용해서 [지난 글]({{ site.baseurl }}/2021/03/06/evt-on-modular-surface/) 전체를 다시 적어야겠지만, Sullivan의 asymptotic behavior의 증명에서 문제가 되는 부분은 없으니 그대로 두기로 한다.



## References

[1] M. Pollicott, *Limiting distributions for geodesics excursions on the modular surface*, Contemporary Mathematics **14** (2009), 177-185.