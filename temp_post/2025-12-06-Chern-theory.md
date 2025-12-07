---
layout : post
title : 양자물리와 기하학_ 고차원 게이지 이론
image : "https://picsum.photos/700/300"
category : Physics and Mathematics
author : Me
---

지난 글에서는 Adiabatic theorem에서 등장하는 Berry phase와 그것의 기하학적 해석에 대해 살펴보았다. 이때, 2차원 매개변수의 공간에서의 적분이 정수로 표현되는 것을 보았다. 
이번 글에서는 더 일반적인 차원에서의 게이지 이론을 살펴보고, Chern 이론과의 관계를 알아보도록 하겠다.

## Degeneracay and Principal $U(k)$-bundle

Berry phase를 도입할 때의 상황을 돌이켜보자. 
원래의 가정은 임의의 $R \in \mathcal{M}$에 대해, $\mathcal{H}(R)$의 고유값이 discrete하고 non-degenerate하며, 각각이 $R$에 대해 연속적으로 변한다는 것이었다. 
이번에는 이 가정을 완화하여, $\mathcal{H}(R)$의 고유값이 모든 점에서 $k_n$-fold degeneracy를 가진다고 하자. 즉,

$$
\mathcal{H}(R) \psi_{n, \alpha}(R) = E_n(R) \psi_{n, \alpha}(R), \quad E_0(R) < E_1(R) < \cdots,\quad \alpha = 1, \ldots, k_n
$$

을 만족하는 $\mathcal{H}$의 $E_n$-고유공간의 정규직교기저 $\\{\psi_{n, \alpha}(R)\\}_{\alpha=1}^{k_n}$를 생각할 수 있다는 것이다. 다만, 모든 점에서 같은 degeneracy를 가진다는 것에 의문을 품을 수 있다. 만약 어떤 점에서 degeneracy가 달라진다면, 에너지도 연속적으로 변한다는 가정에 의해 반드시 에너지 간격이 좁은 영역이 존재하게 되고, 이 영역에서 adiabatic theorem가 성립하지 않게 된다. 따라서, adiabatic한 이론을 다루기 위해선 모든 점에서 같은 degeneracy를 가진다고 가정하는 것이 타당하다.

이전 글에서와 마찬가지로, $n$을 하나 고정시키고 $n$을 생략하여 생각할 수 있다. 즉, 어떤 $E$에 대응하는 고유공간이 모든 $R$에서 $k$-fold degeneracy를 가진다고 하자.

$$
\mathcal{H}(R) \psi_{\alpha}(R) = E(R) \psi_{\alpha}(R), \quad \alpha = 1, \ldots, k
$$

이 경우, 어떤 $g(R) \in U(k)$에 대해, $\psi'_{\alpha}(R) = \sum_{\beta=1}^k g_{\alpha \beta}(R) \psi_{\beta}(R)$ 또한 점 $R$에서의 $E(R)$-고유벡터가 된다. 즉, 실제 해는 다음 집합의 원소들 중 하나이다.

$$
    S_R = \{\phi \mid \mathcal{H}(R) \phi = E(R) \phi, \langle \phi, \phi \rangle = 1\}
$$

하나의 해 $\psi$에 대해, $g \in U(k)$가 주어졌을 때, $\psi' = g \psi$ 역시 해가 된다. 이를 non-degenerate한 경우와 마찬가지로 게이지 변환이라고 부를 수 있고, 게이지를 하나로 고정하는 것은 $U(k)$의 원소를 고르는 것과 같다. 따라서, 이제는 각 점에 $U(k)$가 붙어있는 공간을 생각해볼 수 있다. 이를 **$U(k)$-주다발(principal $U(k)$-bundle)**이라고 부른다. 다만, 이 경우 $U(1)$의 경우와는 달리, $S_R \cong S^{2k-1} \ncong U(k)$이고, 각 점에 파동함수를 대응시키는 것이 아니라 (군 구조가 잘 주어져 있는) 게이지 자체를 대응시키는 것으로밖에 생각할 수 없다는 점에 유의하자. 

$U(1)$-주다발과 비슷하게, 열린 집합 $U \subseteq \mathcal{M}$의 각 점에서 $h \in U(k)$를 고르는 단면을 생각해볼 수 있을것이며, 서로 다른 열린집합 $U_\alpha$, $U_\beta$ 위의 단면 $h_\alpha$, $h_\beta$ 사이의 관계는 다음과 같이 표현될 것이다.

$$
    h'_{\alpha}(R) = h_{\beta}(R) g_{\alpha \beta}(R), \quad g_{\alpha \beta}(R) \in U(k), \quad R \in U_\alpha \cap U_\beta
$$

$g_{\alpha \beta}$는 마찬가지로 전이 함수라고 부른다.

## Differential Geometry of $U(k)$-bundle

이제, $U(k)$-주다발 위의 접속(connection)을 생각해보자. $U(1)$-주다발의 경우와 마찬가지로, 열린집합 $U \subseteq \mathcal{M}$ 위의 단면 $h$에 대해 생각해야 할 것이다. 
어떤 $U$ 위의 단면 $h$가 주어져 있다고 하자. 그러면, 임의의 $U$ 위의 단면 $s$에 대해, 어떤 함수 $s^{(h)} : U \to U(k)$가 있어 다음과 같이 쓸 수 있다.

$$
    s = h s^{(h)}
$$

$U(1)$-주다발의 경우와 같이 $h$는 게이지를 고르는 일종의 좌표계 역할을 한다고 생각할 수 있다. 따라서, 다음과 같은 반변 규칙(contravariant rule)이 존재한다.

$$
    \begin{cases}
        h' = hg \\
        s^{(h')} = g^{-1} s^{(h)}
    \end{cases} 
$$

참고로, $U(k)$는 일반적으로 Abelian이 아니기 때문에, 이제부터는 순서를 신경써줘야 한다. 순서를 지켜 써서 명확히 볼 수 있는 것은, 물리학자들이 보는 *파동함수*는 실제로는 $U(k)$-주다발 위의 단면의 성분이라는 것이다. (게이지 변환이 왼쪽에 작용하는 곳이 파동함수이다.)

이제 본격적으로 접속에 대해 논의해보자. $U(k)$-주다발 위의 접속 $\nabla$는 다음과 같이 정의된다.

$$
    \nabla s = h \otimes ds^{(h)} + (\nabla h) s^{(h)}
$$

마찬가지로, 다음과 같은 접속 1-형식이 존재한다.

$$
    \nabla h = h \otimes \omega^{(h)}
$$

다른 기저 $h' = h g$의 접속 1-형식 $\omega^{(h')}$를 생각해보자.

$$
    \nabla h' = \nabla (h g) = h \otimes dg + h \otimes \omega^{(h)} g = h' \otimes (g^{-1} dg + g^{-1} \omega^{(h)} g)
$$

따라서,

$$
    \omega^{(h')} = g^{-1} dg + g^{-1} \omega^{(h)} g
$$

임을 알 수 있다. 참고로, $\omega^{(h)}$는 $U(k)$의 Lie 대수 $\mathfrak{u}(k)$ 성분을 가진 1-형식이다. $g = e^X$ ($X \in \mathfrak{u}(k)$) 꼴임을 생각하면, 얼추 그럴 것이라고 알 수 있다. 물론, $U(1)$ 게이지에서처럼 $g^{-1} dg$ 가 $dX$가 되지는 않는다.

접속 1-형식 $\omega^{(h)}$로부터 접속의 곡률(curvature)을 다음과 같이 정의할 수 있다.

$$
    \Omega^{(h)} = d\omega^{(h)} + \omega^{(h)} \wedge \omega^{(h)}
$$