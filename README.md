# Smart Multimodal Mobility — Vehicle Routing Problem Optimization

> A Python-based VRP solver developed for ADEME's call for innovative mobility solutions, optimizing delivery routes to reduce energy consumption and CO₂ emissions.

---

## Table of Contents

- [Overview](#overview)
- [Objectives](#objectives)
- [Features](#features)
- [Technical Stack](#technical-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Methodology](#methodology)
- [Results & Performance](#results--performance)
- [Environmental Impact](#environmental-impact)
- [Contributors](#contributors)
- [License](#license)
- [References](#references)

---

## Overview

This project addresses the Vehicle Routing Problem (VRP) in urban and suburban environments. The solver calculates optimal delivery routes on road networks — connecting multiple delivery points and returning to the starting depot — while minimizing total travel time and respecting real-world logistical constraints.

---

## Objectives

| Goal | Description |
|------|-------------|
| **Scale** | Handle large-scale instances (1,000+ cities) |
| **Environment** | Reduce CO₂ emissions through optimized routing |
| **Applicability** | Support mail distribution, product delivery, waste collection |

---

## Features

### Basic Version
- Route optimization for delivery networks
- Support for instances with several thousand cities
- Statistical performance analysis
- Benchmark validation using CVRPLIB

### Additional Constraints (2+ implemented)

| Constraint | Basic Version | Advanced Version |
|------------|---------------|------------------|
| Time Windows | No delivery outside time window | Waiting allowed before opening |
| Heterogeneous Fleet | k identical trucks | 3D capacity + compatibility constraints |
| Dynamic Traffic | Constant travel time | Variable distance matrix per time slot |
| Pickup Points | Single depot | Multi-depot + object-specific constraints |

---

## Technical Stack

- **Language:** Python 3.8+
- **Key Libraries:**
  - `vrplib` — Benchmark instance management
  - `numpy` — Numerical computations
  - `matplotlib` — Visualization
  - `pandas` — Data analysis

---

## Project Structure

```
smart-mobility-vrp/
├── notebooks/
│   ├── 01_modeling.ipynb            # Formal problem modeling
│   ├── 02_implementation.ipynb      # Algorithm implementation
│   └── 03_experimental_study.ipynb  # Performance analysis
├── src/
│   ├── solver.py                    # Main VRP solver
│   ├── algorithms/                  # Metaheuristic implementations
│   ├── constraints/                 # Constraint handlers
│   └── utils.py                     # Helper functions
├── experiments/
│   ├── experiments.py               # Experimental design
│   └── analysis.py                  # Statistical analysis
├── data/
│   └── instances/                   # Test instances
├── results/
│   ├── convergence/                 # Convergence curves
│   └── statistics/                  # Performance statistics
├── requirements.txt
└── README.md
```

---

## Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/smart-mobility-vrp.git
cd smart-mobility-vrp

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

---

## Usage

### Basic Example

```python
import vrplib
from solver import solve_vrp

# Load instance
instance = vrplib.download_instance("X-n101-k25.vrp")

# Solve
solution = solve_vrp(instance)

# Evaluate performance
optimal_sol = vrplib.download_solution("X-n101-k25.sol")
gap = 100 * (solution["cost"] - optimal_sol["cost"]) / optimal_sol["cost"]
print(f"Gap vs reference: {gap:.2f}%")
```

### Running Experiments

```bash
# Run full experimental study
python experiments.py --instances A-n32-k5 X-n101-k25 M-n200-k17 --runs 20

# Generate performance reports
python analysis.py --output results/
```

---

## Methodology

### 1. Formal Modeling
- Mathematical formulation of the VRP
- Complexity analysis (NP-hard problem)
- Constraint integration

### 2. Solution Approach

Choose one metaheuristic:
- Simulated Annealing
- Tabu Search
- Adaptive Large Neighborhood Search (ALNS)

### 3. Experimental Validation
- Test on growing instances (50 → 2,000 clients)
- Generate convergence curves
- Statistical analysis (20 runs per instance)
- Comparison with CVRPLIB benchmarks

---

## Results & Performance

| Instance | Optimum Cost | Our Cost | Gap (%) | Time (s) |
|----------|-------------|----------|---------|----------|
| A-n32-k5 | 784 | 812 | 3.57% | 45.2 |
| X-n101-k25 | 27,591 | 28,995 | 5.09% | 182.7 |

> **Target:** Average gap < 7% on instances with fewer than 200 customers.

The experimental study includes:
- **Convergence analysis** — solution quality over iterations
- **Scalability study** — performance on growing instance sizes
- **Statistical validation** — boxplots showing solution distribution
- **Gap analysis** — comparison with optimal/best-known solutions

---

## Environmental Impact

This project contributes to:
- Reduction of CO₂ emissions through optimized routing
- Fuel consumption optimization via shorter travel distances
- Traffic congestion reduction through better route planning

---

## Contributors

Developed by the **CesiCDP team** in response to ADEME's call for innovative mobility solutions.

---

## License

This project is licensed under the [MIT License](LICENSE).

---

## References

- [CVRPLIB — VRP Benchmark Library](http://vrp.atd-lab.inf.puc-rio.br/)
- [vrplib Python Package](https://pypi.org/project/vrplib/)
- [PEP 8 Style Guide](https://peps.python.org/pep-0008/)

---

*For questions or collaboration opportunities, please open an issue or contact the team.*
