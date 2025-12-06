---
layout: post
title: 양자물리와 기하학_ Berry connection과 Chern number
image: "https://picsum.photos/700/300"
category: Physics and Mathematics
author: Me
---

응집물질을 다루는 논문을 읽다보면, 뜬금없이 기하학적인 개념인 접속(connection)이나 곡률(curvature) 등의 단어가 튀어나오는 경우가 종종 있다. 
다만, 이러한 개념들을 다루는 글은 너무 엉성하거나 물리적인 motivation 없이 순수 수학으로만 설명된 경우가 많아, 제대로 이해하기가 쉽지 않다.
그래서, 이번 글에서는 Berry phase, Berry connection, Chern number 등의 개념이 양자역학에서 어떻게 등장하는지, 그리고 그것들이 미분기하학의 어떤 개념과 연결되는지를 소개하고자 한다.

## Geometric phase and Berry connection
이 절에서는 양자역학에서 기하학이 등장하게 되는 배경을 설명하고자 한다.
계를 기술하는 해밀토니안 $\mathcal{H}$가 어떤 $d$차원 매개변수 다양체 $\mathcal{M}$의 원소 $R$ 에 따라 달라지는 상황을 생각해보자.
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
이때, 2-형식 $F_n := dA_n$를 **Berry 곡률(Berry curvature)**이라 부른다.
다만, 이들이 왜 접속과 곡률이라 불리는지는 아직 명확하지 않다. 

## Gauge transformation and principal bundle

가장 처음 상황으로 돌아가보자. 
이제부터는 어떤 $n$을 하나 고정하여 생각해볼 것이다. 
$n$번째 고유벡터 $\psi_n(R)$을 간단히 $\psi(R)$이라 쓰자. 
즉, 어떤 고정된 $n$에 대해 다음을 만족하는 $\psi(R)$를 생각하는 것이다.

$$
    \mathcal{H}(R) \psi(R) = E_n(R) \psi(R)
$$

하지만, 이를 만족하는 $\psi(R)$는 유일하지 않다.
임의의 $R$에 대해, 다음과 같이 위상 인자를 곱해도 여전히 고유벡터가 된다.

$$
    \psi(R) \mapsto e^{-i \Lambda(R)} \psi(R), \quad \Lambda : \mathcal{M} \to \mathbb{R}
$$

이러한 변환을 **국소 게이지 변환(local gauge transformation)**이라 부른다.


이때, Berry 접속 $A$는 다음과 같이 변환된다.

$$
    A \mapsto i \langle \partial_i (e^{-i \Lambda(R)} \psi(R)) , e^{-i \Lambda(R)} \psi(R) \rangle dR^{i} = A + d\Lambda
$$

또한, Berry 곡률 $F$는 다음과 같이 변환된다.

$$
    F \mapsto dA + d(d\Lambda) = F
$$

즉, $F$는 게이지 불변(gauge invariant)이라고 말할 수 있다.

위에서 언급했듯, 게이지 변환된 파동함수 역시 각 점에서의 해밀토니안의 고유벡터이므로 이제부터는 게이지 변환에 불변인 구조를 살펴보고자 한다.

각 점에 $\psi(R)$을 대응시키는 대신, 해밀토니안의 $E_n(R)$ 의 고유벡터 중 단위벡터를 모두 모은 집합을 대응시키는 것을 생각해보자.
즉, 다음과 같은 집합을 생각하는 것이다.

$$
    S_R := \{ \phi \mid \mathcal{H}(R) \phi = E_n(R) \phi, \langle \phi, \phi \rangle = 1 \}
$$

이는 근본적으로 어떤 해 $\psi(R)$의 게이지 변환 $e^{i \Lambda(R)} \psi(R)$을 모두 모은 집합이고, 그 자체로 

$$
    U(1) = \{ e^{i \theta} \mid \theta \in \mathbb{R} \}
$$

 과 동형이다. 다시 말해, 문제 상황은 각 점에 $U(1)$-모양의 공간을 대응시키는 상황으로 바뀌었다. 이를 **$U(1)$-주다발(principal $U(1)$-bundle)**이라 부른다.

각 점에서 $U(1)$의 원소를 선택하는 것을 생각해보자. 이를 **단면(section)**이라 부른다.
이 단면은 각 점에서 해밀토니안의 고유벡터 중 하나를 선택하는 것과 같다. 즉, 게이지 중 하나를 고르는 것이다.
하지만, 이렇게 뽑은 $\psi(R)$에 대해서 미분 등의 연산을 자유롭게 하기 위해서는 선택하는 영역이 열린 집합이어야 한다. 따라서, $\mathcal{M}$의 열린집합 $U \subseteq \mathcal{M}$ 위에서 단면 $\psi$를 선택하는 것을 생각해보자.

만약 단면 $\psi$를 열린 집합 $U$ 위에서 선택했다면, $U$ 위의 임의의 단면 $s$는 어떤 함수 $s^{(\psi)} : U \to U(1)$에 대해 다음과 같이 쓸 수 있다.

$$
    s = s^{(\psi)}\psi
$$

이는 게이지를 하나 고르는 것은 $U \times U(1)$ 위의 좌표계 $(R, s^{(\psi)}(R))$를 고르는 것과 같다는 것을 의미한다. 따라서, 다음과 같은 반변 규칙(contravariant rule)이 존재한다.

$$
    \begin{cases}
    \psi \mapsto \psi' = e^{-i \Lambda} \psi
    \\
    s^{(\psi)} \mapsto s^{(\psi')} = e^{i \Lambda} s^{(\psi)}    
    \end{cases}
$$

하지만, 많은 다양체는 하나의 열린집합으로 덮을 수 없다 (구면 $S^2$ 혹은 토러스 $T^2$에서조차 불가능하다).
따라서, 여러 열린집합 $U_{\alpha}$의 묶음 $\\{U_{\alpha}\\}$으로 $\mathcal{M}$을 덮는 것을 생각해보자. 
각 열린집합 $U_{\alpha}$ 위에서 단면 $\psi_{\alpha}$를 선택한다 하면, 두 영역 $U_{\alpha}, U_{\beta}$의 교집합 $U_{\alpha} \cap U_{\beta}$ 위에는 서로 다른 두 단면 $\psi_{\alpha}, \psi_{\beta}$가 존재한다. $U_{\alpha}$에서 $U_{\beta}$로 넘어가는 미분구조를 생각하고 싶은데, 두 단면이 $U_{\alpha} \cap U_{\beta}$ 위에서 서로 같지 않을 수 있다. 
하지만, 근본적으로 두 단면 모두 같은 고유벡터 공간에서 온 것이므로, 다음과 같이 서로 다른 단면들이 어떻게 연결되는지 나타내는 함수를 정의할 수 있다.

$$
    \psi_{\beta} = e^{-i \Lambda_{\alpha \beta}} \psi_{\alpha} \quad \text{on } U_{\alpha} \cap U_{\beta}
$$

이러한 함수 $g_{\alpha \beta} := e^{-i \Lambda_{\alpha \beta}} : U_{\alpha} \cap U_{\beta} \to U(1)$를 **전이 함수(transition function)**라 부른다.

이 전이 함수는 주다발이라는 공간의 구조를 담고 있다.
만약, 전이 함수가 모두 항등함수라면, 즉, $\Lambda_{\alpha \beta} \equiv 0$이라면, 모든 단면들이 서로 일치하므로, $\mathcal{M} \times U(1)$과 동형이다.
하지만, 꼭 그렇지 않은 경우도 존재하며, 이러한 경우를 **비자명 주다발(non-trivial principal bundle)**이라 부른다.

다만, 실제로 물리적인 상황에서 주다발의 구조를 완전히 파악하는 것은 쉽지 않다.
다음 절에서는 주다발의 구조를 파악하는 도구로써 접속과 곡률을 소개하고자 한다.

## Connection and curvature on principal bundle

서로 다른 점에 붙은 $U(1)$은 독립된 공간이기 때문에, 두 점에 붙어 있는 $U(1)$의 원소를 직접 비교하는 것은 불가능하다. 
따라서, 한 점에 붙어있는 원소를 다른 점에 붙어있는 공간으로 옮길 때 어떻게 변하는지를 알려주는 구조가 필요하다. 이를 통상적으로 접속(connection)이라 부른다.

$U \cong \mathbb{R}^d$인 $\mathcal{M}$의 열린집합을 생각하자. 이때, $U \times U(1)$ 위에서는, 다음 두 조건을 만족하는 **접속 (connection)** $\nabla$을 정의할 수 있다.

$$
    \begin{cases}
        \nabla s = ds^{(\psi)} \otimes \psi + s^{(\psi)} \nabla \psi
        \\
        \nabla (s + t) = \nabla s + \nabla t
    \end{cases}
$$

여기서, 기저의 접속 $\nabla \psi$이 공간의 구조를 담는다. 그 형태가 어떤지는 몰라도, 이 또한 $U(1) \times T^*\mathcal{M}$의 원소이므로, 다음과 같이 쓸 수 있다.

$$
    \nabla \psi = \omega^{(\psi)} \otimes \psi
$$

이때 $\omega^{(\psi)}$를 ($\psi$에 대한) **접속 1-형식(connection 1-form)**이라 부른다. (리만 기하학에서 Christoffel 기호라고 부르는 것이 이 접속 1-형식의 성분이다.)

이제 다른 기저 $\psi' = e^{-i \Lambda} \psi$의 접속 1-형식 $\omega^{(\psi')}$를 생각해보자.

$$
    \nabla \psi' = \nabla (e^{-i \Lambda} \psi) = -ie^{-i \Lambda} d\Lambda \otimes \psi + \omega^{(\psi)} \otimes e^{-i \Lambda} \psi = (\omega^{(\psi)} - i d\Lambda) \otimes \psi'
$$

따라서, 

$$
    \omega^{(\psi')} = \omega^{(\psi)} - i d\Lambda
$$

을 만족해야 한다. 그런데, 앞에서 본 Berry 접속 $A$에 대해, $\psi$에 대한 접속 1-형식을 $\omega^{(\psi)} = -i A$로 정의하면, 위의 변환 법칙과 일치한다. 다시 말해, Berry 접속은 정말로 $U(1)$-주다발 위의 접속이다.

만약, $U$ 위에 접속이 주어지면, $U$ 위에서 이 접속의 곡률 2-형식(curvature 2-form)을 다음과 같이 정의할 수 있다.

$$
    \Omega^{(\psi)} := d\omega^{(\psi)} + \omega^{(\psi)} \wedge \omega^{(\psi)} = d\omega^{(\psi)}
$$

그런데, 앞에서 보았듯이, $\Omega^{(\psi)}$는 게이지 불변이다. 즉, $U$ 위의 임의의 단면 $\psi, \psi'$에 대해,
$$
    \Omega^{(\psi')} = \Omega^{(\psi)}
$$
이다. 따라서, $\Omega^{(\psi)}$를 단순히 $\Omega$라 쓰기로 하자. 이제, 앞에서 정의한 Berry 곡률 $F = dA$와 다음과 같이 연결된다.

$$
    \Omega = d\omega^{(\psi)} = -i dA = -i F
$$