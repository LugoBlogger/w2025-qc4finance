# 2025 Quantum Program - Quantum Project 2

Team name: **EntangledBitterGourd**      
Members:
- Henokh Lugo (gst-MlaI21bO5FRYdyD)
- Vinay K (gst-QcL1CBJvvholFTu)
- Rutuja Pable (gst-sOMzNWAzMWkUIOb)


In this project, we solve the bond optimization problem
using Variatonal Quantum Eigensolver algorithm based on 
the work of (Chen, 2023) with some modification. 
The problem that we are going to solve is defined as 
a constrained optimization problem with the following forms

<img src="./images/01-problem-statement.png" width=600>

where $y_{\ell, i}$ are binary variables that determine
whether we include a bond or not into our portfolio.
The other symbols ($\gamma_{\ell, i}$ and $\alpha_{\ell, i}$) are parameters that are defined by the characteristic
of the bonds $i$ and the sector $\ell$. $C$ is a constant.

Alongside with the above formula, there are 19 constraints
that are explained in the detail in the [Slides](#slides) section 

## Installation

The following installation has been tested on Ubuntu 22.04 LTS and with GPU: Nvidia RTX 2060.
`lightning.gpu` only support for compute capability at least 7.0. See this table
to know for the other GeForce/RTX graphic card

1. Run conda environment requirement and installation
   ```
   conda env create -f environment.yml
   ```
   and after that activate the environment with `conda activate womanium2025project`

2. (optional) Install Nvidia CUDA libraries and its runtimes
   ```
   pip install nvidia-cusparse-cu11 nvidia-cublas-cu11 nvidia-cuda-runtime-cu11 custatevec_cu11
   ```

3. (optional) Use CUDA Tensor Network to speed up the computation for number of qubits > 20. 
   ```
   pip install cutensor-cu11
   pip install pennylane-lightning-tensor 
   ```

4. (optional) Use matrix product states with `qml.device("default.tensor")`
   ```
   pip install quimb
   ```

5. Run the notebook `./program/06-run-vqe.ipynb`, to see the result.


## Slides

Please take a look our slide in [here](https://docs.google.com/presentation/d/1bY7O3fusFT1GMOFGxjlAGDBic2viIeRAxoCRcGNsAhU/edit?usp=sharing)

## References

- [(Chen, 2023) - Part 1 and 2 - Portfolio optimization with variational quantum eigensolver (VQE)](https://eric08000800.medium.com/portfolio-optimization-with-variational-quantum-eigensolver-vqe-1-82fd17300b49)

