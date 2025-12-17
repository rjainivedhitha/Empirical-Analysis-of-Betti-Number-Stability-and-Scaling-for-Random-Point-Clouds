# Empirical Analysis of Betti Number Stability and Scaling for Random Point Clouds

## Overview
This project presents an empirical study of the stability and scaling behavior of Betti numbers using tools from Topological Data Analysis (TDA). By applying persistent homology to random point clouds, we analyze how topological features such as connected components and loops evolve with increasing sample size and noise.

The project serves as a **bridging study** connecting concepts from mathematics, data science, and computational topology.

---

## Objectives 
- To empirically analyze how persistent Betti numbers scale with sample size.
- To study the stability of persistence diagrams under noise perturbations.
- To compare topological behavior across different random point cloud models.
- To validate robustness with respect to persistence thresholds and modeling choices.
- To explore finite-size scaling as a unifying framework for sample-size and noise dependence.

---

## Models Studied
We consider three classes of 2D point clouds:

### 1. Uniform Disk
Points sampled uniformly inside a unit disk.  
This model represents a random geometric structure without intrinsic 1D topology.

### 2. Gaussian Cloud
Points sampled from an isotropic 2D Gaussian distribution.  
This serves as a null model with no underlying topological features.

### 3. Noisy Circle
Points sampled on a unit circle with additive Gaussian noise.  
This model contains a known topological feature: a single persistent 1-dimensional hole.

---

## Key Concepts and Methods

### Persistent Homology
Persistent homology is used to track the birth and death of topological features across a filtration.  
In this project:
- Vietoris–Rips filtrations are constructed from point clouds.
- Homology is computed up to dimension 1 (H₀ and H₁).
- Computations are performed using the `ripser` library.

### Betti Numbers
- **Betti-0 (H₀)**: counts connected components.
- **Betti-1 (H₁)**: counts loops or cycles.

We focus primarily on H₁ features and analyze their persistence across scales.

---

### Stability Analysis
To assess robustness, we measure the **bottleneck distance** between persistence diagrams obtained from:
- an original point cloud, and
- a slightly perturbed (jittered) version of the same cloud.

This experiment is motivated by the **stability theorem for persistent homology**, which guarantees that small perturbations in data lead to bounded changes in persistence diagrams.

---

### Scaling Analysis
We study how the mean number of persistent H₁ features scales with the number of points \(N\):
- Log–log regression is used to estimate scaling exponents.
- Bootstrap resampling provides confidence intervals.

Disk and Gaussian models show approximately linear scaling, while the circle model behaves differently due to its intrinsic topology.

---

### Finite-Size Scaling
Motivated by statistical physics, we test a finite-size scaling ansatz:

\[
M(N,\sigma) \approx N^{\alpha} \mathcal{F}(\sigma N^{\phi})
\]

where:
- \(M\) is the number of persistent H₁ features,
- \(N\) is the sample size,
- \(\sigma\) is the noise level,
- \(\alpha\) and \(\phi\) are scaling exponents.

Successful collapse of rescaled curves suggests that the combined dependence on noise and sample size can be captured by a universal scaling function.

---

## Robustness Checks
To ensure conclusions are not artifacts of parameter choices, several robustness analyses are performed:

- **Persistence threshold sweep**: studying how results change with varying thresholds.
- **Adaptive thresholding**: defining thresholds based on null-model lifetimes.
- **Top-k method**: counting only the longest H₁ features (useful for isolating true topology in the circle model).
- **maxdim sensitivity**: verifying that results are consistent across different homology truncations.

---

## Results Summary
- Disk and Gaussian point clouds exhibit approximately linear growth in the number of persistent H₁ features with sample size.
- The circle model contains a single robust topological loop, which is recovered using adaptive or top-k persistence criteria.
- Bottleneck distances increase with noise, consistent with stability theory.
- Finite-size scaling provides an effective framework for understanding combined noise and size effects.

---

## Tools and Libraries
- **Python**
- **NumPy / Pandas**
- **Matplotlib**
- **ripser**
- **persim**
- **Google Colab**

---

## How to Run
1. Open the provided Jupyter notebook (`.ipynb`) in Google Colab.
2. Install required dependencies.
3. Run cells sequentially to generate results and plots.
4. Outputs (CSV files and figures) are automatically saved to Google Drive.

---

## Limitations
- Results are empirical and based on finite sample sizes.
- Analysis is restricted to low-dimensional homology (H₀ and H₁).
- Finite-size scaling results are exploratory rather than asymptotic guarantees.

---

## Conclusion
This project demonstrates how topological data analysis can be used to study structure, noise, and scaling in finite data. By combining theory, computation, and robustness analysis, it provides a clear illustration of how topology, probability, and data science intersect in modern data analysis.

---

## References
- Cohen-Steiner, D., Edelsbrunner, H., & Harer, J. (2007). Stability of persistence diagrams.
- Penrose, M. (2003). *Random Geometric Graphs*.
- Kahle, M. (2011). Random geometric complexes.
