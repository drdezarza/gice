# LLM-Mediated Demand Response Coordination in Smart Microgrids


## Overview

The work addresses a core challenge in next-generation smart city energy systems: how to coordinate voluntary demand curtailment among heterogeneous prosumers — residential and commercial agents who both consume and produce electricity — when individual incentives favour free-riding over collective grid stability. This coordination problem is structurally equivalent to a repeated Prisoner's Dilemma on a social network, and we instantiate it on a Barabási–Albert scale-free topology reflecting real urban energy community structure.

The central contribution is a **hybrid decision architecture** that decouples game-theoretic base probability (derived from payoff history, exploitation memory, and conformist neighbourhood imitation) from LLM narrative evaluation of incoming demand-response directives. This separation resolves a critical methodological challenge: RLHF-aligned language models exhibit overwhelming cooperation bias when used as direct decision-makers, collapsing all experimental conditions to near-identical dynamics regardless of grid state. By confining the LLM to a scalar narrative shift δ ∈ [−0.30, +0.30] rather than a binary curtailment decision, the architecture preserves genuine strategic tension across six prosumer personality archetypes — pragmatist, idealist, skeptic, conformist, strategist, and opportunist.

A central **LLM Influence Compiler** — abstracting the role of a demand-response aggregator or distribution system operator — observes a noisy population snapshot and compiles structured directives via a Solver–Critic pipeline, targeting high-centrality network nodes every Δt = 5 steps. 

---

## Repository Structure

```
gice/
├── gice_nebius_v3.ipynb          # Main simulation notebook (all 4 experiments)
├── data/
│   ├── exp1_compiled_timeseries.csv
│   ├── exp1_unstructured_timeseries.csv
│   ├── exp1_no_influence_timeseries.csv
│   ├── exp2_id_compiled_timeseries.csv
│   ├── exp2_id_unstructured_timeseries.csv
│   ├── exp2_id_noinfl_timeseries.csv
│   ├── exp3_hubs_timeseries.csv
│   ├── exp3_bridges_timeseries.csv
│   ├── exp3_random_timeseries.csv
│   ├── exp3_periphery_timeseries.csv
│   ├── exp4_comp_r*.csv
│   ├── exp4_unst_r*.csv
│   └── summary_all_experiments.csv
└── figures/
    ├── exp1_compilation_comparison.png
    ├── exp3_targeting_robustness.png
    ├── exp4_resistance_sweep.png
    └── agent_analysis.png
```

---

## Requirements

- Python 3.10+
- `networkx`, `numpy`, `pandas`, `matplotlib`, `tqdm`
- Nebius AI Studio API key (for live LLM calls; cached results included for reproducibility)

All LLM calls use **Llama-3.3-70B-Instruct** via the Nebius AI Studio API with SHA1-based caching. Cached responses are included so all figures can be reproduced without API access.

