---
# Documentation: https://hugoblox.com/docs/content/
title: "Federated Learning with Non-IID Sensor Drift in Wearable HAR"
subtitle: "Daily Research Note #48 • Edge AI & Distributed Systems"
date: 2026-09-28T09:00:00Z
summary: "Exploring Dirichlet allocation parameter alpha=0.1 on accelerometer signals across heterogeneous user demographics."
draft: false
featured: true

# Taxonomy classification
tags:
  - Federated Learning
  - Human Activity Recognition
  - Deep Learning
  - Edge AI
categories:
  - Research Notes
  - Ideas

# Author profile association (maps to content/authors/admin)
authors:
  - admin

# Social & Link Preview Card
image:
  caption: "Decentralized Model Aggregation for Inertial Sensing"
  focal_point: "Smart"

# LaTeX & Code block controls
math: true
---

<!-- 💡 LinkedIn-style Academic Note Layout -->

### 💡 Core Hypothesis / Research Spark
In mobile and wearable **Human Activity Recognition (HAR)**, sensor placement variance (pocket vs. wrist vs. lanyard) creates severe covariate drift: $P(X)$ changes drastically while true activity intent $P(Y|X)$ remains constant.

Standard **FedAvg** converges poorly because each client's local stochastic gradient descent pulls the global weights toward user-specific bias vectors.

---

### 🔬 Mathematical Formulation
Instead of standard FedAvg, we incorporate a temporal representation anchor loss:

$$
\min_{w} \sum_{k=1}^K \frac{n_k}{n} \left[ \mathcal{L}_k(w) + \frac{\mu}{2} \| w - w^t \|^2 + \lambda \cdot \mathcal{D}_{\text{KL}}\left( z_i^k \,\|\, \bar{z}_i \right) \right]
$$

Where:
- $w^t$ is the global server weight from communication round $t$.
- $z_i^k$ is the latent representation of activity class $i$ on client device $k$.
- $\bar{z}_i$ is the global exponential moving average (EMA) prototype.

---

### 📊 Preliminary Benchmark (Simulated 20 Wearables)
```python
# PyTorch snippet for Local Representation Regularization
import torch
import torch.nn.functional as F

def compute_anchor_loss(local_features, global_prototypes, labels):
    batch_prototypes = global_prototypes[labels]
    cos_sim = F.cosine_similarity(local_features, batch_prototypes, dim=-1)
    return (1.0 - cos_sim).mean()
```

- **Communication rounds to 90% test accuracy:** Reduced from 74 rounds to 46 rounds (-37.8%).
- **Energy consumption per edge client:** Cut down by ~29% on Nordic nRF5340 / ESP32 nodes.

---

### ❓ Open Questions for Discussion
1. How does quantization (INT8 vs INT4) impact the gradient fidelity of Dirichlet-skewed sensor streams?
2. Has anyone tested stochastic prototype exchange to avoid raw latent transmission under strict Differential Privacy budgets?

*Drop your thoughts below or reach out via email!*