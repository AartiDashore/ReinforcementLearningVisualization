# Reinforcement Learning Visualization: Q-Learning in a Grid Environment

This project demonstrates the implementation of a simple Q-learning algorithm in a grid environment and visualizes the agent's learning process. The goal of the agent is to navigate from the starting position to a goal location in a grid while learning the optimal policy through trial and error.

## Table of Contents
- [Overview](#overview)
- [Concepts](#concepts)
- [Algorithms](#algorithms)
- [Variables and Parameters](#variables-and-parameters)
- [Prerequisites](#prerequisites)
- [Usage](#usage)
- [Visualization](#visualization)
- [Learned Policy Map](#learned-policy-map)
- [Applications of Q-Learning Algorithms](#applications-of-q\-learning-algorithms)
- [License](#license)

## Overview

In this project, we use Q-learning, a fundamental reinforcement learning (RL) algorithm, to teach an agent how to navigate a simple grid environment. The agent starts at the top-left corner of the grid and must reach the goal in the bottom-right corner. As the agent interacts with the environment, it learns the best actions to take at each step to minimize the total number of steps and maximize rewards.

The project also includes visualizations of the learning trajectory and the learned policy map.

## Concepts

### Reinforcement Learning (RL)
Reinforcement Learning is a machine learning paradigm where an agent learns to make decisions by interacting with an environment. The agent receives rewards or penalties based on the actions it takes and learns to maximize cumulative rewards over time.

### Q-learning
Q-learning is a model-free RL algorithm that allows the agent to learn a policy that dictates the best action to take in each state. The Q-values represent the expected future rewards for taking a particular action in a given state.

### Policy Evaluation
The learned policy is the mapping from states to actions that the agent follows to maximize its cumulative reward. In Q-learning, the policy is derived from the Q-values stored in a Q-table.

## Algorithms

### Q-Learning Algorithm
The Q-learning algorithm updates a Q-value function based on the action taken by the agent. The agent explores the environment by choosing actions and updating the Q-values according to the following update rule:

```
Q(s, a) ← Q(s, a) + α * [r + γ * max(Q(s', a')) - Q(s, a)]
```

Where:
- `Q(s, a)`: The Q-value for state `s` and action `a`.
- `α`: The learning rate (how quickly the agent updates its knowledge).
- `r`: The immediate reward received after taking action `a` in state `s`.
- `γ`: The discount factor (how much future rewards are valued).
- `s'`: The next state resulting from the action `a`.
- `max(Q(s', a'))`: The maximum predicted future reward for the next state.

### Greedy vs. Exploratory Action Selection
- **Exploration**: The agent selects a random action with probability `ε` (epsilon) to explore new states.
- **Exploitation**: The agent selects the action with the highest Q-value for the current state to exploit its learned policy.
  
## Variables and Parameters

### Environment: `GridWorld`
- **size**: The size of the grid (e.g., `size=5` creates a 5x5 grid).
- **state**: The current position of the agent in the grid, initialized to `(0, 0)`.
- **goal**: The goal position in the grid, initialized to `(size-1, size-1)`.

### Agent: `QLearningAgent`
- **alpha (`α`)**: Learning rate. Controls how much new information overrides the old information. Values range from `0` (no learning) to `1` (only new information is used).
- **gamma (`γ`)**: Discount factor. Controls the importance of future rewards. A value close to `1` makes the agent prioritize future rewards over immediate rewards.
- **epsilon (`ε`)**: Exploration rate. Controls how often the agent explores new actions. A higher value means more exploration, while a lower value means more exploitation of the learned policy.
- **q_table**: A 3D numpy array that stores the Q-values for each state-action pair.

### Actions
The agent can choose one of the following actions at each step:
- `up`
- `down`
- `left`
- `right`

These actions correspond to moving up, down, left, or right in the grid.

### Rewards
- **Goal state**: Reaching the goal gives a reward of `1`.
- **Other states**: All other moves incur a small penalty of `-0.1` to encourage the agent to find the goal quickly.

## Prerequisites

To run this project, you need to have Python installed along with the following libraries:
- `numpy`
- `matplotlib`

You can install the necessary libraries using:
```bash
pip install numpy matplotlib
```

## Usage

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-repo/rl-qlearning-visualization.git
   cd rl-qlearning-visualization
   ```

2. **Run the Program**:
   Execute the script to train the Q-learning agent and visualize its learning process:
   ```bash
   python q_learning_gridworld.py
   ```

3. **Adjust Parameters**: 
   You can modify the environment size, learning rate (`alpha`), discount factor (`gamma`), and exploration rate (`epsilon`) by adjusting the parameters in the script.

## Visualization

### Learning Trajectories
During training, the agent's trajectory (path) through the grid is visualized at intervals (e.g., after every 100 episodes). This shows how the agent improves over time by learning to find more efficient paths to the goal.

Example plot showing the agent's path:

![Agent_Trajectory_1](https://github.com/AartiDashore/ReinforcementLearningVisualization/blob/main/o1.png)

![Agent_Trajectory_2](https://github.com/AartiDashore/ReinforcementLearningVisualization/blob/main/o2.png)

![Agent_Trajectory_3](https://github.com/AartiDashore/ReinforcementLearningVisualization/blob/main/o3.png)

![Agent_Trajectory_4](https://github.com/AartiDashore/ReinforcementLearningVisualization/blob/main/o4.png)

![Agent_Trajectory_5](https://github.com/AartiDashore/ReinforcementLearningVisualization/blob/main/o5.png)


### Learned Policy Map
After training, the learned policy is visualized as a grid where each cell shows the optimal action for that state (e.g., "U" for up, "D" for down, "L" for left, and "R" for right).

Example output of the policy map:

![Output_Map](https://github.com/AartiDashore/ReinforcementLearningVisualization/blob/main/output_map.png)

## Applications Of Q-Learning Algorithms
The Q-learning algorithm and reinforcement learning (RL) concepts implemented in the project can be applied to a variety of real-world problems where an agent must make sequential decisions in an environment to maximize cumulative rewards. These applications demonstrate the versatility of Q-learning and reinforcement learning in solving real-world problems across various industries. The ability of RL algorithms to learn optimal decision-making policies through experience and feedback makes them highly effective for tasks that require sequential decision-making in uncertain environments. Here are some key applications:

### 1. **Autonomous Navigation and Robotics**
   - **Self-driving cars**: RL helps autonomous vehicles learn to navigate through complex environments by making real-time decisions to avoid obstacles, follow traffic rules, and optimize routes.
   - **Robotics**: Robots in industrial settings can learn to perform tasks like assembling products, moving objects, or navigating through spaces by trial and error, optimizing performance over time.
   
### 2. **Game AI**
   - **Video game agents**: Q-learning is often used to train AI agents that can play games by learning optimal strategies. For instance, in simple grid-based games or more complex ones like chess or Go, RL enables the AI to improve by playing many rounds.
   - **Board games**: RL can be applied to board games where the agent learns the best moves by evaluating the state of the game and selecting optimal strategies, like training agents for tic-tac-toe, checkers, or chess.

### 3. **Recommendation Systems**
   - **Dynamic content recommendations**: RL can be applied to recommendation systems to continuously learn user preferences and adapt recommendations. For example, online platforms (e.g., YouTube, Netflix) can use RL to recommend movies, videos, or products based on user interactions.
   - **Personalized advertising**: RL optimizes the selection and placement of ads to maximize click-through rates or conversions by learning the most relevant ads for individual users.

### 4. **Finance and Trading**
   - **Portfolio management**: RL can help manage a financial portfolio by learning to allocate resources optimally over different assets to maximize returns while minimizing risk. The agent can adapt to market conditions and continuously refine its investment strategy.
   - **Algorithmic trading**: In stock markets, RL agents can be trained to execute buy/sell decisions based on market data to maximize profits while considering transaction costs and market risks.

### 5. **Healthcare**
   - **Treatment planning**: RL can be applied to healthcare settings to help doctors or AI systems make treatment decisions. For example, in cancer treatment, RL can learn to suggest the optimal sequence of treatments (e.g., chemotherapy, surgery) to maximize patient survival rates while minimizing side effects.
   - **Personalized medicine**: RL helps in recommending personalized treatment paths based on patient data and past outcomes, making medicine more tailored to individual needs.

### 6. **Energy Management**
   - **Smart grids**: RL can be used to optimize energy distribution in smart grids by learning when and where to supply power based on demand, availability of renewable energy sources, and grid load.
   - **HVAC systems**: RL optimizes heating, ventilation, and air conditioning (HVAC) systems in buildings to reduce energy consumption by learning how to adjust settings dynamically based on external temperature, occupancy, and time of day.

### 7. **Supply Chain Optimization**
   - **Inventory management**: RL can help manage inventory in warehouses or retail by learning optimal restocking policies to minimize costs and avoid stockouts or overstocking.
   - **Logistics and transportation**: RL helps optimize the routes and schedules of delivery trucks or cargo ships to minimize fuel consumption, travel time, and costs, while also considering constraints like traffic or weather.

### 8. **Manufacturing**
   - **Process optimization**: In manufacturing, RL is used to optimize production processes, such as reducing waste, improving yield, and minimizing defects, by learning the best configuration of machine parameters.
   - **Quality control**: RL agents can monitor manufacturing processes and adapt settings in real time to maintain high product quality while reducing defects and downtime.

### 9. **Resource Management in Cloud Computing**
   - **Cloud resource allocation**: RL can be used to dynamically allocate resources (CPU, memory, storage) in cloud computing environments. The agent learns to balance load distribution, scale resources, and reduce energy consumption while meeting user demands.
   - **Task scheduling**: RL can optimize task scheduling in cloud environments, ensuring that jobs are executed efficiently while minimizing delays and resource contention.

### 10. **Marketing and Customer Interaction**
   - **Dynamic pricing**: RL can learn to set optimal prices for products in real time by considering factors like demand, customer behavior, and competitor prices to maximize profits.
   - **Customer support chatbots**: RL-powered chatbots can interact with customers and learn the best responses to inquiries, improving over time through interactions and feedback.

### 11. **Smart Cities**
   - **Traffic light control**: RL can optimize the control of traffic lights to minimize congestion and reduce travel time in urban areas. The system learns to adjust the timing of lights based on real-time traffic flow and road conditions.
   - **Waste management**: RL can optimize waste collection routes and schedules in smart cities to reduce fuel consumption and operational costs by learning the best paths based on waste accumulation patterns.

### 12. **Education and Training**
   - **Personalized learning**: RL can be used in educational systems to provide personalized learning experiences by adapting to the student's learning style, pace, and performance. The system can suggest learning materials, exercises, and feedback that maximize engagement and retention.
   - **Training simulations**: RL is applied to training simulations, such as flight simulators or medical training, where agents learn to navigate complex situations by practicing and improving their decision-making skills.

### 13. **Natural Language Processing (NLP)**
   - **Dialogue systems**: RL helps improve conversational AI systems by learning to provide the most relevant and context-aware responses in chatbots and virtual assistants.
   - **Machine translation**: RL can optimize translation models to improve the accuracy and fluency of language translations by continuously learning from feedback on translation quality.

### 14. **Adaptive Control Systems**
   - **Robust control**: RL is used in control systems, such as autopilot systems for aircraft or spacecraft, where the agent learns to make decisions in dynamic environments with unpredictable conditions, ensuring optimal performance.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

### Key Points:
- **Algorithms**: Describes Q-learning with the update rule and action selection strategies (exploration vs. exploitation).
- **Variables**: Explains important variables like the learning rate (`α`), discount factor (`γ`), and exploration rate (`ε`), as well as the Q-table.
- **Visualization**: Explains how to visualize both the learning trajectory and the final policy map.
