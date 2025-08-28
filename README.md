# Single Agent Robust Deep Reinforcement Learning for Bus Fleet Control

This project implements a Single Agent Robust Deep Reinforcement Learning approach for Bus Fleet Control using Soft Actor-Critic (SAC) algorithm. This work is associated with the paper "Single Agent Robust Deep Reinforcement Learning for Bus Fleet Control".

## Paper

📄 **ArXiv**: https://arxiv.org/submit/6745266/view

## Overview

This project uses deep reinforcement learning to optimize bus fleet operations, focusing on reducing bus bunching and improving service reliability through intelligent holding strategies. The implementation is based on the Soft Actor-Critic (SAC) algorithm and builds upon the foundation from [LSTM-RL](https://github.com/maywind23/LSTM-RL).

## Features

- **SAC v2 Implementation**: Advanced Soft Actor-Critic with automatic entropy tuning
- **Bus Fleet Simulation**: Comprehensive bus route simulation environment
- **Holding Strategy Optimization**: Learn optimal bus holding decisions to prevent bunching
- **Visualization Tools**: Generate plots for trajectory analysis, headway variance, and bunching events
- **Policy Evaluation**: Evaluate trained policies with detailed event recording

## Project Structure

```
├── env/                          # Simulation environment
│   ├── sim.py                   # Main simulation environment
│   ├── bus.py                   # Bus agent implementation
│   ├── route.py                 # Route management
│   ├── station.py               # Station/stop implementation
│   ├── passenger.py             # Passenger demand modeling
│   ├── timetable.py             # Schedule management
│   ├── visualize.py             # Visualization utilities
│   ├── config.json              # Environment configuration
│   └── data/                    # Route and passenger data
├── sac_v2_bus.py               # Main SAC training script
├── evaluate_policy_with_holding.py  # Policy evaluation with event tracking
├── normalization.py            # State/reward normalization utilities
├── plot_bunching.py            # Bunching analysis visualization
├── requirements.txt            # Python dependencies
└── model/                      # Saved model checkpoints
```

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd Catetorical-Feature-SAC-in-bus-simulation
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```

## Usage

### Training

To train the SAC agent, simply run:

```bash
python sac_v2_bus.py
```

The script supports various command-line arguments for customization:

- `--train`: Enable training mode (default: True)
- `--test`: Enable testing mode (default: False)
- `--use_gradient_clip`: Use gradient clipping (default: True)
- `--use_state_norm`: Use state normalization (default: False)
- `--use_reward_norm`: Use reward normalization (default: False)
- `--use_reward_scaling`: Use reward scaling (default: False)
- `--gamma`: Discount factor (default: 0.99)
- `--batch_size`: Training batch size (default: 2048)
- `--max_episodes`: Maximum training episodes (default: 500)
- `--weight_reg`: L2 regularization weight (default: 0.1)
- `--auto_entropy`: Automatic entropy tuning (default: True)
- `--maximum_alpha`: Maximum entropy coefficient (default: 0.3)

### Evaluation

To evaluate a trained policy and record holding events:

```bash
python evaluate_policy_with_holding.py
```

This will generate detailed logs of holding decisions and their impacts on service quality.

### Visualization

Use the plotting utilities to analyze results:

```bash
python plot_bunching.py
```

## Environment Configuration

The simulation environment is configured through `env/config.json`. Key parameters include:

- Route topology and station locations
- Passenger demand patterns
- Service frequency and scheduling
- Reward function parameters

## Model Architecture

The SAC implementation includes:

- **Actor Network**: Policy network with tanh-squashed Gaussian outputs
- **Critic Networks**: Twin Q-networks for value estimation
- **Target Networks**: Soft-updated target networks for stability
- **Automatic Entropy Tuning**: Adaptive temperature parameter

## Results

The model generates various visualization outputs:

- **Bus Trajectories**: Space-time diagrams showing bus movements
- **Headway Analysis**: Service regularity metrics
- **Bunching Events**: Detection and analysis of bus bunching
- **Holding Records**: Log of all holding decisions and their effects

Results are saved in the `env/pic/` directory with detailed CSV logs and visualization plots.

## Citation

If you use this code in your research, please cite:

```bibtex
@article{your_paper_2024,
  title={Single Agent Robust Deep Reinforcement Learning for Bus Fleet Control},
  author={Your Name},
  journal={ArXiv preprint},
  year={2024},
  url={https://arxiv.org/submit/6745266/view}
}
```

## Acknowledgments

This project builds upon the foundation provided by [LSTM-RL](https://github.com/maywind23/LSTM-RL). We thank the original authors for their contributions to the field.

## License

This project is licensed under the same terms as the original LSTM-RL repository.