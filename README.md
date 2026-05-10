# SOVEREIGN Game: Geopolitical Deep Reinforcement Learning

This repository contains the implementation and experimental results for the SOVEREIGN Game, a custom Deep Reinforcement Learning (DRL) geopolitical simulation environment built using Gymnasium and Stable-Baselines3.

## Project Overview

The core research question of this project is: **Can a militarily superior agent learn, through experience alone, that invasion is a strategically dominated strategy?**

The environment models a 3-Nation conflict:
*   **Invader (The RL Agent)**: Starts with a hard-power advantage (2x military units).
*   **Defender**: A rule-based opponent with a home-turf advantage.
*   **Neutral**: A stochastic observer whose political posture is governed by a mathematical drift-diffusion model, shifting based on the Invader's actions.

The agent uses **Proximal Policy Optimization (PPO)** to navigate a multi-dimensional state space and a MultiDiscrete action space, balancing military conquest against political legitimacy, economic sanctions, and occupation costs.

## Repository Structure

*   `SOVEREIGN_Game_Standalone_executed.ipynb`: The primary executable Jupyter Notebook. It contains the complete `SovereignEnv` Gymnasium environment, the PPO training loop, the ablation study implementation, and the generated evaluation graphs.
*   `SOVEREIGN_Project_Documentation.md`: Detailed documentation covering the theoretical RL framework, environment dynamics, and analysis of emergent behaviors.
*   `experiment_results.json`: Raw numerical output from the ablation experiments.
*   `sovereign_map.png`: Visualization of the 9-territory map topology.
*   `experiment_results.png`: Bar chart visualizing action frequencies across ablation tests.
*   `SOVEREIGN_Presentation.pptx`: The final slide deck presentation summarizing the project.

## How to Execute

To run the simulation and reproduce the experiments:

1.  **Environment Setup**: Ensure you have a Python environment with the required dependencies:
    ```bash
    pip install gymnasium stable-baselines3 numpy matplotlib
    ```
2.  **Running the Code**:
    *   Open `SOVEREIGN_Game_Standalone_executed.ipynb` in Jupyter Notebook, JupyterLab, or Google Colab.
    *   Execute the cells sequentially from top to bottom.
    *   The notebook is self-contained. It will define the environment, train the models for the 5 ablation regimes, evaluate them, and automatically plot the resulting bar charts.

## Key Results

Our experiments demonstrate the emergence of a **Peace-Dominant Policy**. When all political and economic consequences are active (Full Model), the agent mathematically recognizes that the long-term costs of war (sanctions and legitimacy drops) outweigh the short-term benefits of captured resources. It learns to rely exclusively on diplomacy (`NEGOTIATE` frequency ~100%). However, when these consequences are ablated (Baseline Model), the agent reverts to pure military conquest.
