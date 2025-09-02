# SwarmNavigator

Decentralized Multi-Agent Coverage & Obstacle Avoidance in 2D Gridworlds (Reinforcement Learning Framework)  
Ayushman Mishra (`frMishR`)

---

## Overview

**SwarmNavigator** is an open-source, research-grade RL framework for decentralized multi-agent coverage and collision avoidance in configurable 2D gridworlds.  
All code, results, and visualizations are contained in a single Jupyter notebook. This project demonstrates how advanced swarm robotics and deep RL can be developed, analyzed, and shared with minimal setup—enabling robust benchmarking, visualization, and extension for research and industry applications.

---

## Project Structure

```text
SwarmNavigator/
├── dqn_logs/            # Training logs and rewards for DQN runs
├── ppo_logs/            # Training logs and rewards for PPO runs
├── ppo_swarm_logs/      # Logs for PPO-trained swarm agents
├── results/             # Output: GIFs (demo episodes, coverage maps)
├── SwarmNavigator.ipynb # Main Jupyter Notebook (all code + documentation)
├── .gitattributes
├── .gitignore
├── LICENSE
├── README.md
└── requirements.txt


---

## Project Goals

- Develop a robust, modular environment for multi-agent RL research and demonstration.
- Enable scalable benchmarking of PPO, DQN, and random baseline agents on customizable gridworlds.
- Provide best-practice diagnostics: reward curves, coverage heatmaps, agent trajectory overlays, animated rollouts.
- Showcase code quality and research rigor suitable for portfolio, lab, and technical job applications.

---

## Key Features

| Feature                        | Details                                                                          |
|--------------------------------|----------------------------------------------------------------------------------|
| **Customizable Gridworld**     | Arbitrary grid size, obstacle density, and agent count (1–4 agents).             |
| **Multi-Agent Swarm Support**  | Decentralized agent control, parallel movement, inter-agent collision logic.      |
| **RL Algorithms**              | PPO (policy gradient), DQN (value-based), and random baseline agents.            |
| **Collision-Aware Rewards**    | Penalizes obstacle/wall/agent collisions, rewards new coverage.                   |
| **Full Visualization**         | Step-by-step grid plots, coverage heatmaps, color-coded agent trajectories.       |
| **GIF/MP4 Export**             | Animated demos of agent and swarm rollouts for documentation and recruiter demos. |
| **Logging & Reproducibility**  | All training logs and outputs saved in dedicated folders for each algorithm.      |
| **Extensible Architecture**    | Object-oriented code, ready for ROS2 integration, curriculum RL, or vision tasks. |

---

## Methodology

- **Environment**:  
  Custom Python class simulates a 2D grid with configurable obstacles and agent spawning.  
  Agents act in parallel, each choosing from five discrete actions (up, down, left, right, stay).

- **Reward Structure**:  
  +1 for new cell coverage, –1 for collisions, 0 otherwise.

- **RL Integration**:  
  Environments are wrapped for Stable-Baselines3 compatibility.  
  Trained both single-agent and multi-agent policies with PPO and DQN.

- **Visualization**:  
  - **Coverage Heatmaps**: Per-cell visitation frequency for agents and swarms.
  - **Trajectory Overlays**: Plots of individual and swarm movement paths.
  - **Animated Rollouts**: GIF/MP4 export of agent navigation in real environments.
  - **Reward Curves**: Training progress for PPO/DQN.
  - **Direct Baselines**: Random agent runs for benchmarking.

---

## Results

### 1. Performance Comparison

| Experiment                 | Coverage (20 steps) | Coverage (30 steps) | Coverage Heatmap | Notable Behaviors           |
|----------------------------|---------------------|---------------------|------------------|-----------------------------|
| Single-Agent (Random)      | 5/36                | 10/36               | Baseline         | Limited, repetitive paths   |
| Swarm (2 Agents, Random)   | 18/36               | 25+/36              | Baseline         | Superior, distributed       |
| PPO (Single-Agent)         | ~Moderate           | ~Moderate           | Heatmap          | Safe, local loops           |
| DQN (Single-Agent)         | ~Moderate           | ~Moderate           | Heatmap          | Local optima, avoids risks  |

### 2. Visual Outputs

- **Animated Trajectories:**  
  All agent and swarm rollouts are visualized and exported as GIF/MP4 (`/results/`).
- **Coverage Over Time:**  
  Plots demonstrate swarm coverage is 3x faster than solo agent.
- **Reward Curves:**  
  PPO/DQN learning dynamics, with clear convergence and diagnostic dips.
- **Inter-Agent Collision Analysis:**  
  Swarm rollout plots and logs include collision events for research transparency.

---

## Quick Start

1. **Install dependencies:**  
   ```bash
   pip install -r requirements.txt
   
2. Open SwarmNavigator.ipynb in Jupyter Notebook or Google Colab.

3. Run all cells:
All visual outputs and logs will be generated and saved to /results/, dqn_logs/, ppo_logs/, and ppo_swarm_logs/.

4. Review outputs:
Use the notebook or log folders to inspect coverage plots, GIFs/MP4s, and training logs.

5. Extend:
The code is modular for additional agents, reward functions, or RL algorithms.

---

## Technical Stack

- Python 3.10+
- Jupyter Notebook (local or Colab)
- Stable-Baselines3, Gymnasium
- Numpy, Matplotlib, Seaborn, Pillow, OpenCV, TQDM

---

## Author

**Ayushman Mishra**  
Robotics & Reinforcement Learning Engineer  
Arizona State University  
[GitHub: frMishR](https://github.com/frMishR)  
Email (University): [amish141@asu.edu]  
Email (Personal): [4yxmi0@gmail.com]

---

## Limitations & Future Directions

- Exploration:  
Current RL policies may converge to local optima in sparse reward settings. Future work includes intrinsic exploration, curriculum learning, and attention-based communication.
- Scalability:  
Demonstrated for up to 4 agents; future work to extend to larger swarms and grids.
- Real Robot Deployment:  
Next phase: port trained policies to ROS2 and integrate with vision/perception modules.
- Inter-Agent Communication:  
Explicit coordination to boost coverage and reduce collisions.

---

## License

MIT License. See `LICENSE` for details.

---

## Project Summary Table

| Metric                  | Value                     |
|-------------------------|---------------------------|
| Total Lines of Code     | ~900+                     |
| RL Algorithms           | PPO, DQN, Random Baseline |
| Max Swarm Size          | 4 Agents (parallel)       |
| Visualization Outputs   | 20+ (plots, GIFs, MP4)    |
| Training Log Folders    | dqn_logs, ppo_logs, ppo_swarm_logs |
| Project Duration        | ~9–11 hours (core to polish) |
| Reproducibility         | 100% (Colab/local, no data needed) |

---

For further details, see `SwarmNavigator.ipynb` or contact the author.
