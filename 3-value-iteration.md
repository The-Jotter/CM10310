---
title: MDPs and Value Iteration
date: 2023-02-21
---

# MDPs and Value Iteration
## What is a Policy?
A policy (represented by $\pi$) specifies which action to take for each possible state $\pi(a | s)$.

* ***Deterministic*** policies select only one possible action every time.
* ***Stochastic*** policies can randomly select from multiple different possible actions.

For example, a *deterministic* policy $\pi_1$ for a dice-rolling game would be:
| $\pi_{1}$ | $a_1$ | $a_2$ | $a_3$ |
|-----------|-------|-------|-------|
| $s_1$ | 0 | 0 | 1 |
| $s_2$ | 0 | 1|  0 |

A *stochastic* policy $\pi_2$ for the same game would be:

| $\pi_{2}$ | $a_1$ | $a_2$ | $a_3$ |
|-----------|-------|-------|-------|
| $s_1$ | 0.25 | 0.25 | 0.5|
| $s_2$ | 0 | 0.8| 0.2|

## Expected Value $\mathbb{E}$
The expected value is the average value you will get after experimenting $\infty$ or a high number of times.

For a fair die, where each side is as likely to come up:

$\mathbb{E}\left[d6\right] = \frac{1}{6} \sum_{n=1}^6 n = 3.5$ 

For a biased die, where 6 is 3 times as likely to come up than the others:

$\mathbb{E}_{\text{Biased}} = \frac{1}{8} \left(1 + 2 + 3 + 4 + 5 + 3 \times 6\right) = 4.125$

### The State-Value Function
Okay, but what about finding out what policy is best to take?

We can use this expected value to find out which policy will get us the best long term reward (using our friend, the discounted return $G_t$):

$V^{\pi}(s) = \mathbb{E}_{\pi}\left[G_t | s_t = s\right]$

This value tells us "how good" each state is under the policy $\pi$.

If we recall what the discounted return formula is:

$G_t = r_{t+1} + \gamma r_{t+2} + \gamma^2 r_{t+3} + \cdots\\G_t = r_{t+1} + \gamma(r_{t+2} + \gamma r_{t+3} + \cdots)$

We can notice it is self-similar!

So therefore $G_t = r_{t+1} + \gamma G_{t+1}$

Our new formula for the state-value function can be written as:

$V^{\pi}(s) = \mathbb{E}_{\pi}\left[r_{t+1} + \gamma G_{t+1} | s_{t+1} = s^\prime\right]$

or, in terms of actions $a$:

$V^\pi(s) = \sum_{a}\underbrace{\pi(a | s)}_{\mathclap{\text{Probability of choosing action }a \text{ under policy} \pi}}\sum_{s^\prime, r}\overbrace{p(s^\prime, r|s, a)}^{\mathclap{\text{Probability of transitioning to state }s^\prime \text{ using action } a}}\cdot (r + \gamma \underbrace{V^\pi(s^\prime)}_{\mathclap{\text{State-value function}}})$

The above formula will give us a numerical summary of how good state $s$ is based on its possible future rewards.

However, there's a problem here... Figuring out the value of one state $s$, requires the value of another state $s^\prime$. How can we solve this?

### Value-Iteration
