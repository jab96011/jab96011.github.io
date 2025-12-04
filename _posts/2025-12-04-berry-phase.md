---
layout: post
title: 양자물리와 기하학_ Berry connection과 Chern number
image: "https://picsum.photos/700/300"
category: Physics and Mathematics
author: Me
---

응집물질을 다루는 논문을 읽다보면, 뜬금없이 기하학적인 개념인 접속(connection)이나 곡률(curvature) 등의 단어가 튀어나오는 경우가 종종 있다. 
다만, 이러한 개념들을 다루는 글은 너무 엉성하거나 수학적으로 너무 어려운 경우가 많아, 제대로 이해하기가 쉽지 않다.
그래서, 기말고사도 대비할 겸, 양자물리에서 등장하는 기하학적 개념들을 정리해보고자 한다.

## Geometric phase and Berry connection
이 절에서는 양자역학에서 기하학이 등장하게 되는 배경을 설명하고자 한다.
계를 기술하는 해밀토니안 $\mathcal{H}$가 어떤 $d$차원 매개변수 공간 $\mathcal{M} \cong \mathbb{R}^d$의 원소 $R$ 에 따라 달라지는 상황을 생각해보자.
이 $R$은 무엇이든 될 수 있다. 가령, 외부에서 가하는 자기장이 될 수도 있고, 고체물리에서 말하는 Bloch momentum이 될 수도 있다.

이제, 임의의 $R \in \mathcal{M}$에 대해, $\mathcal{H}(R)$의 고유값이 discrete하고 non-degenerate하며, 각각이 $R$에 대해 연속적으로 변한다고 가정하자.
그렇다면, 다음과 같이 고윳값과 그에 대한 orthonormal한 고유벡터를 정의할 수 있다.

$$
\mathcal{H}(R) \psi_n(R) = E_n(R) \psi_n(R), \quad E_0(R) < E_1(R) < \cdots
$$

꽤나 복잡한 계산을 통해 다음 정리를 증명할 수 있다.

> **Theorem 1. (Adiabatic Theorem)**
> $\mathcal{M}$ 위의 곡선 $R : [0, T] \to \mathcal{M}$을 생각하자. 
> 위에서 정의한 해밀토니안과 고윳값, 고유벡터에 대해, 다음을 생각해보자.
> 
> $$
> {\tilde{\mathcal{H}}}(t) := \mathcal{H}(R(t)),\quad {\tilde{\psi}}_n(t) := \psi_n(R(t)),\quad \tilde{E}_n(t) := E_n(R(t))
> $$
>
> 이때, 초깃값이 $\Psi(0) = \tilde{\psi}_n(0)$인 파동함수 $\Psi(t)$가 다음 Schrödinger 방정식을 만족한다고 하자.
>
> $$
> i \hbar \frac{d}{dt} \Psi(t) = {\tilde{\mathcal{H}}}(t) \Psi(t)
> $$
>
> 만약, $\|\dot{R}\|$가 $\Delta/\hbar$에 비해 충분히 작다면 ($\Delta$는 고윳값 간의 간격), $\Psi(t)$는 다음과 같이 근사될 수 있다.
> 
> $$
> \Psi(t) \simeq \exp\left( -\frac{i}{\hbar} \int_0^t \tilde{E}_n(t') dt' \right) \exp\left( i {\gamma}_n(t) \right) \tilde{\psi}_n(t)
> $$ 
>
> 여기서, $\gamma_n(t)$는 다음과 같이 정의된다.
> 
> $$
> \gamma_n(t) := i \int_0^t \langle {\tilde{\psi}}_n(t') | \frac{d}{dt'} |{\tilde{\psi}}_n(t') \rangle dt' = i \int_0^t \langle \dot{\tilde{\psi}}_n(t'), {\tilde{\psi}}_n(t') \rangle dt'
> $$

Adiabatic theorem은 매개변수 $R$이 천천히 변할 때, $n$번째 고유상태는 $n$번째 고유상태에 머문다는 것을 말해준다. 물론, 그 위상은 변화할 수 있고, 크게 두 부분으로 나눌 수 있다.
하나는 **동적 위상(dynamic phase)**으로, 각 점에서의 에너지가 주는 위상 변화이다.

$$
    \theta_n(t) = -\frac{1}{\hbar} \int_0^t E_n(R(t')) dt'
$$

다른 하나는 **기하학적 위상(geometric phase)**이라 부른다.

$$
    \gamma_n(t) := i \int_0^t \langle {\tilde{\psi}}_n(t') | \frac{d}{dt'} |{\tilde{\psi}}_n(t') \rangle dt' = i \int_0^t \langle \dot{\tilde{\psi}}_n(t'), {\tilde{\psi}}_n(t') \rangle dt'
$$

그런데, 처음의 정의로부터 $\dot{\tilde{\psi}}_n(t)$에 연쇄 법칙을 적용하면 다음과 같이 쓸 수 있다.  
(Einstein summation convention 사용, $\partial_i := \partial / \partial R^i$)

$$
    \frac{d}{dt}{\tilde{\psi}}_n(t) = \nabla_R {\psi}_n(R(t)) \cdot \dot{R}(t) = \partial_i {\psi}_n(R(t)) \dot{R}^i(t)
$$

따라서, 기하학적 위상은 다음과 같이 쓸 수 있다.

$$
    \gamma_n(t) = i \int_0^t \langle \partial_i {\psi}_n(R(t')) , {\psi}_n(R(t')) \rangle \cdot \dot{R}(t') dt' = \int_C i \langle \partial_i {\psi}_n(R) , {\psi}_n(R) \rangle dR^{i}
$$

여기서, $C$는 시작점 $R(0)$에서 끝점 $R(t)$까지의 매개변수 공간 $\mathcal{M}$ 위의 곡선이다.
다시 말해, 기하학적 위상은 매개변수 공간 위의 곡선 $C$의 매개화에 상관없이 그 형태에만 영향을 받는다.

이때, 위의 적분에서 등장하는 1-형식

$$
    A_n := i \langle \partial_i \psi_n(R) , \psi_n(R) \rangle dR^{i}
$$

을 **Berry 접속(Berry connection)**이라 부른다.

> **Remark 2.** 
> $\langle \psi_n(R) , \psi_n(R) \rangle \equiv 1$이므로, 
>
> $$
> i\langle \partial_i \psi_n(R) , \psi_n(R) \rangle + i\langle \psi_n(R) , \partial_i \psi_n(R) \rangle = 0
> $$
> 
> 이다. 그런데, 좌변은 $(A_n)_i - \overline{(A_n)_i}$이므로, $A_n$이 허수가 되는 걱정을 할 필요는 없다.

이제, 매개변수 공간 $\mathcal{M}$ 위의 닫힌 곡선 $C$를 생각해보자. 이때, 다음과 같이 Stokes 정리를 적용할 수 있다.

$$
    \gamma_n(C) = \oint_C A_n = \int_S dA_n
$$

여기서, $S$는 $C$를 경계로 가지는 $\mathcal{M}$ 위의 임의의 곡면이다.
이때, 2-형식 $\Omega_n := dA_n$를 **Berry 곡률(Berry curvature)**이라 부른다.

## Gauge transformation and Chern number

가장 처음 상황으로 돌아가보자.
해밀토니안 $\mathcal{H}(R)$의 고유벡터 $\psi_n(R)$는 유일하지 않다.
임의의 $R$에 대해, 다음과 같이 위상 인자를 곱해도 여전히 고유벡터가 된다.

$$
    \psi_n(R) \mapsto e^{-i \Lambda(R)} \psi_n(R), \quad \Lambda : \mathcal{M} \to \mathbb{R}
$$

이러한 변환을 **국소 게이지 변환(local gauge transformation)**이라 부른다.

이 상황을 조금 다른 관점에서도 생각해볼 수 있다. 
각 점에 $\psi_n(R)$을 대응시키는 대신, $\psi_n(R)$이 속한 1차원 복소 벡터 공간 $\text{span}_{\mathbb{C}}\\{\psi_n(R)\\}$을 대응시키는 것이다. 이를 **복소 선다발(complex line bundle)**이라 부른다. 파동함수 $\psi_n(R)$는 이 선다발의 국소적 단면(section)으로 생각할 수 있다.

이때, Berry 접속 $A_n$는 다음과 같이 변환된다.

$$
    A_n \mapsto i \langle \partial_i (e^{-i \Lambda(R)} \psi_n(R)) , e^{-i \Lambda(R)} \psi_n(R) \rangle dR^{i} = A_n + d\Lambda
$$

따라서, Berry 곡률 $\Omega_n$은 게이지 불변량이다. ($d^2 = 0$이므로)

