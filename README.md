# Q-Learning and Deep Q-Network (DQN) Projects

## Overview
This repository contains two reinforcement learning projects implemented in **Python** using **PyTorch** and **Gymnasium**. These projects demonstrate a structured progression from traditional table-based **Q-learning** to deep reinforcement learning with **Deep Q-Networks (DQN)**.

## Project Structure
### 1. Q-Learning (FrozenLake-v1)
**Objective:** Solve the **FrozenLake-v1** environment using **Q-learning**, a tabular reinforcement learning method.

#### Hyperparameters:
- **Learning Rate (α):** Controls how much new information overrides old information.
- **Discount Factor (γ):** Determines the importance of future rewards.
- **Exploration Rate (ε):** Defines the probability of taking random actions.
- **Epsilon Decay:** Ensures the agent explores sufficiently before exploiting learned knowledge.

#### Training Process:
- Initialized a **Q-table** with all values set to zero.
- Used the **Bellman equation** to iteratively update Q-values.
- Implemented an **epsilon-greedy policy** to balance exploration and exploitation.
- Trained the agent over **several thousand episodes** until convergence.

#### Testing & Results:
- The agent successfully learned to navigate the frozen lake without falling into holes.
- Achieved a **high cumulative reward** after tuning hyperparameters.
- Demonstrated **stable and optimal decision-making** with improved success rates.

#### Challenges & Fixes:
- Initial instability due to improper learning rate → **Adjusted α** for smoother updates.
- Agent getting stuck in loops → **Fine-tuned ε decay** to improve exploration.
- Poor long-term reward optimization → **Tweaked γ** to ensure future rewards were valued correctly.

---

### 2. Deep Q-Network (DQN) (CartPole-v1)
**Objective:** Train a **DQN agent** to balance a pole on a moving cart in **CartPole-v1**.

#### Hyperparameters:
- **Gamma (γ):** 0.99 – Encourages long-term rewards.
- **Learning Rate (α):** 0.001 – Optimized for stable learning.
- **Epsilon (ε) Start:** 1.0 – Ensures early exploration.
- **Epsilon (ε) End:** 0.01 – Prevents excessive randomness in later stages.
- **Epsilon Decay:** 0.995 – Gradual reduction of exploration.
- **Batch Size:** 64 – Number of experiences sampled for training.
- **Memory Capacity:** 10,000 – Stores past experiences for replay.
- **Target Network Update Frequency:** Every 10 episodes – Stabilizes learning.
- **Total Episodes:** 500 – Ensures adequate training time.

#### Training Process:
- **Neural Network Architecture:**
  - Input: **State (4-dimensional)**
  - Hidden Layers: **Two fully connected layers (128 neurons each, ReLU activation)**
  - Output: **Q-values for 2 possible actions**
- **Experience Replay:** Stores past experiences and samples random batches to break correlation between consecutive experiences.
- **Target Network:** Used to stabilize training by maintaining a delayed copy of the main Q-network.
- **Epsilon-Greedy Strategy:**
  - Starts with high randomness (ε = 1.0) and gradually shifts toward exploitation.
  - Ensures sufficient exploration in early training stages.

#### Testing & Results:
- Successfully trained the agent to achieve a **perfect score of 500**, meaning it balanced the pole indefinitely.
- **Evaluated performance** by running multiple test episodes without exploration (ε = 0).
- **Recorded a video** showcasing the trained agent’s performance.
- Optimized hyperparameters to achieve **smooth and stable training**.

#### Challenges & Fixes:
- Training instability → **Adjusted network architecture** for better convergence.
- Poor exploration → **Modified epsilon decay rate** to balance exploration and exploitation.
- Video recording issues → **Refactored rendering process** to ensure successful visualization.

---

## Dependencies
Ensure you have the necessary libraries installed:
```bash
pip install numpy torch gymnasium matplotlib imageio
```

## Results Summary
| Project | Environment | Method | Final Performance |
|---------|------------|--------|-------------------|
| **Q-Learning** | FrozenLake-v1 | Tabular Q-learning | Solved, optimal path found |
| **DQN** | CartPole-v1 | Deep Q-Network | Achieved max score (500) |

## Files Included
- `reinforcement_learning.py` - Contains both **Q-learning** and **DQN** implementations.
- `dqn_cartpole.mp4` - Video demonstrating the trained **DQN agent**.
- `frozenlake_qlearning.mp4` - Video demonstrating the trained **Q-learning agent**.

## Conclusion
This repository provides a comprehensive guide to reinforcement learning, from **basic Q-learning** to **advanced deep Q-networks**. The projects highlight key concepts such as:
- **Q-learning updates** using tabular methods.
- **Neural network-based function approximation** in deep RL.
- **Experience replay and target networks** for stable DQN training.
- **Hyperparameter tuning** for improved learning performance.

Both projects demonstrate successful training and testing, with recorded videos to visualize the learning process. The trained models effectively **solve their respective environments** through reinforcement learning techniques.

## Future Work
* Implement Double DQN to reduce overestimation of Q-values.
* Train an agent using Dueling DQN for more efficient learning.
* Extend to more complex environments like Atari games.
* Experiment with different reward structures to test robustness.
* Introduce policy-based methods (e.g., Actor-Critic) for comparison.

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a new branch (feature-branch).
3. Commit your changes and push them.
4. Open a Pull Request.

## License
This project is licensed under the MIT License.
