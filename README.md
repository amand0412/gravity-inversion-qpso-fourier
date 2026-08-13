# Sedimentary Basin Depth Estimation from Gravity Data using QPSO

This repository contains the MATLAB implementation of a **Quantum-behaved Particle Swarm Optimization (QPSO)** based approach for estimating sedimentary basin basement depth from gravity anomaly data. It provides the computational framework for investigating gravity inversion using **Fourier parameterization, adaptive Fourier coefficient selection, and constant- and variable-density gravity forward modelling**.

## 📖 Description

Estimating the basement depth of sedimentary basins from gravity anomalies is a nonlinear and non-unique geophysical inverse problem. This work implements a **QPSO-based gravity inversion approach** for recovering sedimentary basin geometry from gravity data using a reduced Fourier parameterization.

The implementation investigates two synthetic basin models:

1. Constant-Density Basin Model: A synthetic basin with a constant density contrast of -800 kg/m³, where the basement geometry is estimated from its gravity anomaly.
2. Variable-Density Basin Model: A synthetic basin incorporating a depth-dependent density contrast based on an exponential compaction relationship.

The primary goal is to evaluate the capability of QPSO for gravity inversion, while reducing the number of inversion parameters through Fourier representation and automatically selecting the required number of Fourier coefficients based on spectral energy and reconstruction error.

Key Features:

* Implementation of Quantum-behaved Particle Swarm Optimization (QPSO) for gravity inversion
* Fourier-based parameterization of sedimentary basin depth
* Automatic Fourier coefficient selection using spectral energy and reconstruction-error criteria
* Constant-density and depth-dependent variable-density gravity forward modelling
* Legendre-Gauss quadrature for numerical integration
* Physical depth constraints during optimization
* Multiple independent QPSO runs for inversion analysis
* Gravity and basement-depth RMSE evaluation
* PCA-based analysis of low-misfit/equivalent inversion models
* Synthetic basin models for testing and evaluation

## 🚀 Installation & Setup

### 1. Clone the Repository

```bash
git clone <YOUR-GITHUB-REPOSITORY-URL>
cd <YOUR-REPOSITORY-NAME>
```

### 2. MATLAB Requirement

This repository is implemented in **MATLAB** using MATLAB Live Scripts (`.mlx`).

A recent MATLAB version is recommended.

No Python environment or external Python dependencies are required.

### 3. Add Files to MATLAB Path

Open MATLAB in the repository directory or add the repository and its subdirectories to the MATLAB path:

```matlab
addpath(genpath(pwd));
```

## 📁 Repository Structure

```text
.
├── model_1_synthetic.mlx
│   └── Constant-density synthetic basin model,
│       Fourier analysis, adaptive coefficient selection,
│       QPSO inversion, RMSE and PCA analysis
│
├── model_2_synthetic.mlx
│   └── Variable-density synthetic basin model,
│       Fourier analysis, adaptive coefficient selection,
│       QPSO inversion, RMSE and PCA analysis
│
├── QPSO.mlx
│   └── Quantum-behaved Particle Swarm Optimization implementation
│
├── constant_density_gravity.mlx
│   └── Constant-density gravity forward modelling
│
├── variable_density_gravity.mlx
│   └── Variable-density gravity forward modelling
│
├── lgwt.mlx
│   └── Legendre-Gauss quadrature implementation
│
├── pca_reduction.mlx
│   └── PCA-based model reduction and
│       inversion-equivalence analysis
│
└── README.md
    └── This file
```

## 🔬 Methodology

The complete inversion workflow consists of the following steps:

1. Generate synthetic sedimentary basin depth models.
2. Calculate gravity anomalies using constant- or variable-density forward modelling.
3. Represent the basin geometry using a Fourier series.
4. Automatically determine the required Fourier coefficients using spectral energy and reconstruction error.
5. Estimate the Fourier coefficients using QPSO.
6. Reconstruct the basement depth from the optimized Fourier coefficients.
7. Calculate gravity and depth RMSE to evaluate the inversion.
8. Analyse the distribution of low-misfit inversion models using PCA.

## ⚙️ Main Parameters

The principal parameters used in the QPSO inversion include:

```text
Fourier energy threshold       = 99%
Maximum Fourier coefficients   = 51
QPSO contraction coefficient   = 0.75
Population size                = 100
Maximum iterations             = 300
Independent QPSO runs          = 5
Parameter search range         = [-1000, 1000]
Depth constraint               = 0–6000 m
Penalty coefficient            = 1000
Quadrature points              = 10
```

The number of Fourier coefficients is selected automatically rather than being fixed manually for every inversion.

## 🔧 Running the Synthetic Models

### 1. Run the Constant-Density Model

Open:

```text
model_1_synthetic.mlx
```

and run the Live Script in MATLAB.

This experiment generates a synthetic basin with a constant density contrast of:

```text
Δρ = -800 kg/m³
```

The script performs Fourier analysis, adaptive coefficient selection, QPSO inversion, forward modelling, RMSE calculation, and PCA-based analysis.

### 2. Run the Variable-Density Model

Open:

```text
model_2_synthetic.mlx
```

and run the Live Script.

The variable-density model uses the depth-dependent density relationship:

```matlab
rho(z) = (-0.38 - 0.42*exp(-0.5*z*10^-3))*1000;
```

The script performs the same overall inversion workflow using the variable-density gravity forward model.

## 📊 Outputs

The scripts generate diagnostic and inversion results including:

* Fourier amplitude spectra
* Automatically selected Fourier coefficients
* Synthetic and reconstructed gravity anomalies
* True and inverted basement depth profiles
* Gravity RMSE
* Basement-depth RMSE
* QPSO convergence behaviour
* PCA-based low-misfit model analysis

The results can be used to evaluate the accuracy and stability of the QPSO-based gravity inversion.

## 🙏 Acknowledgments

* The Legendre-Gauss quadrature implementation is based on the `lgwt` routine by **Greg von Winckel (2004)**.
* The gravity forward modelling follows the polygonal gravity formulation implemented in the provided MATLAB routines.
* MATLAB's built-in `peaks` function is used for generating synthetic basin geometries.

## 📄 License

A specific license has not yet been included with the current repository.

If the repository is released publicly, an appropriate `LICENSE` file should be added.

---

## ⚠️ Important Notes for Users

1. **MATLAB Live Scripts:**
   The main implementation is provided as `.mlx` MATLAB Live Scripts.

2. **File Path:**
   Ensure that all supporting files are available in the MATLAB path before running the synthetic models.

3. **Computational Requirements:**
   QPSO performs multiple independent optimization runs with a population of particles and repeated gravity forward calculations. Therefore, execution time depends on the available computational resources.

4. **Depth Constraints:**
   The inverted basement depth is constrained to:

   ```text
   0–6000 m
   ```

5. Noise Configuration:
   Model-1 currently uses a noise-free synthetic gravity response, while Model-2 includes Gaussian noise with a standard deviation of approximately 0.5 mGal.

6. Randomness:
   QPSO initialization and synthetic noise generation involve random numbers. For exactly reproducible results, a fixed MATLAB random seed can be specified before running the experiments.

## 🔗 Related Resources

The implementation uses the following computational components:

* Quantum-behaved Particle Swarm Optimization (QPSO)
* Fourier spectral representation
* Constant-density gravity forward modelling
* Variable-density gravity forward modelling
* Legendre-Gauss quadrature
* Principal Component Analysis (PCA)

## 📚 Citation

If you use this repository in your research, please cite the associated research publication.

### BibTeX

```bibtex
@article{<AUTHOR_YEAR>,
  title={<ARTICLE TITLE>},
  author={<AUTHORS>},
  journal={<JOURNAL>},
  year={<YEAR>},
  doi={<DOI>}
}
```

> **Note:** Replace the placeholder citation information with the final bibliographic details of the associated QPSO research paper before publishing the repository.
