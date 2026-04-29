# Smart Multimodal Mobility — VRP Optimization

A Python-based VRP solver developed for ADEME's call for innovative mobility solutions, optimizing delivery routes to reduce energy consumption and CO₂ emissions.

---

## Table of Contents

* Overview
* Objectives
* Features
* Technical Stack
* Project Structure
* Installation
* Usage
* Methodology
* Results & Performance
* Environmental Impact
* Contributors
* License
* References

---

## Overview

This project addresses the Vehicle Routing Problem (VRP) in urban and suburban environments. The solver computes optimal delivery routes connecting multiple delivery points while returning to a central depot, minimizing travel cost and respecting real-world constraints.

---

## Objectives

| Goal          | Description                                                               |
| ------------- | ------------------------------------------------------------------------- |
| Scale         | Handle large-scale instances (1,000+ cities)                              |
| Environment   | Reduce CO₂ emissions through optimized routing                            |
| Applicability | Support logistics use cases (delivery, waste collection, postal services) |

---

## Features

### Basic Version

* Route optimization for delivery networks
* Support for large VRP instances
* Performance evaluation tools
* Benchmark validation using CVRPLIB

### Advanced Constraints

| Constraint   | Basic Version           | Advanced Version                     |
| ------------ | ----------------------- | ------------------------------------ |
| Time Windows | Strict delivery windows | Waiting allowed before opening       |
| Fleet        | Identical vehicles      | Heterogeneous fleet with constraints |
| Traffic      | Static travel times     | Time-dependent travel matrix         |
| Depots       | Single depot            | Multi-depot support                  |

---

## Technical Stack

* **Language:** Python 3.8+
* **Libraries:**

  * `vrplib` — Benchmark instance handling
  * `numpy` — Numerical computations
  * `pandas` — Data processing
  * `matplotlib` — Visualization

---

## Project Structure

```
smart-mobility-vrp/
├── docs/
│   ├── resources/
│   │   └── advanced_algorithms.pdf     # Theoretical background
│   └── diagrams/
│       └── use_case_diagram.png        # System design
│
├── instances/
│   ├── A-n32-k5.vrp                   # Benchmark instance
│   ├── X-n101-k25.vrp                 # Larger instance
│   └── Generated.vrplib               # Custom generated instance
│
├── notebook/
│   └── final_deliverable.ipynb        # Main implementation & experiments
│
└── README.md
```

---

## Installation

```bash
# Clone repository
git clone https://github.com/yourusername/smart-mobility-vrp.git
cd smart-mobility-vrp

# Create virtual environment
python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate

# Install dependencies
pip install numpy pandas matplotlib vrplib
```

---

## Usage

### Run via Notebook (Recommended)

```bash
jupyter notebook notebook/final_deliverable.ipynb
```

The notebook contains:

* Problem modeling
* Algorithm implementation
* Experimental evaluation

---

### Example (inside notebook)

```python
import vrplib

# Load instance
instance = vrplib.read_instance("instances/X-n101-k25.vrp")

# Solve (implementation inside notebook)
solution = solve_vrp(instance)

print(solution)
```

---

## Methodology

### 1. Problem Modeling

* Formal VRP definition
* Constraints integration
* NP-hard complexity analysis

### 2. Solution Approach

Metaheuristics explored:

* Simulated Annealing
* Tabu Search
* Adaptive Large Neighborhood Search (ALNS)

### 3. Experimental Validation

* Benchmark testing (CVRPLIB)
* Multiple runs per instance
* Convergence analysis
* Performance comparison

---

## Results & Performance

| Instance   | Optimum | Our Cost | Gap (%) | Time (s) |
| ---------- | ------- | -------- | ------- | -------- |
| A-n32-k5   | 784     | 812      | 3.57%   | 45.2     |
| X-n101-k25 | 27,591  | 28,995   | 5.09%   | 182.7    |

**Target:** Average gap < 7% for instances under 200 customers.

---

## Environmental Impact

This project contributes to:

* Reduced CO₂ emissions
* Lower fuel consumption
* Improved traffic efficiency
* Smarter urban logistics

---

## Contributors

Developed by the **CesiCDP team** for ADEME’s innovative mobility initiative.

---

## License

This project is licensed under the MIT License.

---

## References

* CVRPLIB — Vehicle Routing Benchmark Library
* vrplib Python Package
* PEP 8 Style Guide
