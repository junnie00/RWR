<div align="center">

# Reasoning Warm-up
### Scaling Label-free RL via Verifiable Surrogate Rewards

**NeurIPS 2026 Manuscript**

[![Code Release](https://img.shields.io/badge/Code-Coming%20Soon-lightgrey)](#code-release)
[![Research](https://img.shields.io/badge/Research-Label--free%20RL-blue)](#overview)

</div>

## Overview

**Reasoning Warm-up Reinforcement Learning (RWR)** investigates how to improve large language model reasoning through reinforcement learning *without using ground-truth answers to the main tasks as training rewards*.

Many label-free RL approaches construct pseudo-rewards from a model's own generations, such as self-consistency or majority voting. These signals may be misleading on complex, multi-step problems: a model can repeatedly produce mutually consistent but incorrect reasoning trajectories.

RWR explores an alternative: **verifiable surrogate rewards derived from deterministic auxiliary tasks**. The main-task answer need not be verified during optimization.

## Motivation: The Reasoning Warm-up Phenomenon

Our research is motivated by an empirical phenomenon termed **Reasoning Warm-up**: when a model successfully completes an exactly verifiable auxiliary task before tackling a difficult reasoning problem, its success probability on the subsequent main task increases.

This observation motivates using auxiliary-task verification as feedback for reasoning trajectories. Crucially, **correctness on the auxiliary task is a surrogate signal, not proof that the main-task answer is correct**.

## Method

RWR integrates deterministic auxiliary tasks into both generation and policy optimization:

1. **Auxiliary task construction.** Prepare a deterministic task whose answer can be verified exactly.
2. **Auxiliary-augmented rollout.** Generate a trajectory that first addresses the auxiliary task and then the target reasoning problem.
3. **Verifiable surrogate reward.** Check the auxiliary-task answer with its verifier to obtain trajectory-level feedback, without consulting the main-task ground-truth answer.
4. **Reinforcement learning.** Optimize the policy using the auxiliary-verification-based reward signal.

```text
  Main reasoning problem
    (no reward label)
           |
           v
  Deterministic auxiliary task
           |
           v
  Auxiliary-augmented rollout
     /                 \
    v                   v
 Auxiliary answer    Main-task answer
    |                   |
    v                   | (not checked for reward)
 Exact verifier         |
    |                   |
    v                   |
 Surrogate reward ------+
    |
    v
  Policy optimization
```

Unlike purely self-referential pseudo-rewards, the auxiliary feedback is grounded in an **external, exact verifier**.

## Research Scope

The manuscript investigates the Reasoning Warm-up phenomenon, proposes the RWR framework, develops theoretical analysis, and evaluates the approach on reasoning benchmarks. Please refer to the manuscript for detailed experimental settings, quantitative results, and limitations.

## Code Release

> **Coming soon.** This repository is currently a public project landing page. The training and evaluation implementation, configurations, and reproducibility instructions have not yet been released.

We will add installation and usage instructions alongside runnable code. No unverified command, checkpoint, or benchmark result is advertised here.

## Citation

**Reasoning Warm-up: Scaling Label-free RL via Verifiable Surrogate Rewards**

*NeurIPS 2026 manuscript.*

A public paper link and verified BibTeX entry will be added when available. This label does not by itself indicate an acceptance decision.

## Questions

Please use the [GitHub Issues](https://github.com/junnie00/RWR/issues) page for questions and project updates.

---

<div align="center"><sub>RWR · Reasoning Warm-up Reinforcement Learning</sub></div>
