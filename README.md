# Optimizing DQN for Electricity Market Management

## Project Overview
This project explores reinforcement learning for optimizing energy trading in an electricity market with a battery storage system. Initially, both **DQN (Deep Q-Network)** and **PPO (Proximal Policy Optimization)** agents were implemented, but due to PPO's poor performance in the sparse reward setting, we focused on **DQN**. Later, we applied **Genetic Algorithms (GA)** to optimize DQN’s hyperparameters, leading to significant improvements.

## Problem Statement
Managing an electricity market with dynamic **price** and **demand** fluctuations is complex. An optimal energy trading policy must balance **charging and discharging a battery** to maximize **profit** while ensuring demand is met efficiently.

## Environment
The **ElectricityMarketEnv** is a custom OpenAI Gym environment that models:

- **State Space:** (1) Battery **State of Charge (SoC)**, (2) Electricity **demand**, and (3) **Price**.
- **Action Space:** Continuous charging/discharging in the range **[-Battery Capacity, Battery Capacity]**.
- **Reward Function:** Profit is earned by selling excess electricity to the grid.

An **ExtremeEnvironment** version with more volatile price/demand peaks was also tested for robustness.

## Methods

### 1. Initial Comparison of DQN vs PPO
- **DQN:** A value-based, off-policy RL algorithm with **discretized actions**.
- **PPO:** A policy-based, on-policy RL method with **continuous actions**.
- PPO struggled due to **sparse rewards**, leading us to focus on DQN.

### 2. Genetic Algorithm for Hyperparameter Tuning
- **GA optimizes DQN hyperparameters**, evolving a population over multiple generations.
- Parameters tuned: **learning rate, gamma, epsilon decay, batch size, action discretization, etc.**
- GA **selected the best-performing individuals** based on **profit and demand satisfaction**.

## Results

### Default vs Optimized DQN Parameters:
| Parameter       | Default DQN | Optimized DQN (GA) |
|----------------|------------|-------------------|
| Learning Rate  | 0.001      | 0.009           |
| Gamma          | 0.99       | 0.933           |
| Epsilon Decay  | 0.99       | 0.989           |
| Epsilon Min    | 0.05       | 0.021           |
| Batch Size     | 64         | 16              |
| Memory Size    | 10,000     | 2,000           |
| Action Size    | 11         | 5               |

### Performance Gains:
- **Higher profits** achieved using GA-optimized DQN.
- **More stable learning curve** in **ExtremeEnvironment**.

## Installation & Usage

### 1. Clone Repository
```bash
git clone https://github.com/maayanwasser/SDMRL-project
cd your-repo
```

### 2.Installation & Requirements
```bash
pip install gymnasium numpy tensorflow matplotlib

```
### 3. Run Environment
First cell

### 4. Define DQN and PPO agents
Second and third cells

### 5. Define extreme environment
4th cell

### 6. Run and evaluate DQN and PPO agents
5th cell

### 7. Run and evaluate Hyperparameter Optimization (GA)
6th cell


