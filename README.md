# Benchmarking Single-Cell Trajectory Inference Algorithms

This project benchmarks popular trajectory inference (TI) algorithms used in single-cell RNA sequencing (scRNA-seq) data analysis. It evaluates the strengths and weaknesses of each method using multiple real-world datasets and complementary metrics.

> **Author**: Satwik Nimmagadda  
> **Supervisor**: Dr. Hamim Zafar  
> **Institution**: IIT Kanpur

---

## 🔬 Overview

Trajectory inference aims to model dynamic biological processes such as cell differentiation by ordering cells along developmental trajectories using their gene expression profiles. Given the growing number of TI algorithms with varying assumptions and capabilities, a systematic evaluation is essential.

This project compares **seven trajectory inference methods** across **four biological datasets** using **four complementary evaluation metrics**.

---

## 📂 Datasets

We used four publicly available single-cell datasets, covering different organisms and topological structures:

| Dataset                             | Organism | Topology        | Description                                      |
|-------------------------------------|----------|------------------|--------------------------------------------------|
| Placenta Trophoblast Differentiation | Mouse    | Disconnected     | Two roots branching into three lineages         |
| Mouse Cell Atlas (MCA)              | Mouse    | Disconnected     | Linear + multifurcating components              |
| Oligodendrocyte Differentiation     | Mouse    | Multifurcating   | One root with six terminal states               |
| Planaria Parenchyme Differentiation | Planaria | Multifurcating   | Four direct branches                             |

---

## ⚙️ Methods Evaluated

| Method     | Approach                                   | Topology Supported   | Platform |
|------------|--------------------------------------------|-----------------------|----------|
| **VIA**     | Lazy teleporting random walks              | Complex, disconnected | Python   |
| **MARGARET**| Deep metric learning                       | Disconnected          | Python   |
| **Palantir**| Markov chain + diffusion maps              | Tree-like             | Python   |
| **PAGA**    | Graph abstraction over kNN graph           | Disconnected          | Python   |
| **Slingshot**| MST + principal curves                    | Tree                  | R        |
| **DPT**     | Diffusion pseudotime                       | Bifurcating           | R        |
| **SCORPIUS**| Correlation distances + MDS                | Linear                | R        |

---

## 📏 Evaluation Metrics

Each method was assessed using four metrics:

| Metric             | What It Evaluates                        |
|--------------------|-------------------------------------------|
| **HIM Distance**   | Topological similarity to ground truth    |
| **F1 Branches**    | Accuracy of cell-to-branch assignments    |
| **Correlation**    | Preservation of cell orderings            |
| **FeatureImp_wcor**| Recovery of biologically important genes |

All metrics are normalized between 0 and 1. Higher is better.

---

## 📊 Key Findings

- **No single method consistently outperforms others across all metrics and datasets.**
- Metric-wise top performers:
  - **Topology (HIM)**: MARGARET
  - **Branch Assignment (F1)**: Slingshot
  - **Cell Ordering (Correlation)**: VIA
  - **Gene Relevance (FeatureImp_wcor)**: MARGARET
- **Slingshot**, **MARGARET**, and **Palantir** performed best overall.

---

## 🔮 Future Work

We aim to develop a graph ensemble based **consensus framework** that integrates the strengths of multiple TI methods to produce more robust and consistent trajectory reconstructions.

---

## 📎 Resources

- 📄 [Full Report (PDF)](./Project Report.pdf)  
- 🎞️ [Presentation Slides (PDF)](./Presentation.pdf)

