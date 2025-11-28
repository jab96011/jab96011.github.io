---
layout: post
title: [Probability Theory] 측도와 확률공간
image: "https://picsum.photos/700/300"
category: Physics and Mathematics
author: Me
---

항상 확률변수에 관한 이론을 접할때면, 이것이 고등학교때 배웠던 직관적인 개념과 연결되지 않는 느낌을 받는다. 
특히나, 수학에서 확률론이라 부르는 분야는 그 motivation에서 더 멀어진 느낌이 들곤 한다. 
이 글에서는 *엄밀한* 확률론의 기초 개념을 보며 이해한 나의 생각을 정리해보고자 한다.

## Why measure?
확률이란 무엇일까? 
고등학교에서는 확률을 어떤 사건이 일어날 경우의 수를 전체 경우의 수로 나눈 값으로 정의했다.
예를 들어, 빨, 주, 노, 초, 파 색깔의 공이 각각 20개씩 들어있는 상자에서 공 하나를 무작위로 뽑는 실험을 생각해보자.
이 실험에서, 빨간색 공을 뽑을 확률은 20/100 = 1/5 이다.

이를 추상화해보면,
어떤 전체 집합이 있고 그 안의 어떤 사건을 유발하는 부분집합을 뽑을 확률을 생각할 수 있다.
다만, 전체 집합의 크기에 대한 부분집합의 크기의 비라는 확률을 정의하기 위해서는 전체 집합의 크기와 부분집합의 크기를 정의할 수 있어야 한다.
즉, 집합은 *크기를 잴 수 있어야 한다*.

이를 위해, 수학에서는 집합에 측도(measure)라는 개념을 도입한다.
집합 $\Omega$에 대해, 어떤 부분집합의 모임 $\mathcal{F} \subseteq \mathcal{P}(\Omega)$이 있어, $\mathcal{F}$의 모든 원소의 크기를 어떤 함수 $\mu$로 잴 수 있다고 하자. 
수학자들이 늘 하는 일은, 이 $\mathcal{F}$와 $\mu$가 최소한 만족해야 할 조건들을 정하는 것이다.

> **Definition.** 어떤 집합 $\Omega$에 대해, $\mathcal{F} \subseteq \mathcal{P}(\Omega)$가 다음 조건을 만족한다고 하자.
> 1. $\varnothing \in \mathcal{F}$
> 2. $A \in \mathcal{F} \implies  \Omega \setminus A \in \mathcal{F}$
> 3. $\mathcal{F}$ 이 $\cup$에 대해 닫혀있다.
> 
> 이때, $\mathcal{F}$를 $\Omega$ 위의 $\sigma$-대수($\sigma$-algebra)라 부르고, $\mathcal{F}$의 원소를 가측 집합(measurable set)이라 부르며, $(\Omega, \mathcal{F})$를 가측 공간(measurable space)라 부른다.

> **Definition.** 어떤 가측 공간 $(\Omega, \mathcal{F})$에 대해, 함수 $\mu : \mathcal{F} \to [0, \infty]$가 다음 조건을 만족한다고 하자.
> 1. $\mu(\varnothing) = 0$
> 2. 서로소인 가측 집합들의 열 $\{A_i\}_{i=1}^{\infty} \subseteq \mathcal{F}$에 대해,
> $$
> \mu\left( \bigcup_{i=1}^{\infty} A_i \right) = \sum_{i=1}^{\infty} \mu(A_i)
> $$
> 이때, $\mu$를 측도(measure)라 부르고, $(\Omega, \mathcal{F}, \mu)$를 측도 공간(measure space)라 부른다.

> **Example.** 어떤 유한 집합 $\Omega$에 대해, $\mathcal{F} = \mathcal{P}(\Omega)$, $\mu(A) = |A|$로 정의하자.
> 이때, $(\Omega, \mathcal{F}, \mu)$는 측도 공간이다. 

늘상 그렇듯이, 위의 정의들로부터 직관적으로 크기를 재는 함수로써의 측도가 만족해야 할 몇 가지 성질들을 유도할 수 있다.
> **Proposition.** 어떤 측도 공간 $(\Omega, \mathcal{F}, \mu)$에 대해, 다음이 성립한다.
> 1. $A, B \in \mathcal{F}$이고 $A \subseteq B$이면, $\mu(A) \leq \mu(B)$
> 2. $A, B \in \mathcal{F}$이면, $\mu(A \cup B) + \mu(A \cap B) = \mu(A) + \mu(B)$

> **Definition.** 어떤 위상 공간 $(\Omega, \mathcal{T})$에 대해, $\mathcal{T}$를 포함하는 가장 작은 $\sigma$-대수 $\mathcal{B}(\Omega)$를 $\Omega$의 Borel $\sigma$-대수(Borel $\sigma$-algebra)라 부른다.

## Probability space and random variables
만약, 전체 공간의 크기가 1이 되도록 하는 측도를 생각하면 이 공간의 부분집합의 크기는 그 자체로 전체 공간의 크기에 대한 비율이 되고 이를 확률로 생각할 수 있다.

> **Definition.** 어떤 측도 공간 $(\Omega, \mathcal{F}, \mu = \mathbb{P})$에 대해, $\mathbb{P}(\Omega) = 1$이라면, 이를 확률 공간(probability space)이라 부르고, $\mathbb{P}$를 확률 측도(probability measure)라 하고 $\Omega$의 원소를 표본 공간(sample space)이라 하며, $\mathcal{F}$의 원소를 사건(event)이라 부른다.

이제 다시 처음의 예시로 돌아가보자. 
상자에서 공 하나를 무작위로 뽑는 실험에서, 표본 공간 $\Omega$는 상자 안의 100개의 공으로 이루어진 집합이다.
이 공에 각각 번호를 붙여 $\Omega = \{1, 2, \ldots, 100\}$가 되도록 하자.
이때, $\mathcal{F} = \mathcal{P}(\Omega)$, $\mathbb{P}(A) = |A| / 100$로 정의하면, $(\Omega, \mathcal{F}, \mathbb{P})$는 확률 공간이 된다.
이제, 빨, 주, 노, 초, 파 각각의 색깔을 1, 2, 3, 4, 5에 대응하면, 다음과 같은 함수를 생각할 수 있다.
$$
    X(\omega)= \begin{cases}
    1 & (1 \leq \omega \leq 20)\\
    2 & (20 < \omega \leq 40)\\
    3 & (40 < \omega \leq 60)\\
    4 & (60 < \omega \leq 80)\\
    5 & (80 < \omega \leq 100)
    \end{cases}
$$
즉, 1번부터 20번까지의 공이 빨간색이고, 21번부터 40번까지의 공이 주황색이고, ... 한 상황을 생각해보자는 것이다. 
이제, 빨간색 공을 뽑는 사건은 색깔을 뽑는 함수 $X$의 빨간색에 대한 역상,
$$
    X^{-1}(1) = \{\omega \in \Omega | X(\omega) = 1\} = \{1, 2, \ldots, 20\}
$$
로 쓸 수 있고, 빨간색 공을 뽑을 확률은 $\mathbb{P}(X^{-1}(1)) = 20/100 = 1/5$로 쓸 수 있다.
이처럼, 그 역상으로써 사건을 표현할 수 있는 함수를 생각해보고자 한다.

> **Definition.** 두 가측 공간 $(\Omega, \mathcal{F})$, $(E, \mathcal{E})$에 대해, 함수 $X : \Omega \to E$가 임의의 $B \in \mathcal{E}$에 대해 $X^{-1}(B) \in \mathcal{F}$를 만족하면, $X$를 $\mathcal{F}/\mathcal{E}$-가측 함수(measurable function)라 부른다.

> **Definition.** 어떤 확률 공간 $(\Omega, \mathcal{F}, \mathbb{P})$ 와 가측 공간 $(E, \mathcal{E})$에 대해, $\mathcal{F}/\mathcal{E}$-가측 함수 $X : \Omega \to E$를 확률 변수(random variable)라 부른다.

> **Notation.** 어떤 확률 변수 $X : \Omega \to E$가 주어지면, $X$가 $x \in E$ 라는 값을 가지는 확률을 $\mathbb{P}(X = x)$로 쓴다. 즉,
> $$
> \mathbb{P}(X = x) := \mathbb{P}(X^{-1}(x))
> $$
> 이다.

다만, 모든 사건을 모아둔 집합 $\mathcal{F}$와는 달리, 확률 변수 $X$가 만들어내는 사건들은 그 일부에 불과하다. 가령, $X^{-1}(B)$는 $B$에 1이 포함되어있다면 반드시 1부터 20까지의 수를 모두 포함하여야 하므로, $\{1, 21\}$이라는 사건은 $X$의 역상으로 표현할 수 없다.
따라서, **확률 변수 $X$가 만들어내는 사건들의 모임**을 다음과 같이 정의한다.
> **Definition.** 어떤 확률 변수 $X : \Omega \to E$에 대해, 
> $$
>    \sigma(X) := \{X^{-1}(B) | B \in \mathcal{E}\} \subseteq \mathcal{F}
> $$
> 은 $\sigma$-대수를 이루고 ($\mathcal{E}$가 $\sigma$-대수이므로), 이를 $X$가 생성하는 $\sigma$-대수라 부른다.

## Conclusion
이렇게, 왜 측도가 필요한지, 사건과 확률을 어떻게 정의하는지, 확률 변수란 무엇인지에 대해 알아보았다. 다음 글에서는 측도를 통해 할 수 있는 적분과 이를 통해 정의되는 다양한 통계량들에 대해 살펴보고자 한다.