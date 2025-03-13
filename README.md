Electricity Market Optimization using Deep Reinforcement Learning and Genetic Algorithms


Project Overview:

This project explores the use of Deep Q-Networks (DQN) and Proximal Policy Optimization (PPO) to optimize battery usage in an electricity market environment. Initially, both PPO and DQN were evaluated, but due to PPO's poor performance with sparse rewards, we focused on optimizing DQN using Genetic Algorithms (GA) for hyperparameter tuning.


Repository Structure:

ProjectMaayanSagiNew.ipynb - The main Jupyter Notebook containing the implementation and the results and graphs running the code
ProjectMaayanSagiNew.py - The implementation code in Python file.



Environment Setup:

Electricity Market Environment-
The environment models an electricity market with the following components:

State Space-
SoC (State of Charge of the battery) - Ranges from 0 to Battery Capacity.
Dt (Electricity Demand) - Ranges from [0, ∞].
Pt (Electricity Price) - Ranges from [0, ∞].

Action Space-
Continuous action space for battery charging/discharging, ranging from -Battery Capacity to Battery Capacity.

Code Implementation:

1. Electricity Market Environment

The environment is implemented as a gym.Env class, simulating a battery storage system where the agent decides when to charge/discharge based on electricity demand and price variations.

2. Deep Q-Network (DQN) Implementation

The DQN agent uses:

A replay buffer to store experiences.

A neural network to approximate Q-values.

A target network for stable updates.

Initial hyperparameters:

learning_rate=0.001, gamma=0.99, epsilon=1.0, epsilon_decay=0.99,
epsilon_min=0.05, batch_size=64, memory_size=10000, action_size=11

3. Proximal Policy Optimization (PPO) Implementation

PPO was tested as an alternative policy-based RL approach but struggled with sparse rewards, leading us to focus on DQN.

Hyperparameter Optimization with Genetic Algorithm (GA)

To enhance DQN’s performance, we implemented a Genetic Algorithm (GA) for hyperparameter tuning. GA iteratively selects, mutates, and evolves hyperparameters to maximize the agent’s performance.

Best hyperparameters found by GA:

learning_rate=0.009, gamma=0.933, epsilon=1.0, epsilon_decay=0.989,
epsilon_min=0.021, batch_size=16, memory_size=2000, action_size=5


Experimental Results:

DQN vs PPO: DQN showed better initial performance.

Default vs Optimized DQN: The GA-tuned DQN showed improved training stability, higher profits, and better demand satisfaction.

Extreme Market Conditions: The GA-optimized DQN adapted better to volatility than the default DQN.



Running the Project:

Installation

pip install gymnasium tensorflow numpy matplotlib


Training the DQN Agent

python train_dqn.py


Running the Genetic Algorithm Optimization

python run_ga.py


Testing the Optimized Model

python test_agent.py


Conclusion

This project demonstrated how Reinforcement Learning and Genetic Algorithms can optimize electricity market operations by efficiently managing battery storage. The GA-optimized DQN significantly outperformed the baseline model, showing promise for real-world applications in smart energy management.

