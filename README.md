# Benchmarking Single-Cell Trajectory Inference Algorithms

This project benchmarks popular trajectory inference (TI) algorithms used in single-cell RNA sequencing (scRNA-seq) data analysis. It evaluates the strengths and weaknesses of each method using multiple real-world datasets and complementary metrics.

> 📍 **Author**: Satwik Nimmagadda  
> 🧑‍🏫 **Supervisor**: Dr. Hamim Zafar  
> 🏫 **Institution**: IIT Kanpur

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
- **Top 3 Overall (geometric mean across metrics)**:
  - 🥇 Slingshot — 0.58
  - 🥈 MARGARET — 0.55
  - 🥉 Palantir — 0.52

---

## 🔮 Future Work

We aim to develop a **consensus framework** that integrates the strengths of multiple TI methods to produce more robust and generalizable trajectory reconstructions.

---

## 📁 Repository Structure

├── data/ # Preprocessed datasets
├── methods/ # Wrapper scripts for each TI method
├── metrics/ # Code for computing evaluation metrics
├── results/ # Plots and tables summarizing results
├── utils/ # Helper functions for preprocessing and visualization
└── README.md # You're here!


---

## 📚 References

See the [report](./Report-2-1.pdf) for a full list of citations, including:

- Saelens et al., *Nat. Biotechnol.*, 2019
- Stassen et al., *Nat. Commun.*, 2021 (VIA)
- Pandey & Zafar, *Nucleic Acids Res.*, 2022 (MARGARET)
- Setty et al., *Nat. Biotechnol.*, 2019 (Palantir)
- Wolf et al., *Genome Biol.*, 2019 (PAGA)
- Street et al., *BMC Genomics*, 2018 (Slingshot)
- Cannoodt et al., *bioRxiv*, 2016 (SCORPIUS)

---

## 📎 Resources

- 📄 [Full Report (PDF)](./Report-2-1.pdf)  
- 🎞️ [Presentation Slides (PDF)](./Presentation-2-1.pdf)

---

Feel free to open an issue if you'd like to reproduce or extend this benchmarking study.
