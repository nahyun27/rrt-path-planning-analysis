# RRT Path Planning Analysis

This project presents a comparative analysis of sampling-based path planning algorithms including **RRT**, **RRT\***, and **Dubins RRT**.

The goal is to evaluate algorithm performance under different environments, parameter settings, and motion constraints.

The experiments analyze:

- Path planning success rate
- Path cost (Euclidean distance)
- Path stability
- Parameter sensitivity
- Motion feasibility

---

## Algorithms

### RRT (Rapidly-exploring Random Tree)

RRT is a sampling-based path planning algorithm designed for fast exploration of configuration space.  
It efficiently finds feasible paths but does not guarantee optimality.

### RRT*

RRT* improves RRT by introducing a **rewiring process** that locally optimizes the tree structure.  
This results in shorter and more stable paths.

### Dubins RRT

Dubins RRT extends RRT by considering **non-holonomic motion constraints**.

It generates physically feasible paths by limiting the turning radius and producing smooth trajectories.

---

## Experiment Overview

The project consists of four experimental tasks.

---

## Task 1 — Baseline Experiment

Baseline comparison between RRT and RRT* in the same environment.

### Setup

- Start: (0, 0)
- Goal: (12, 10)
- Search Area: [-2, 14]
- Robot radius: 0.8
- Obstacles: 9 circular obstacles blocking the straight path
- Trials: 30 runs per algorithm

### Parameters

- Expand distance: 1.5
- Goal sample rate: 5%
- Max iterations: 500

### Metrics

- Success rate
- Path cost
- Standard deviation
- Median

### Results

- Both algorithms achieved 100% success rate
- RRT* produced shorter paths
- RRT* showed fewer outliers
- RRT* demonstrated better path stability

---

## Task 2 — Scenario Variation Experiment

Performance comparison under different environment complexities.

### Scenarios

#### Scenario A — Narrow Passage

Environment with a narrow corridor restricting movement.

- Lower success rate observed
- RRT* achieved about 3% higher success rate

#### Scenario B — Dense Obstacles

Environment with many obstacles.

- Both algorithms achieved 100% success rate
- RRT* generated shorter and more consistent paths

#### Scenario C — Long Range Planning

Long-distance planning with multiple obstacles.

- Both algorithms achieved stable convergence
- RRT* maintained better path quality

### Results

- RRT* produced paths 0.4–1.0 units shorter on average
- Dense obstacle environments showed up to 2% improvement
- Narrow passage showed higher variability

---

## Task 3 — Hyperparameter Sensitivity Analysis

Performance analysis with different parameter settings.

### Environment

Narrow passage configuration.

### Parameters Tested

- Expand distance:

1.0, 2.0, 3.0, 4.0, 5.0


- Goal sample rate:

2, 5, 10, 15, 20


### Trials

- 30 runs per configuration
- 25 parameter combinations

### Metrics

- Success rate
- Path cost
- Runtime

### Results

- Expand distance strongly affected success rate
- Small expand distance reduced RRT success rate to ~70%
- RRT* maintained 80–100% success rate

Best parameter range:

- expand_distance = 3–4
- goal_sample_rate = 10–15


RRT* showed more stable performance across parameter changes.

---

## Task 4 — Dubins Steering Experiment

Evaluation of RRT with Dubins steering constraints.

### Setup

- Start: (0, 0)
- Goal: (14, 10)
- Search Area: [-2, 18]
- Robot radius: 0.8
- Expand distance: 1.0
- Goal sample rate: 3%
- Max iterations: 500

### Dubins Parameter

Turning radius = 2.0


### Environment

Complex environment with asymmetric obstacles and narrow passages.

### Trials

30 runs per algorithm.

### Metrics

- Success rate
- Path cost
- Runtime

### Results

- Both algorithms achieved 100% success rate
- Dubins RRT reduced path cost by about 2–3%
- Paths were smoother and more realistic
- Lower variance in path length

---

## Key Findings

### RRT

- Fast exploration
- Higher variance in path length
- Less stable path quality

### RRT*

- Shorter paths
- More stable performance
- Robust to parameter changes
- Better global optimality

### Dubins RRT

- Smooth trajectories
- Physically feasible paths
- Improved path consistency

---

## Requirements

numpy
matplotlib


Install:

```bash
pip install numpy matplotlib
```
