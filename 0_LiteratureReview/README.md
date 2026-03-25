# Literature Review

Approaches or solutions that have been tried before on similar projects.
# Literature Review: Physics-Informed Model Order Reduction via Neural Networks

## Overview
This repository serves as a living literature review and documentation hub for research at the intersection of Model Order Reduction (MOR) and Physics-Informed Neural Networks (PINNs). 

The primary focus is tracking methodologies that accelerate complex multiphysics simulations—such as those traditionally handled by FEM software like Abaqus or COMSOL—by leveraging deep learning and reduced-basis techniques to achieve real-time predictive capabilities.

## Core References

### Foundational Methods & Mathematics
* **Data-driven science and engineering: Machine learning, dynamical systems, and control**
    * *Authors:* Steven L. Brunton and J. Nathan Kutz
    * *Publication:* Cambridge University Press, 2019.
    * *Relevance:* An essential foundation covering the mathematics of extracting dynamics from data, including Singular Value Decomposition (SVD) and the machine learning architectures necessary for robust reduced-order modeling.

* **A short review on model order reduction based on proper generalized decomposition**
    * *Authors:* Francisco Chinesta, Pierre Ladeveze, and Elias Cueto
    * *Publication:* Archives of Computational Methods in Engineering, 18(4):395, 2011.
    * *Relevance:* A comprehensive review of Proper Generalized Decomposition (PGD). This serves as a critical baseline for classical, projection-based MOR approaches before the integration of modern deep learning frameworks.

### Applied Physics-Informed Machine Learning
* **Real-time magnetic field and performance prediction of EV motors based on physics-informed machine learning**
    * *Authors:* Y. Wang, Y. Cheng, L. Ding, K. Yao, W. Li, and S. Cui
    * *Publication:* IEEE Transactions on Transportation Electrification, 11(6):14087–14099, Dec 2025.
    * *Relevance:* Demonstrates a highly relevant, practical application of PIML for real-time state prediction in complex engineering systems. It highlights the massive efficiency and speed gains achievable over traditional numerical solvers while maintaining physical accuracy.

## Research Objectives
The literature curated in this project specifically informs the development of:
1.  **Nonlinear Dimensionality Reduction:** Moving beyond linear methods by utilizing neural network autoencoders to map high-dimensional FEM data to compact latent spaces.
2.  **Physics-Informed Architecture:** Embedding governing physical equations directly into the training process (e.g., via custom PDE loss functions in PyTorch) to ensure predictions obey fundamental conservation laws.
3.  **Real-Time Surrogates:** Replacing computationally expensive full-order models with fast, data-driven surrogates for rapid engineering design and evaluation.

