# Applied Reinforcement Learning Bootcamp

A comprehensive educational repository containing all materials for mastering reinforcement learning concepts, from fundamentals to advanced applications.

## Overview

This repository contains Jupyter notebooks, code examples, assignments, and resources for the Applied Reinforcement Learning Bootcamp. The content is organized in a progressive manner, starting from the basics and building towards advanced topics.

## Repository Structure

The repository is organized into the following main sections:

1. **00-Prerequisites**: Mathematics, Python, and other prerequisites
2. **01-Fundamentals-of-Sequential-Decision-Making**: Core concepts and frameworks
3. **02-Introduction-to-RL**: Basic reinforcement learning algorithms and methods
4. **03-RL-for-Price-Optimization**: Applying RL to pricing strategies and optimization
5. **04-RL-for-LLMs**: Reinforcement learning in large language models
6. **05-RL-for-Agentic-AI**: RL techniques for autonomous agents and systems
7. **06-Summary**: Review and synthesis of concepts

## Getting Started

1. Clone this repository
2. Set up your Python environment using the requirements file
3. Navigate to the notebooks in order, starting with the prerequisites

## Dependencies

See `requirements.txt` for the required Python packages.

## License

See the [LICENSE](LICENSE) file for details.

# Asset Selling Problem Implementation

This repository contains a Python implementation of the asset selling problem as described in the provided text. The asset selling problem explores optimal strategies for selling assets (such as stocks or real estate) over time to maximize returns.

## Overview

In the asset selling problem, an agent holds a single share of stock and must decide when to sell it to maximize the expected return. The price of the stock evolves according to a stochastic process over time. Once the stock is sold, the process stops.

### Basic Model Components

- **State Variables**: 
  - `Rt` - Physical state (1 if still holding the stock, 0 if sold)
  - `pt` - Price of the stock at time t
  - In time series models, previous prices are also included in the state

- **Decision Variable**:
  - `xt` - Action (1 if we sell the stock, 0 if we hold it)

- **Transition Function**:
  - `Rt+1 = Rt - xt` - Stock holding updates
  - `pt+1 = pt + price_change` - Price evolution

- **Objective Function**:
  - Maximize the price at which we sell the stock

## Implementation

The implementation is structured into three main Python files:

1. `asset_selling_problem.py` - Core implementation of the problem, including price simulation, policy evaluation, and visualization.
2. `selling_policies.py` - Various selling policies (strategies) for deciding when to sell.
3. `run_asset_selling.py` - Demo script that runs experiments and generates visualizations.

### Price Models

Two price evolution models are implemented:

1. **Normal Distribution Model**: Price changes follow a normal distribution with specified mean and standard deviation.
2. **Time Series Model**: Price evolves according to an AR(3) model, including autocorrelation over time.

### Selling Policies

Several selling policies are implemented, including:

- **Sell Immediately**: Always sell at the first time step.
- **Sell at End**: Hold until the end, then sell.
- **Sell Low**: Sell if the price drops below a threshold.
- **High-Low**: Sell if the price is outside specified bounds (too high or too low).
- **Tracking**: Sell when the price exceeds a moving average by a threshold.
- **Momentum**: Sell based on price momentum.
- **Optimal Stopping**: Policy based on backward induction for optimal stopping.
- **Dynamic Threshold**: Time-varying threshold that changes as we approach the horizon.
- **Random Policy**: Sell with a fixed probability at each time step.

## Usage

To run the demo script:

```bash
python run_asset_selling.py
```

This will:
1. Generate sample price paths
2. Compare different selling policies
3. Perform parameter sensitivity analysis
4. Compare performance across different price models

## Customization

You can customize the implementation by:

1. Modifying existing policies or adding new ones in `selling_policies.py`
2. Adjusting parameters in `run_asset_selling.py`
3. Extending the `AssetSellingProblem` class in `asset_selling_problem.py` with new features

## Dependencies

- NumPy
- Matplotlib
- Pandas

## Extensions

Possible extensions to this implementation include:

1. More sophisticated price models (e.g., jump diffusion)
2. Transaction costs
3. Risk-sensitive objectives
4. Multiple assets (portfolio management)
5. Deep reinforcement learning approaches
