# Benchmarking Single-Cell Trajectory Inference Algorithms

This project evaluates and compares seven trajectory inference (TI) algorithms on four single-cell RNA-seq datasets. The goal is to assess how well each method reconstructs developmental trajectories of cells using diverse topologies and metrics.

## 🧪 Methods Evaluated

- **VIA**
- **MARGARET**
- **Palantir**
- **Slingshot**
- **PAGA**
- **DPT**
- **SCORPIUS**

## 📊 Evaluation Metrics

- **HIM Distance** – Topological similarity  
- **F1 Branches** – Branch assignment accuracy  
- **Correlation** – Preservation of cell ordering  
- **FeatureImp_wcor** – Gene relevance recovery  

## 📁 Datasets

- Placenta trophoblast (mouse)  
- Mouse cell atlas  
- Oligodendrocyte differentiation  
- Planaria parenchyme differentiation  

## ✅ Key Results

- No single method dominates across all metrics.  
- **Slingshot**, **MARGARET**, and **Palantir** performed best overall.  
- Future goal: build a consensus framework leveraging the strengths of multiple methods.

## 📎 Resources

- 📄 [Full Report](./Report-2-1.pdf)  
- 🎞️ [Presentation Slides](./Presentation-2-1.pdf)
