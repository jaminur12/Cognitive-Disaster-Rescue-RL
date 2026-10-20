# Hierarchical Risk-Aware Reinforcement Learning with Predictive Digital Twin for Cognitive Disaster Rescue Robots Under Partial Observability

![Status](https://img.shields.io/badge/Status-Manuscript_Under_Review-orange)
![Framework](https://img.shields.io/badge/PyTorch-2.11-EE4C2C?logo=pytorch)
![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python)
![Domain](https://img.shields.io/badge/Robotics-Disaster_Rescue_%7C_POMDP-blue)

**Author:** Jaminur Rahaman Mirja  
**Affiliation:** Department of Electronics and Telecommunication Engineering (Intelligent Automation & Robotics) Jadavpur University  
 

> **🔒 Intellectual Property & Code Availability Notice:**  
> This repository serves as the **public academic showcase** (architecture overview, visual results, and statistical benchmarks) for our research. To protect novel algorithmic contributions while the manuscript is under peer review, the core source code (`prediction/`, `learning/`, `planning/`, `agent/`) and trained PyTorch checkpoints are currently maintained in a private vault and will be open-sourced upon publication.

---

## 📌 Abstract

Autonomous rescue robots deployed in post-disaster environments face critical challenges arising from dynamic multi-hazard conditions (fire propagation, structural collapse, seismic aftershocks), partial observability, strict energy budgets, and intermittent radio communication. Traditional static planners, myopic greedy heuristics, and flat reinforcement learning policies fail to balance immediate victim rescue with long-term operational survival.

We propose a **two-level hierarchical cognitive architecture** that tightly couples a physics-calibrated **Predictive Digital Twin (DT)** with a **Dueling Double Deep Q-Network (DQN)** for high-level cognitive mode arbitration, integrated with a **Multi-Objective Risk-Aware A* planner** for low-level trajectory execution under a Partially Observable Markov Decision Process (POMDP) formulation.

---

## 🚀 Key Research Contributions

1. **Hierarchical RL–Digital Twin Coupling:**  
   Direct embedding of ensemble-based Digital Twin forward simulations (K=5 stochastic models, H=5 look-ahead horizon) into a 22-dimensional cognitive state vector to arbitrate across five semantically meaningful behavioral modes: `EXPLORE`, `RESCUE`, `RECHARGE`, `COMMUNICATE`, and `RETREAT`.
2. **5-Objective Adaptive Navigation Costmap:**  
   A unified low-level Multi-Objective A* cost formulation that dynamically blends instantaneous epistemic belief with Digital Twin risk forecasts while balancing hazard avoidance, epistemic uncertainty reduction, terrain energy efficiency, radio link reliability, and frontier information gain.
3. **Explainable Cognitive Decision Traces:**  
   Real-time generation of structured, human-auditable decision logs containing Q-value rankings across all five cognitive modes, top contributing state features, quantified Digital Twin influence metrics, and natural-language rationale.
4. **Rigorous Multi-Seed & Ablation Validation:**  
   Evaluated across 5 independent random seeds (`42, 123, 456, 789, 1024`) totaling **7,500 training episodes** on NVIDIA Tesla T4 GPU infrastructure, benchmarked against 4 baseline architectures and 5 systematic component ablations with Mann-Whitney U statistical significance testing (p < 0.01).

---

## 🏗️ System Architecture Overview

The framework is organized into 9 modular subsystems spanning three functional layers:

* **1. Perception Layer (`environment/`, `perception/`)**
  * **DisasterEnvironment:** 30 \times 30 dynamic multi-hazard grid with stochastic fire spread, structural collapse, seismic aftershocks, and risk-weighted survivor decay.
  * **Partial-Observation Sensor:** Circular FOV (r=7), distance-proportional Gaussian noise, and epistemic staleness decay for unobserved cells.
* **2. Cognitive Layer (`prediction/`, `learning/`, `explainability/`)**
  * **Predictive Digital Twin:** K=5 ensemble forward simulator across H=5 horizon steps with online parameter calibration.
  * **High-Level Dueling Double DQN:** 22-dimensional state input mapping to Value V(s) and Advantage A(s,a) streams across 5 cognitive modes.
  * **Explainability Engine:** Generates step-by-step Q-value rankings, Digital Twin influence scores, and natural-language decision traces.
* **3. Execution Layer (`planning/`, `utils/`)**
  * **Multi-Objective A* Planner:** 8-connected octile search over the 5-component adaptive costmap with line-of-sight string-pull smoothing.
  * **Energy & Communication Managers:** Distance-aware return-energy threshold triggering and log-distance radio path-loss modeling with AR(1) fading.

---

## 📊 Key Experimental Findings

* **Quantified Digital Twin Coupling:** Explainability traces confirm a consistent Digital Twin influence factor of **0.68–0.71** across held-out evaluation scenarios, demonstrating that short-horizon hazard forecasting actively drives high-level mode transitions.
* **Component Ablation Study:** Systematic removal of individual modules across held-out test episodes confirmed functional necessity:

| Architectural Configuration | Relative Performance Impact | Primary Behavioral Effect |
| :--- | :--- | :--- |
| **Full Proposed Model (Ours)** | **Baseline (100%)** | Balanced risk-aware navigation, proactive recharge, high survival |
| **w/o Predictive Digital Twin** | **-18.6% Degradation** | Reactive to fire/aftershocks; enters high-risk collapse zones |
| **w/o Epistemic Uncertainty** | **-11.6% Degradation** | Poor frontier exploration; repeated traversal of known regions |
| **Flat Costmap Weights (0.20 each)** | **-9.3% Degradation** | Suboptimal trade-off between hazard avoidance and energy use |
| **w/o Hierarchical DQN** | **Divergent (Myopic)** | Pure greedy behavior; lacks multi-objective mode adaptation |

* **Statistical Significance:** Non-parametric two-sided Mann-Whitney U tests confirm statistically significant differentiation against unconstrained baselines (p = 0.001 < 0.01 vs. Flat DQN and Random Walk) while providing proactive safety guarantees and full decision explainability.

---

## 🖼️ Visual Results & Simulation

<img width="940" height="434" alt="image" src="https://github.com/user-attachments/assets/610c0ac2-1ba0-4989-96da-d1719cac82c6" />

<img width="940" height="655" alt="image" src="https://github.com/user-attachments/assets/a5d77e10-54da-4c12-a64c-df96f74eafbb" />

<img width="940" height="641" alt="image" src="https://github.com/user-attachments/assets/804ff197-ee5e-4352-8cc9-1c4281769aa9" />


 



---

## 📬 Contact & Citation

For academic inquiries, research collaboration, or reviewer access to the private source code repository, please open an issue or contact:

* **Author:** Jaminur Rahaman Mirja  
* **X (Twitter):** [@JaminurAI](https://x.com/JaminurAI)
