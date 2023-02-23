---
title: Markov Decision Process
date: 2023-02-14
slides: https://moodle.bath.ac.uk/pluginfile.php/2184406/mod_resource/content/4/s2week2_MarkovDecisionProcess.pdf
---

# Markov Decision Process

What about decision-making under uncertain environments where outcomes are not certain?

For example, how does a potential agent make decisions in a game like Pacman, or Tetris?

Here, the outcome of our actions is not certain. Instead, we work with probabilities

Transition probability: the probability that the action leads to a specific state.

## The Markov Property
In some situations, we could assume the history of every
state and action before affects the next state.

But, this is a nightmare. So, we can look at a specific property of probabilistic systems:
The Markov Property.

Systems with the Markov Property do not need this memory of the previous history:
you only need the current state to know what could happen next.

For example in the game Tetris, it does not matter how we get to a particular state
of blocks on the grid (since they are essentially equivalent -- a block is a block).

## What is the Markov Decision Process?
It consists of:
* A set of possible states: $(s_0, s_1, \dots, s_n)$
* Possible Actions from a state $a_i$
* Transition probabilities: $p(s_{t+1} | s_t, a_t)$
* Reward for each transition between each state $r(s_{t+1}, s_t, a_t)$

### Transitional Probabilities

$p(s_{t+1} | s_{t}, a_t)$ &mdash; The probability of transitioning to state $s_{t+1}$ from $s_t$ using action $a_t$ 

| Variable | Description   |
|----------|---------------|
|$s_t$     | Current state |
|$s_{t+1}$ | Next state    |
|$a_t$     | Action to take now |

### Maximizing long-term rewards

How do we choose a strategy for choosing an action in an MDP?

The *discounted return* with a discount rate $\gamma$ of a sequence of states is defined as:

$G_t = r_{t+1} + \gamma r_{t+1} + \gamma^2 r_{t+2} + \dots = \sum_{k=0}^{\infty} \gamma^{k}r_{t+(k+1)}$

Where $0 \leq \gamma \leq 1$.

The variable $\gamma$ allows us to control how much our agent would take future rewards into account:
* So a lower amount makes the agent favour short-term rewards; and
* $\gamma = 1$ would make the agent consider all future rewards equally.

Though a value of $\gamma = 1$ is not feasible as we cannot add an infinite sum &mdash; a slightly lower discount rate (such as $\gamma = 0.9$) can allow us to get closer to an approximation for this infinite sum.