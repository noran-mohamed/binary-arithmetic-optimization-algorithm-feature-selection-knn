# BAOA-Inspired Feature Selection Experiments
This repository contains a complete implementation of a feature selection framework inspired by the BAOA (Binary AOA) algorithm proposed in the original research paper.  
"BAOA: Binary Arithmetic Optimization Algorithm With K-Nearest Neighbor Classifier for Feature Selection", DOI: 10.1109/ACCESS.2023.3310429
The notebook applies BAOA to real datasets and compares its performance against four other binary optimization algorithms commonly used in feature selection.

## Project Overview

This project implements a binary feature selection meta-heuristic based on the principles of **BAOA**, integrating both exploration and exploitation through adaptive operators.  
The objective function aims to balance two goals:

- **Maximize classification accuracy**
- **Minimize the number of selected features**

The trained classifier used for evaluation is a **K-Nearest Neighbors (KNN)** model.

## Implementation Highlights

### Feature Binarization  
Real-valued solution vectors generated during optimization are converted to binary using a **sigmoid-based probabilistic thresholding**:

- Sigmoid activation
- Randomized thresholding to generate 0/1 feature selections

### Fitness Function (Eq. 8)

The fitness score is defined as a weighted combination of:

- Classification error using KNN
- Ratio of selected features to total features

If no feature is selected, the worst possible fitness value is automatically assigned.

### BAOA Optimization Logic

The main BAOA loop includes:

- Initialization of random candidate solutions  
- Iterative update of positions based on:
  - Memory-driven operators
  - Scaling factors MOA and MOP
- Randomized operator selection for both exploration and exploitation
- Solution binarization after updates

The algorithm returns:

- The best binary feature mask  
- Best achieved fitness  
- A convergence curve over iterations

---

## Datasets Used

Two benchmark datasets were tested:

- **SonarEW**
- **BreastEW**

Both were split into train and test sets and evaluated independently.

---

## Baselines & Comparative Optimizers

In addition to BAOA, four well-known binary optimization algorithms were also implemented in comparable form:

- **BPSO** — Binary Particle Swarm Optimization  
- **BDF** — Binary Differential Evolution  
- **BGA** — Binary Genetic Algorithm  
- **BCAT** — Binary Cat Swarm Optimization  

All optimizers were:

- Implemented with convergence tracking  
- Evaluated under the same experimental conditions  
- Tested on the same datasets

---

## Experimental Evaluation

### Metrics Reported

For each optimizer, the following were computed:

| Metric | Description |
|---|---|
| **Fitness Score** | Weighted combination of error + feature count |
| **Number of Selected Features** | Dimensionality after selection |
| **Classification Accuracy** | KNN accuracy on test data |

The results for each dataset were consolidated into comparison tables.

### Convergence Analysis

Each optimizer stored its fitness value over iterations, allowing:

- Convergence visualization  
- Stability comparisons across algorithms  
- Performance trajectory interpretation

---

## Statistical Analysis

Additional statistical evaluations were performed to:

- Quantify whether improvements were significant  
- Compare stability across multiple runs  
- Strengthen conclusions beyond raw metrics

---

## Running the Experiments

The main comparison function:

```
df_results, convergence_curves = run_comparison(X_train, X_test, y_train, y_test)
```

Produces:

- A results table summarizing final performance
- A dictionary of convergence curves

---

## Code Structure

```
main_notebook.ipynb     # All implementation and experiments
```

Core components include:

- Sigmoid-based binarization  
- Fitness computation  
- BAOA loop logic  
- Baseline optimizers  
- Comparison and evaluation utilities

---

## Inspiration

This project is **inspired by the BAOA paper**, adapting the optimization strategy for practical binary feature selection with real datasets and benchmark comparisons.  
The implementation is educational and research-oriented, enabling reproducible experiments and deeper understanding of meta-heuristic optimization.

---

## Contributions

Suggestions and improvements are welcome!  
If you want to extend the study with:

- New datasets  
- Additional meta-heuristics  
- Deep models embedded in feature extraction

Feel free to open a pull request.

---

## ⚖️ License

This project is for research and educational purposes.
