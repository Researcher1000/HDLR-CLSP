---
title: "Code Repository – Hierarchical Deep Reinforcement Learning for CLSP"
output: html_document
---

# Purpose of this repository

This repository contains the **implementation used in the experiments of the article**  
*“Hierarchical Deep Reinforcement Learning for Capacitated Lot-Sizing Problem: From Stochastic Multi-Item to Sequence-Dependent Setups”* :contentReference[oaicite:1]{index=1}.

The code reproduces the Hierarchical Deep Reinforcement Learning (HDRL) framework proposed in the paper and the benchmark heuristics used for comparison.

The repository allows the reviewer to:

- run the **hierarchical PPO training procedure**,
- generate the **S-CLSP and S-CLSP-SD benchmark instances** used in the study,
- evaluate the learned policies,
- run the **AMBS benchmark heuristics** used in the comparisons.

---

# Repository structure
├── main.py
├── CLSP_HDRL/
│ ├── algo_ppo_hier.py
│ ├── algo_ppo_hier2.py
│ ├── buffers.py
│ ├── dists.py
│ ├── envs.py
│ ├── envs2.py
│ ├── nets.py
│ └── init.py
├── AMBS_SCLSP.ipynb
├── AMBS_SCLSP_SD.ipynb
└── README.Rmd


---

# Main components

## `main.ipynb`

Main script used to **train and evaluate the HDRL agent**.

It:

1. selects a benchmark instance,
2. builds the environment,
3. trains the hierarchical PPO agents,
4. evaluates the learned policy.

---

## `CLSP_HDRL/`

Core implementation of the hierarchical reinforcement learning framework.

- **`algo_ppo_hier.py`**  
  PPO implementation for the hierarchical agent in the **S-CLSP environment**.

- **`algo_ppo_hier2.py`**  
  PPO implementation adapted to the **sequence-dependent setup environment (S-CLSP-SD)**.

- **`envs.py`**  
  Environment definition for the **S-CLSP** benchmark.

- **`envs2.py`**  
  Environment definition for the **S-CLSP-SD** benchmark.

- **`nets.py`**  
  Neural network architectures used by the high-level and low-level agents.

- **`buffers.py`**  
  Experience buffers used during PPO training.

- **`dists.py`**  
  Action distributions used by the policies.

---

## Benchmark heuristics

Two notebooks implement the heuristics used as baselines in the paper:

- **`AMBS_SCLSP.ipynb`**  
  Implementation of the **AMBS heuristic** for the stochastic CLSP.

- **`AMBS_SCLSP_SD.ipynb`**  
  Adapted AMBS heuristic that incorporates **sequence-dependent setups**.

These scripts reproduce the benchmark policies used in the experimental comparison.

---

# Running an experiment

To reproduce an experiment, edit in `main.ipynb`:
INSTANCE_ID = "1.1"
VARIANT = "optimized"

And run it with the desired instance and setup variant.


The script trains the hierarchical agents and evaluates the resulting policy over multiple simulation runs.

---

# Notes for reviewers

- The repository contains **the full experimental implementation** used in the paper.
- Benchmark instances follow the generation procedures described in the article.
- Training and evaluation settings correspond to the **baseline and optimized configurations reported in the experimental section**.
