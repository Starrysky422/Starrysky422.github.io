---
layout: post
title: Relationship between Continued Fraction and Modular Surface
comments: true
tags: 
- Ergodic Theory
- Continued Fraction
---

Modular surface의 geodesic flow와 연분수 사이의 연관성은 ergodic theory의 가장 기초적인 내용 중 하나이다. 이들 사이의 연관은 동역학과 정수론 사이의 연결고리를 제공한다.

이 글을 포함한 모든 포스트에서, 대부분의 내용은 별다른 명시가 없더라도 almost everywhere sense로 이해한다.



## Continued Fraction

우선 연분수에 관해 살펴보자. 연분수는 흔히 알고 있는 그 연분수를 이야기 한다. 보통 다음과 같은 표기법을 사용한다.

$$[a_0;a_1,a_2,a_3,\dots] = a_0+\dfrac{1}{a_1+\dfrac{1}{a_2+\dfrac{1}{\ddots}}}$$

그리고 일반적으로 $x\in [0,1]$의 연분수 표기를 쓸 일이 많으니, $a_0(=0)$를 생략하여 $[a_1, a_2, \dots]$로도 많이 쓴다.

연분수는 다음과 같이 정의되는 **Gauss map** $T:[0,1]\to[0,1]$를 이용해서 구성할 수 있다.

$$T(x) = \frac{1}{x} - \left\lfloor \frac{1}{x} \right\rfloor$$

이때 $T$는 다음의 Gauss measure $\mu$를 보존한다.

$$\mu(A) = \frac{1}{\log 2} \int_A \frac{dx}{1+x}$$

Gauss map은 one-sided shift처럼 볼 수 있다. 즉, $x\in[0,1]$의 연분수 전개가 $[a_1,a_2,\dots]$이면 $Tx$의 연분수 전개는 $[a_2, a_3, \dots]$가 된다. 따라서 $a_n(x) = \lfloor \frac{1}{T^{n-1}x} \rfloor$와 같이도 쓸 수 있다. 한편 $Tx$에는 $a_1$의 정보가 남아있지 않으므로 정보의 손실이 발생한다. 보통 measure-preserving transformation(이하 m.p.t.)을 다룰 때는 일대일대응인 편이 좋기 때문에, 다음과 같은 invertible extension $\overline{T}:[0,1]^2\to[0,1]^2$을 생각한다.

$$\overline{T}(x,y) = \left( Tx, \frac{1}{\lfloor\tfrac{1}{x}\rfloor + y} \right)$$

이는 다음과 같이 two-sided shift처럼 볼 수 있으므로, 정보의 손실이 일어나지 않는다.

$$\overline{T}([a_1,a_2,a_3,\dots],[b_1,b_2,b_3,\dots]) = \left( [a_2,a_3,a_4,\dots], [a_1,b_1,b_2,\dots] \right)$$

이 extension 역시 Gauss map이라고 부른다.



## Möbius Transformation and Modular Surface

Hyperbolic surface $\mathbb{H}$ 위에 möbius 변환으로 $SL_2(\mathbb{R})$-action(또는 $PSL_2(\mathbb{R})$-action)을 정의하자.

$$\begin{pmatrix} a&b \\ c&d \end{pmatrix} : z \mapsto \frac{az+b}{cz+d}$$

이는 isometric action이 되므로, tangent bundle $T\mathbb{H}$ 위의 action을 induce한다. 따라서 $SL_2(\mathbb{R})$의 discrete subgroup $\Gamma$에 대해, quotient space $X = \mathbb{H}/\Gamma$와 그 tangent bundle $TX = T\mathbb{H}/\Gamma$가 잘 정의된다. 특히 $\Gamma = SL_2(\mathbb{Z})$에 대해, $X = \mathbb{H}/\Gamma$를 modular surface라고 하며, 보통 다음과 같은 fundamental domain을 생각하게 된다.

$$F = \left\{ z \in \mathbb{H} : -\frac{1}{2} \le \Re(z) \le \frac{1}{2},\ \lvert{z}\rvert \ge 1 \right\}$$

<embed src="/svg/relationship-between-continued-fraction-and-modular-surface/image01.svg" type="image/svg+xml" />

그런데 왜 modular surface를 생각하는 것일까? Gauss map을 살펴보면, 우리는 결국 두 가지 연산 '$x\mapsto \frac{1}{x}$'와 '$x\mapsto x-\lfloor x\rfloor$'를 사용함을 알 수 있다. 이때 $\sigma=\big(\begin{smallmatrix}0&-1\\\\1&0\end{smallmatrix}\big), \tau=\big(\begin{smallmatrix}1&1\\\\0&1\end{smallmatrix}\big) \in SL_2(\mathbb{Z})$이 각각 $x\mapsto -\frac{1}{x}$, $x\mapsto x+1$으로 작용함을 고려하면 (그리고 더 나아가 $SL_2(\mathbb{Z}) = \langle \sigma,\tau \rangle$임을 보면) modular surface $\mathbb{H}/SL_2(\mathbb{Z})$를 생각하는 것이 어느정도 자연스러울 것이다. 앞의 fundamental domain의 세 '변' 중 아래의 원호는 $\sigma$에, 옆의 두 수직선은 $\tau$에 대응됨에 주목하자.

그런데 Gauss map의 연산은 $x\mapsto \frac{1}{x}$인 반면, $\sigma$는 $x\mapsto -\frac{1}{x}$에 대응된다는 점이 조금 찝찝하다. 이 차이 때문에 Gauss map은 사실 $SL_2(\mathbb{Z})$-action으로 완전히 나타낼 수가 없고, 정확히 이 부호만큼의 차이가 생긴다. 그러니 이 부호를 붙여서, Gauss map의 invertible extension $\overline{T}:[0,1]^2\times(\mathbb{Z}/2\mathbb{Z})\to [0,1]^2\times(\mathbb{Z}/2\mathbb{Z})$를 재정의하자.

$$\overline{T}(x,y,\epsilon) = \left( Tx, \frac{1}{\lfloor\tfrac{1}{x}\rfloor + y}, 1-\epsilon \right)$$

앞으로 $Y = [0,1]^2\times(\mathbb{Z}/2\mathbb{Z})$로 쓰자.



## Geodesic Coding

이제 modular surface 위의 geodesic을 어떤 문자열에 대응할 것이다. Fundamental domain의 copy들로 $\mathbb{H}$를 타일링 한 뒤, geodesic과 교차하는 domain의 변들이 각각 $\sigma,\tau$ 중 무엇에 대응되는지를 차례대로 기록하자. (이때 geodesic이 domain의 꼭짓점을 지나는 등의 경우는 '거의 없으므로' 무시해도 된다.) 이와 같은 대응을 **geodesic coding**이라고 한다.

$\mathbb{H}$의 geodesic은 (upper half-plane model 기준으로) 수직선, 또는 밑변에 수직한 반원이다. 수직선인 경우는 거의 없으므로 무시하고, 반원만을 생각하자. Modular surface의 geodesic $\gamma$에 대해, 그 lift $\tilde{\gamma}$를 생각한다. 특히, 이러한 lift 중 $\tilde{\gamma}(+\infty)$, $\tilde{\gamma}(-\infty)$가 하나는 $[-1,0]$에, 다른 하나는 $[1,\infty)$에 들어가도록 고를 수 있다. 이때 $[-1,0]$에 속한 것을 $-y$, $[1,\infty)$에 속한 것을 $\frac{1}{x}$로 쓰자. 그리고 $\epsilon\in\mathbb{Z}/2\mathbb{Z}$를 $\tilde{\gamma}(+\infty) = -y$면 $0$, $\tilde{\gamma}(+\infty) = \frac{1}{x}$면 $1$로 정해주자. 그러면 이 lift $\tilde{\gamma}$를 $(x,y,\epsilon)\in[0,1]^2\times Y = (\mathbb{Z}/2\mathbb{Z})$에 대응시킬 수 있다.

<embed src="/svg/relationship-between-continued-fraction-and-modular-surface/image02.svg" type="image/svg+xml" />

이 geodesic이 굵게 표시한 '$\sigma$변' 위에서 '$\tau$변'과 만나는 횟수를 보면, $\tau$변들이 $1$씩 거리를 두고 위치해 있으므로 정확히 $\lfloor{\frac{1}{x}}\rfloor = a_1(x)$번이라는 것을 관찰할 수 있다. 즉, geodesic coding으로 얻어지는 문자열을 보면, 두 $\sigma$ 사이에 $\tau$가 $a_1(x)$번 나타나는 것이다.

그 다음에 나타나는 $\tau$는 몇 번일까? $\epsilon = 0$인 경우만 보자. ($\epsilon = 1$인 경우는 대칭적이다.) $\tilde{\gamma}$를 $-\lfloor\frac{1}{x}\rfloor$만큼 평행이동한 뒤, $\sigma$를 취해서 뒤집어주면, $\sigma$변 위에 위치한 부분이 그 다음의 $\tau$들에 해당할 것이다. 이때 이 geodesic의 두 끝점은 $+\infty$에서 $-\frac{1}{Tx}$, $-\infty$에서 $\frac{1}{\lfloor\frac{1}{x}\rfloor + y}$가 된다. 즉, 이 geodesic은 $(Tx, \frac{1}{\lfloor\frac{1}{x}\rfloor + y}, 1-\epsilon) = \overline{T}(x,y,\epsilon)$에 해당되는 것이다. 마찬가지로 하면, $n$번째 단계에서 두 $\sigma$ 사이에 위치한 $\tau$의 개수는 $a_1(T^{n-1}x) = a_n(x)$개임을 알 수 있다.



## Special Flow

Geodesic coding을 통해 modular surface의 geodesic과 연분수 사이의 연관을 찾았다. 이를 geodesic flow와도 연결지어 보자. 앞의 geodesic $\tilde{\gamma}$가 두 $\sigma$변 사이에서 머무는 시간을 'return-time function' $r(x,y)$로 정의하자. 이제 다음과 같이, $Y\times\mathbb{R}$에 동치관계를 준 공간 $Y_r$을 생각하자.

$$Y_r = Y\times\mathbb{R} \big/ \big((x,y,\epsilon),s) \sim (\overline{T}(x,y,\epsilon),s-r(x,y)\big)$$

이 위에서 flow $\psi_t:Y_r \to Y_r$을 자명하게 다음과 같이 정의하자.

$$\psi_t((x,y,\epsilon),s) = ((x,y,\epsilon),s+t)$$

<embed src="/svg/relationship-between-continued-fraction-and-modular-surface/image03.svg" type="image/svg+xml" />

이렇게 정의한 flow $\psi_t$를 transformation $\overline{T}$와 suspension function $r$로부터 생성된 **special flow**라고 한다.

그런데 $r(x,y)$는 두 $\sigma$변 사이의 geodesic segment의 길이로 정의했고, 다음 geodesic segment는 $\overline{T}(x,y,\epsilon)$으로 정의했으니, 이 special flow는 modular surface 위의 geodesic flow와 동형이라는 것을 알 수 있다.



## Choice of Suspension Function

앞에서 정한 suspension function $r(x,y)$는 geodesic segment의 길이로 정의되어서 계산하기가 어렵다. $r(x,y)$를 다른 함수로 바꿀 수 있을까?

어떤 함수 $g:Y\to\mathbb{R}$에 대해서, $f(x,y,\epsilon) = g(\overline{T}(x,y,\epsilon)) - g(x,y,\epsilon)$을 만족하면 $f:Y\to\mathbb{R}$을 **coboundary**라고 한다. 그리고 두 suspension function이 coboundary만큼 차이가 난다면, 즉 **cohomologous**하다면 두 special flow는 서로 동형이다. 그런데 return-time function $r(x,y)$는 $-2\log x$와 cohomologous하다는 것이 알려져 있다. (이 내용은 기회가 된다면 추후 포스트에서 다룰 예정이다) 이제 $r(x,y) = -2\log x$로 재정의하면, 연분수로부터 modular surface의 geodesic flow와 동형인 special flow를 만들 수 있다.



## References

[1] M. Einsiedler and T. Ward, *Ergodic theory*, Springer London Limited, 2013.

[2] M. Pollicott, *Limiting distributions for geodesics excursions on the modular surface*, Contemporary Mathematics **14** (2009), 177-185.