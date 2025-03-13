# Texas Hold'em Deep RL

This repository contains a collection of poker agents built and tested in [RLCard](https://github.com/datamllab/rlcard). The agents range from upgraded CFR implementations (including CFR+ with baseline and state abstraction) to a PPO+LSTM approach for partially observable settings. Additionally, an NFSP agent is provided as a baseline for comparison.

## Contents

- **`NFSP_agents.ipynb`**  
  Demonstrates how to train and evaluate a Neural Fictitious Self-Play (NFSP) agent in Leduc Hold’em.
  
- **`texas_holdem_agents.ipynb`**  
  Contains various CFR-based and PPO+LSTM agents, as well as evaluation routines and tournament comparisons against random or CFR opponents.

- **`texas_holdem_agents.html`**  
  An HTML export of the above notebook.

- **`experiments/`**  
  Folders for saving model checkpoints, training logs, and performance plots. For example:
  - `leduc_holdem_cfr_result/`
  - `leduc_holdem_cfr_plus_baseline_abstract_result/`
  - `leduc_holdem_ppo_lstm_result/`
  - etc.

## Features

1. **CFR+ with Baseline and State Abstraction**  
   - Incorporates KMeans-based state abstraction to cluster similar states.
   - Uses a baseline for variance reduction.

2. **NFSP (Neural Fictitious Self-Play)**  
   - Combines reinforcement learning (DQN) and supervised learning (average policy) to approximate a Nash equilibrium in Leduc Hold’em.

3. **PPO+LSTM**  
   - Policy gradient approach (Proximal Policy Optimization) with an LSTM for handling partial observability.
   - Trains on entire episodes, normalizes advantages, and includes an entropy bonus for exploration.

4. **Comparison Utilities**  
   - `compare_models()` function for head-to-head matchups, seating swaps, and averaged rewards.

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/YourUsername/texas-holdem-deep-rl.git
   ```
2. Install dependencies (e.g., RLCard, PyTorch, scikit-learn) if not already present:
   ```bash
   pip install rlcard torch scikit-learn
   ```
3. Run the Jupyter notebooks or Python scripts to train and evaluate agents:
   ```bash
   cd texas-holdem-deep-rl
   jupyter notebook
   ```
   Then open `NFSP_agents.ipynb` or `texas_holdem_agents.ipynb`.

## Usage

1. **Training:**  
   - Inside `texas_holdem_agents.ipynb`, select the agent you want (e.g., `CFRPlusAgentWithBaselineAbstract` or `PPOAgentWithLSTM`) and run the training cells.  
   - Model checkpoints and logs will be saved in `experiments/`.

2. **Evaluation and Comparison:**  
   - Use `tournament()` from RLCard to measure average reward against a random or known baseline agent.  
   - The `compare_models()` function helps you compare two agents by swapping seating positions and averaging results.

3. **Logging and Plotting:**  
   - RLCard’s `Logger` automatically logs performance metrics to CSV.  
   - Use `plot_curve` to generate reward curves over time.

## Future Work

- **Professional-Level Agents:**  
  Ongoing efforts to integrate more advanced techniques (e.g., large-scale self-play, advanced exploration, or deep CFR variants) for professional-level play.
- **Parallelization:**  
  Speeding up training by running multiple environments in parallel.
- **Full Texas Hold’em:**  
  Current examples focus on Leduc (2-player limit). Adapting to larger variants (e.g., No-Limit Texas Hold’em) will require bigger networks and more training data.

## Contributing

Pull requests and issues are welcome! Feel free to suggest improvements or add new agents.

## License

This project is licensed under the [Apache 2.0 License](LICENSE) (or whichever license you prefer).
