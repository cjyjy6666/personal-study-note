# MathFoundationRL
## Basic concepts
**State**:status of agent in environment

**State space**:set of all possible states

**Action**

**Action space of a state**:set of all possible actions in a state. $A(s_i)$ is function of state

**State transition** defines interaction with the environment. could be stochastic or deterministic.

Use state transition probability (conditional probability) to describe the state transition. $P(s_j|s_i,a_i)$

**Policy $\pi(a_i|s)$** means probability of taking action $a_i$ in state $s$,can represent either deterministic or stochastic cases.

**reward**: a real number after taking an action.

often: positive reward: encouragement, negative reward: punishment.

description: conditional probability

**trajectory**: a state-action-reward chain

**return**: sum of rewards along a trajectory

**discounted return**(by introducing **discounted rate$\gamma$**)

**episode**: a finite trajectory

episode tasks->continuing tasks


