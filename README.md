# Dependency-Aware Synthetic Tabular Data Generation

This repository accompanies our paper on **Dependency-Aware Synthetic Tabular Data Generation**, where we propose the **Hierarchical Feature Generation Framework (HFGF)**. HFGF is designed to preserve both **functional** and **logical dependencies** between features in synthetic tabular data.

---

## 🚀 Overview of HFGF

The **Hierarchical Feature Generation Framework (HFGF)** generates synthetic tabular data by separating the process into two stages:

1. **Identify independent and dependent features**
2. **Generate independent features** using standard generative models
3. **Map dependent features** using known or extracted dependencies
4. **Concatenate** independent and dependent features to form the final synthetic dataset

---

## 🔍 Identifying Independent and Dependent Features

- **Simulated Data**:  
  Dependencies are predefined when generating the data. Independent and dependent features are explicitly known.

- **Real Data**:  
  Dependencies are **extracted** using:
  - **FDTool** for functional dependencies:
    - Features not present in the RHS of any rule (or not extracted at all) are considered independent.
  - **Q-function** for logical dependencies:
    - If the Q-score between any two features is **1**, it implies **no dependency** between them.

---

## 🧪 Simulated Data

We created **four synthetic datasets** with varying:
- Number of features
- Number of rows
- Types and numbers of dependencies

**Files:**
- Data generation code: [`Simulated_data_generator.py`](./Simulated_data_generator.py)
- Generated datasets: [`Real_simulated_data/`](./Real_simulated_data/)

See the paper for detailed descriptions of each simulated dataset.

---

## 🛠️ How to Apply HFGF to Your Own Data

1. **Extract dependencies**:
   - Functional dependencies: Use **FDTool**  
     ➤ *[Add FDTool link here]*
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
➤ *[Add links to each generative model's repository here]*

---

## 📁 Project Structure

