# NovoMol: RNN for Orally Bioavailable Drug Design and Validation on PDGFRα Receptor

**Author:** Ishir Rao  
**Full Paper:** [Read on arXiv](https://arxiv.org/abs/2312.01527)

---

## 📄 Abstract
Traditional drug discovery is hindered by long timelines and high failure rates. **NovoMol** addresses this by utilizing a **Recurrent Neural Network (RNN)** with **Long Short-Term Memory (LSTM)** units to generate novel molecules optimized for oral bioavailability. 

By employing the **Quantitative Estimate of Drug-likeness (QED)** as a fitness function, the model was iteratively refined through transfer learning. NovoMol provides a time/cost-efficient AI-based *de novo* method offering promising drug candidates for clinical trials.

## 🚀 Key Results
* **Oral Bioavailability:** 76% of generated molecules passed strict QED oral thresholds after 5 training cycles.
* **Drug-Likeness:** 96% passed the traditionally used Lipinski’s Rule of Five.
* **Target Specificity:** 44% of generated candidates showed superior binding affinity to **Imatinib** (-9.4 kcal/mol) against the PDGFRα receptor.
* **Peak Performance:** The best-generated candidate achieved a binding affinity of **-12.9 kcal/mol**.

---

## 🔬 Methodology

### 1. Generative Modeling
The model is trained on SMILES strings, treating chemical design as a sequence-generation task. The LSTM layers allow the model to learn complex structural rules, such as ring closures and branching, ensuring high chemical validity in generated outputs.

### 2. Reinforcement via Transfer Learning
To bias the model toward "drug-like" space, an evolutionary strategy was employed:
1. **Generation:** Produce a population of novel molecules.
2. **Scoring:** Evaluate candidates using **QED** and **Lipinski’s Rule of Five**.
3. **Refinement:** Retrain the model on the highest-scoring subset to "shift" the chemical distribution toward bioavailable space.

### 3. Target Validation
Candidates were docked against the **PDGFRα** (Platelet-Derived Growth Factor Receptor Alpha) protein. This receptor is a key target in various cancers; docking scores were benchmarked against the FDA-approved drug **Imatinib** to verify therapeutic potential.

---

## 🛠️ Repository Structure
This repository contains the full pipeline from model training to molecular docking validation.

* `LSTM_Training.ipynb`: Notebook for training the base RNN model on the ChEMBL database.
* `Transfer_Learning.ipynb`: The optimization loop used to refine the model for oral bioavailability.
* `Molecule_Generation.ipynb`: Logic for generating novel SMILES strings and performing QED filtering.
* `AutoDock_Vina_Binding.ipynb`: Computational docking simulations to calculate binding affinities.
* `Statistical_Analysis.ipynb`: Data processing and success rate calculations.
* `Draw_Molecules.ipynb`: Visualization scripts using RDKit to render 2D molecular structures.
* `valid_smiles_data`: Processed chemical data used during the training phases.

---

## 💻 Getting Started

### Prerequisites
You will need Python 3.8+ and the following core dependencies:
* **RDKit**: Cheminformatics and molecule visualization.
* **TensorFlow/PyTorch**: Deep learning framework for the LSTM.
* **AutoDock Vina**: Molecular docking engine.
* **Pandas/NumPy**: Data manipulation.

### Installation
```bash
pip install rdkit tensorflow pandas numpy matplotlib
