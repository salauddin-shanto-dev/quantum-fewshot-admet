# Quantum-Enhanced Few-Shot ADMET Prediction

This repository presents **Quantum Kernel + GNN approaches** for **few-shot ADMET prediction**, focusing on the `half_life_obach` endpoint. The work compares **GNN-only** and **Quantum Kernel Support (QKS-only)** baselines with **episodic few-shot training**, suitable for **conference-paper style presentation**.

---

## 1. Overview

**Problem:** Predict ADMET properties of molecules in **few-shot scenarios** using limited labeled data.  
**Endpoint:** `half_life_obach` (667 molecules after preprocessing).

**Approaches Compared:**

1. **GNN-only**: Graph Neural Network encoding molecular graphs, trained episodically.  
2. **QKS-only**: Quantum Kernel-based features generated from molecular ECFP fingerprints, classified with Logistic Regression.

**Evaluation Metrics:**

- **AUC (ROC)**  
- **Average Precision (AP)**  
- **Accuracy (Acc)**

---

## 2. Dataset

- **Source:** TDC ADME benchmark (`half_life_obach`)  
- **Valid Molecules after preprocessing:** 667  
- **Molecular representation:**  
  - Graphs for GNN (atoms as nodes, bonds as edges)  
  - ECFP fingerprints for QKS

---

## 3. Methodology

### 3.1 GNN-only

- **Architecture:** 2-layer GCN with mean-pooling and a linear projection to embedding space.  
- **Training:** Episodic few-shot paradigm (N-way K-shot, Q-query).  
- **Hyperparameters:**  
  - N-way: 2  
  - K-shot: 5  
  - Learning Rate: 1e-3  
  - Hidden dimension: 128  
  - Embedding dimension: 64  
  - Epochs: up to 100 with early stopping

### 3.2 QKS-only

- **Input:** 1024-bit ECFP fingerprints  
- **Quantum Feature Map:** Parameter-free quantum circuit with 16 qubits  
- **Classifier:** Multinomial Logistic Regression  
- **Evaluation:** Episodic few-shot testing

---

## 4. Results

| Endpoint         | Model     | AUC    | AP     | Acc    |
|-----------------|-----------|--------|--------|--------|
| half_life_obach | gnn_only  | 0.7688 | 0.7582 | 0.7488 |
| half_life_obach | qks_only  | 0.9365 | 0.9350 | 0.8618 |

> **Observation:** QKS-only outperforms GNN-only significantly on this endpoint, demonstrating the power of quantum-enhanced features in few-shot molecular property prediction.

---

## 5. Learning Curves & Plots

### 5.1 GNN-only Training Loss
<img width="1200" alt="half_life_obach_gnn_train_loss" src="https://github.com/user-attachments/assets/2f76c9e7-9c3c-4ac4-8d66-1d348e917b87" />


### 5.2 GNN-only Validation Metrics (AUC & AP)
<img width="1200" alt="half_life_obach_gnn_val_metrics" src="https://github.com/user-attachments/assets/85b5cb4d-2361-44f8-8349-9ee4d4851ad3" />


### 5.3 t-SNE Visualization of GNN Embeddings
<img width="1200" alt="half_life_obach_tsne_gnn" src="https://github.com/user-attachments/assets/53896ab4-d2ea-4436-b5ae-653ab536c850" />



---

## 6. Usage

1. **Clone the repository**:
```bash
git clone https://github.com/salauddin-shanto-dev/quantum-fewshot-admet
```
