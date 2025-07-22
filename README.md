# Dependency-Aware Synthetic Tabular Data Generation

This repository presents the **Hierarchical Feature Generation Framework (HFGF)**, a framework for generating synthetic tabular data while preserving both functional and logical dependencies between features. The framework is proposed as part of our research on **Dependency-aware synthetic data generation.**

---

##  Overview of HFGF

The **Hierarchical Feature Generation Framework (HFGF)** generates synthetic tabular data by separating the process into two steps:

1. **Identify independent and dependent features**
2. **Generate independent features** using standard generative models
3. **Map dependent features** using known or extracted dependencies
4. **Concatenate** independent and dependent features to form the final synthetic dataset

---

##  Identifying Independent and Dependent Features

- **Benchmark Data**:  
  Dependencies are predefined when generating the data. Independent and dependent features are explicitly known.

- **Real Data**:  
  Dependencies are **extracted** using:
  - **FDTool** for functional dependencies:
    - Features not present in the RHS of any rule (or not extracted at all) are considered independent.
  - **Q-function** for logical dependencies:
    - If the Q-score between any two features is **1**, it implies **no dependency** between them.

---

##  Benchmark Data

We created **four benchmark datasets** with varying:
- Number of features
- Number of rows
- Types and numbers of dependencies

**Files:**
- Data generation code: [`Benchmark_data_generator.py`](./Benchmark_data_generator.py)
- Generated datasets: [`Benchmark_data/`](./Benchmark_data/)

See the paper for detailed descriptions of each benchmark dataset.

---

## 🛠️ How to Apply HFGF to Your Own Data

1. **Extract dependencies**:
   - Functional dependencies: Use **FDTool**  
     ➤ https://github.com/USEPA/FDTool
   - Logical dependencies: Use the **Q-function**  
     - Code: [`Functions.py`](./Functions.py)  
     - Example usage: [`LD_comparison.py`](./LD_comparison.py)

2. **Identify independent features**:
   - Based on extracted dependency information.

3. **Generate synthetic data** for independent features using a generative model.

4. **Map dependent features** using the known/extracted dependency rules.

5. **Concatenate** independent and dependent features.

6. **Evaluate dependency preservation**:
   - Re-extract dependencies from the synthetic data.
   - Compare them with those from the original data.

---

## 📊 Baseline Generative Models

We compared HFGF with six state-of-the-art generative models using their official implementations.

➤ CTGAN: https://github.com/sdv-dev/CTGAN

➤ CTABGAN+: https://github.com/Team-TUD/CTAB-GAN-Plus-DP

➤ TVAE:  https://github.com/sdv-dev/TVAE

➤ NextConvGeN: https://github.com/manjunath-mahendra/NextConvGeN

➤ TabuLa: https://github.com/zhao-zilong/Tabula

➤ GReaT: https://github.com/tabularis-ai/be_great




