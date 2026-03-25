# Physics-Informed Model Order Reduction (MOR) via Neural Networks

## 📌 Overview
This repository contains the implementation of a deep learning-based surrogate model designed to accelerate complex Finite Element Method (FEM) simulations. Traditional high-fidelity simulations for transient material behavior (e.g., in Abaqus or COMSOL) are computationally expensive. This project tackles this bottleneck by coupling **Singular Value Decomposition (SVD)** with **Deep Neural Networks (built in PyTorch)** to map parametric and temporal inputs directly to the reduced physical state of the system, achieving near real-time inference without sacrificing physical accuracy.

## 🔬 Scientific Context & Materials Engineering Application
In computational materials science, evaluating the transient evolution of physical fields (such as thermal diffusion, stress-strain distribution, or wave propagation) requires solving coupled Partial Differential Equations (PDEs) over thousands of spatial nodes. 

This model employs **Proper Orthogonal Decomposition (POD)** to extract the dominant spatial modes (the core kinematic or thermal features) from heavy FEM output matrices. A neural network is then trained to predict the temporal evolution of these latent variables. This approach is highly applicable to:
* Real-time predictive maintenance and digital twins.
* Rapid prototyping of material microstructures.
* Multi-scale modeling where microscopic solver efficiency is critical.

## 🧠 Model Architecture
The primary implementation is located in: `Physics_Informed_Model_Order_Reduction_via_Neural_Networks (1).ipynb`

The pipeline is structured as follows:
1.  **Data Generation / Ingestion:** High-dimensional snapshot matrices ($N_{nodes} \times N_{steps}$) representing the ground-truth physical fields.
2.  **Dimensionality Reduction (SVD):** The full-order spatial domain ($N = 10,000$ degrees of freedom) is compressed down to a compact latent space ($r \ll N$, typically 2 to 6 dominant modes).
3.  **Neural Network Surrogate:** A PyTorch-based Multilayer Perceptron (MLP) replaces the linear baseline. It learns the highly non-linear mapping between the time vector $t$ (and potentially varying material parameters) and the latent mode coefficients.
4.  **Full-Field Reconstruction:** The predicted latent variables are projected back onto the orthogonal spatial basis to reconstruct the full 10,000-node physical state.

## 💻 Tech Stack
* **Deep Learning:** PyTorch
* **Mathematics & Data Manipulation:** NumPy, SciPy
* **Visualization:** Matplotlib
* **Target Simulation Environments:** FEM Solvers (Abaqus, COMSOL) via exported snapshot matrices.

## 🚀 How to Run
1.  Ensure you have Python 3.8+ installed along with `torch`, `numpy`, `scipy`, and `matplotlib`.
2.  Open the Jupyter Notebook:
    ```bash
    jupyter notebook "Physics_Informed_Model_Order_Reduction_via_Neural_Networks (1).ipynb"
    ```
3.  Run the cells sequentially. The notebook will:
    * Generate/Load the high-fidelity transient dataset.
    * Compute the SVD projection.
    * Initialize and train the PyTorch neural network.
    * Output the loss convergence curve.
    * Visualize the reconstructed physical field against the exact FEM solution.

## 📊 Evaluation & Performance
The deep learning surrogate is evaluated against a classical linear regression baseline (see `baseline_model.ipynb`). Performance is quantified using:
* **Mean Squared Error (MSE)** of the latent space predictions.
* **Relative $L_2$ Error** of the reconstructed global physical field.
* **Computational Speedup:** Time taken for an epoch of neural network inference versus a standard numerical step in a traditional solver.

## 🔭 Future Work & Advanced Topics
* **Physics-Informed Loss Functions (PINNs):** Embedding the governing PDE residuals directly into the PyTorch loss function to enforce thermodynamic consistency and conservation laws during training.
* **Non-linear Manifold Learning:** Replacing SVD with Deep Autoencoders for systems with highly advection-dominated or non-separable behaviors.
