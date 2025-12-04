---
layout: post
title: [Statistical Thermodynamics] Macrovariables
image: "https://picsum.photos/700/300"
category: Physics
author: Me
---

## Macroscopic Configruation


Let $P=T^*C$ be a phase space of $N \sim 10^{23} \gg 1$ particles. 
In reality, we can't see the exact configuration of the particles, but we can see some *macroscopic* values only, e.g. volume, total energy, etc.
Such macroscopic configurations form a small space. Let us call such space $C_M$. 

> **Definition.** Coarse graining is a family of surjective, smooth functions on $P$.
> $$
> \begin{align*} 
>   \pi_t : P &\to C_M \\ x & \mapsto Q = (H_t, Q_i)
> \end{align*}
> $$
> Here, $t$ is the smooth time parameter, $H_t$ is the Hamiltonian at time $t$, and $Q_i$ are other macroscopic variables.
> The system is called time-independent if $\pi_t$ is independent of $t$.

If one observed macrovariables $Q$, then the real (phase space) configuration must be in $\pi_t^{-1}(Q)$. But, we don't know where the configuration really is.
So, we have to consider a probability distribution on $\pi_t^{-1}(Q)$. 
$\pi_t^{-1}(Q)$ is called an **ensemble** of $Q$.
If $A \subset \pi_t^{-1}(Q)$ is a measurable, then we can think the probablity that the configuration is in $A$. Let us denote it by $\mathbb{P}(A|Q, t)$.

## Equilibrium

The system is in **theromodynamic equilibrium** if $\mathbb{P}(A|Q, t)$ is invariant under the Hamiltonian flow $\sigma_s$. 
That is, for any measurable $A \subset \pi_t^{-1}(Q)$, we have
$$
\mathbb{P}(A|Q, t) = \mathbb{P}(\sigma_s(A)|Q, t + s)
$$
for all $t$ and $s$.
It means that the macrovariables $Q$ are not changing in time.

Consider the Liouville theorem, says that the Hamiltonian flow preserves the symplectic volume.
So, if we want $\mathbb{P}(A|Q, t)$ to be invariant under the Hamiltonian flow, then, we can set $\mathbb{P}(A|Q, t)$ being proportional to the symplectic volume.
That is, for any measurable $A \subset \pi_t^{-1}(Q)$ at time $t$, we have
$$
\mathbb{P}(A|Q, t) = \frac{\text{Vol}(A \cap \pi_t^{-1}(Q))}{\text{Vol}(\pi_t^{-1}(Q))}
$$
for all $t$ (at the sense of conditional probability).
This is called the **Ergodic hypothesis**.

If the system is time-independent, then $\pi_t^{-1}(Q)$ is also independent of time. Thus we can set $A \cap \pi_t^{-1}(Q)$ simply $A$.
So, we have
$$
\mathbb{P}(A|Q) = \frac{\text{Vol}(A)}{\text{Vol}(\pi_t^{-1}(Q))} \implies d\mathbb{P}(A|Q) = \frac{dV}{\text{Vol}(\pi_t^{-1}(Q))}
$$
for all $t$.
This is called a **microcanonical ensemble**.

The macrovariable $Q$ would be changing in time, with the transition probability
$$
    \Gamma_{s}(Q \to Q', t) = \int_{\pi_t^{-1}(Q)} \rho(x | Q, t) \mathbf{1}_{
        \pi_{t+s}^{-1}(Q')
    }(\sigma_s(x)) \ dx
$$
where $\rho(x|Q,t)$ is the probability density function of $\mathbb{P}(\cdot|Q,t)$.
Then, how $Q$ is changing in time is given by the master equation
$$
    \mathbb{P}(Q, t + s) - \mathbb{P}(Q, t) = \int_{C_M} dQ' \left[
        \Gamma_s(Q' \to Q, t) \mathbb{P}(Q', t) - \Gamma_s(Q \to Q', t) \mathbb{P}(Q, t)
    \right]
$$
It describes how the probability distribution of macrovariables $Q$ is changing in time.
If the system is in equilibrium, then $\mathbb{P}(Q, t)$ is independent of $t$. Assume that the system is in equilibrium.
Then, the master equation becomes
$$
    0 = \int_{C_M} dQ' \left[
        \Gamma_s(Q' \to Q) \mathbb{P}(Q') - \Gamma_s(Q \to Q') \mathbb{P}(Q)
    \right]
$$
for all $s$.
Let us introduce a stronger condition, called the **detailed balance** or **microscopic reversibility**:
$$
    \frac{\mathbb{P}(Q')}{\mathbb{P}(Q)} = \frac{\Gamma_s(Q \to Q')}{\Gamma_s(Q' \to Q)}
$$


## Environment

