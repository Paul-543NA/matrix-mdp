# Matrix MDP

Easily generate an MDP from transition and reward matricies.

## Installation
Assuming you are in the root directory of the project, run the following command:
```bash
pip install .
```

## Usage
```python
import gymnasium as gym
import matrix_mdp
env = gym.make('matrix_mdp/MatrixMDP-v0')
```

## Environment documentation

### Description

A flexible environment to have a gym API for discrete MDPs with `N_s` states and `N_a` actions given:
 - A vector of initial state distribution P_0(S)
 - A transition probability matrix P(S' | S, A)
 - A reward vector R(S, A)

### Action Space

The action is an `int` state index.

### Observation Space

The observation is an `int` state index.

### Rewards

The reward function is defined according to the reward matrix given at the creation of the environment.

### Starting state

The starting state is a random state sampled from $P_0$.

### Episode Truncation

The episode truncates when a terminal state is reached.
Terminal states are inferred from the transition probability matrix as states that have all leaving
probabilities to 0, e.g. state s is terminal if:
$\sum_{s' \in S} \sum_{a \in A} P(s' | s, a) = 0$

### Arguments

- `p_à`: `ndarray` of shape `(n_states, )` representing the initial state probability distribution.
- `p`: `ndarray` of shape `(n_states, n_states, n_actions)` representing the transition dynamics $P(S' | S, A)$.
- `r`: `ndarray` of shape `(n_states, n_actions)` representing the reward matrix.

```python
import gymnasium as gym
gym.make('MatrixMDP-v0', p_0=p_0, p=p, r=r)
```

### Version History

* `v0`: Initial versions release
