---
title: PPO-based Single-Agent Drone Control in gym-PyBullet-drones Environment
summary: I use PPO based control algorithm and gym-pybullet-drones simulation environment to realize trajectory tracking for UAV simulation and try to add perturbation simulation!
date: 2025-02-16
authors:
  - admin
tags:
  - PPO
  - trajectory tracking
  - UAV
image:
---
## 1.Project Overview
This project implements **Proximal Policy Optimization (PPO)** to train a drone for stable flight in the `gym-pybullet-drones` simulation environment. The agent learns to maximize cumulative rewards through policy iteration, leveraging PPO's stability and efficiency for continuous control tasks. Key components include:
- **Actor-Critic Architecture**: Separate networks for policy (Actor) and value estimation (Critic).
- **Clipped Surrogate Objective**: Ensures stable policy updates by limiting divergence.
- **Generalized Advantage Estimation (GAE)**: Balances bias-variance trade-off in advantage calculation.
- **Experience Buffer**: Efficiently stores and processes trajectory data for mini-batch updates.

## 2.Algorithm Implementation Highlights

### 2.1 Core Components
- **Dual Optimizers**:  
  Actor and Critic networks use separate Adam optimizers with distinct learning rates to decouple updates:
  ```python
  self.actor_opt = Adam(actor.parameters(), lr=3e-4)
  self.critic_opt = Adam(critic.parameters(), lr=1e-3)
  ```
- **Policy Loss with Clipping**:  
  Limits policy updates to prevent drastic changes:
  ```math
  L^{CLIP} = \mathbb{E}_t\left[\min\left(r_t(\theta)A_t, \text{clip}(r_t(\theta), 1-\epsilon, 1+\epsilon)A_t\right)\right]
  ```
- **Entropy Regularization**:  
  Encourages exploration by penalizing low-entropy policies.

### 2.2 Critical Design Choices
- **Parameter Isolation**: Ensures gradients from Actor and Critic do not interfere.
- **KL Early Stopping**: Halts policy updates if KL divergence exceeds `1.5 * target_kl`.
- **Normalization**:  
  - **Observation Normalization**: Standardizes states using running mean/std.  
  - **Reward Normalization**: Scales rewards based on discounted return statistics.

## Disturbance Injection Framework for Quadcopter Control in Gym-PyBullet-Drones Environment  

### 1. Project Overview
This project implements a modular disturbance injection framework within the **gym-pybullet-drones** simulation environment to evaluate and enhance the robustness of quadcopter control algorithms. The framework supports dynamic perturbation of system inputs (e.g., motor RPMs) and states (e.g., position, velocity), enabling rigorous testing of control policies under realistic disturbances such as wind gusts, sensor noise, and electromagnetic interference.  

Key contributions include:    
- **Composable disturbance sequences** (e.g., multi-step pulses, decaying oscillations).  
- **Reproducible experiments** via deterministic random seed management.  

### 2. Technical Implementation  

The codebase employs a **Composite Pattern**  to unify individual disturbances into complex sequences:  

```python  
class Disturbance:  
    def apply(self, target, env):  # Base class for all disturbances  
        return target  

class DisturbanceList(Disturbance):  # Composite class  
    def apply(self, target, env):  
        for disturb in self.disturbances:  # Sequentially apply perturbations  
            target = disturb.apply(target, env)  
        return target  
```
  
- **Flexibility**: Combine impulse, noise, and periodic disturbances.  
- **Reusability**: Disturbances can be masked to specific state/input dimensions (e.g., apply wind only to x-axis) using `mask` parameters 

#### Impulse Disturbance Design
The `ImpulseDisturbance` class models short-duration perturbations with configurable waveforms:  
```python  
class ImpulseDisturbance(Disturbance):  
    def __init__(self, magnitude=1, duration=1, decay_rate=1):  
        # Waveform examples: square (decay_rate=1), triangle (decay_rate<1)  
        self.magnitude = magnitude  
        self.decay = decay_rate ** np.arange(duration)  
```
  
- **Waveform types**: Square, triangular, and exponential decay pulses 
![](./wave.png)
- **Mathematical representation**:  
  - **Square pulse**: $ \delta(t) = A \cdot \mathbb{I}_{[t_0, t_0 + \Delta t]}(t) $  
  - **Triangular pulse**: $ \delta(t) = A \cdot (1 - \frac{t}{\Delta t}) $  

#### Deterministic Randomness
The `seed()` method ensures reproducibility by synchronizing disturbance randomization with the simulation:  
```python  
def seed(self, env):  
    self.np_random = env.np_random   
```
This is critical for RL policy evaluation under stochastic disturbances.  
  

