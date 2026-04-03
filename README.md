# Airline Scheduling Optimization

## Overview
This project builds an optimization-based decision agent for Southwest Airlines that solves the crew scheduling tradeoff between minimizing labor costs and maximizing schedule resilience. Using synthetic data modeled on real FAA regulations and Southwest's route network, it calculates the Pareto frontier of optimal crew pairing solutions and recommends the best option based on business constraints. The agent explains its reasoning in plain language so airline operations leaders can act on it quickly.

## Business Problem
Southwest Airlines' single largest operating expense is labor at roughly 40% of total costs, and how crews are scheduled directly determines both profitability and reliability. The December 2022 meltdown, with 16,700 cancellations and over $800M in losses, showed exactly what happens when a crew scheduling system optimizes purely for cost efficiency with no resilience built in. This project models that tradeoff and builds a smarter decision tool to balance both objectives.

## Status
✅ Part 1: Optimization Engine (Complete)

🚧 Part 2: Constraint-Aware Decision Agent (Coming Soon)

## Technologies
- Python
- Pandas
- NumPy
- Matplotlib
- Jupyter Notebook

---

## Setup

Install dependencies:
```bash
pip install -r requirements.txt
```

---

## Part 1: Optimization Engine (Complete ✓)

### What It Does
This optimization engine analyzes **100 possible combinations** of crew utilization rate (60–95%) and reserve buffer size (2–20 crews) to identify the Pareto frontier of efficient solutions that balance **crew cost efficiency** vs **schedule resilience and disruption recovery**.

### Key Findings
- **16%** of solutions are Pareto optimal (16 out of 100)
- **84 dominated solutions** were identified and should be avoided. Each has a strictly better alternative available on the frontier
- Key strategic points identified on the frontier:

| Strategy | Utilization Rate | Reserve Buffer | Cost Efficiency | Resilience Score |
|---|---|---|---|---|
| Cost Efficiency Priority | 87.17% | 2 crews | 93.5 | 1.9 |
| Weighted (60% cost / 40% resilience) | 85.58% | 7 crews | 81.5 | 26.2 |
| Balanced (max combined score) | 72.97% | 15 crews | 45.7 | 68.6 |
| Equity (scores most equal) | 87.03% | 19 crews | 54.5 | 56.9 |
| Resilience Priority | 68.63% | 19 crews | 20.7 | 89.7 |

### Running the Analysis
1. Ensure you have the required packages: `pandas`, `numpy`, `matplotlib`
2. Open `optimization_engine.ipynb`
3. Run all cells in order
4. Outputs will be saved to the `images/` folder

### Next Steps
Part 2 will add a constraint-aware decision agent that selects among these Pareto optimal solutions based on business constraints and priorities.

---

## Setup
Install dependencies:
```bash
pip install -r requirements.txt
```

## Repository Structure
```
airline_scheduling_optimization/
├── optimization_engine.ipynb       # Main analysis notebook
├── data/
│   ├── data_generation_prompt.txt  # Prompt to create synthetic dataset
│   └── sw_crew_scheduling.csv      # Synthetic 100-solution dataset
├── images/
│   ├── data_exploration.png
│   └── pareto_frontier_analysis.png
├── requirements.txt
└── README.md
```