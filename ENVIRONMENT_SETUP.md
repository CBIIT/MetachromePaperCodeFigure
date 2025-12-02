# Conda Environment Setup Instructions

This guide provides step-by-step instructions for installing Conda, creating a dedicated environment, and running the Jupyter notebooks in this repository.

---

## Table of Contents

1. [Installing Conda](#1-installing-conda)
2. [Creating the Environment](#2-creating-the-environment)
3. [Activating the Environment](#3-activating-the-environment)
4. [Running Jupyter Notebooks](#4-running-jupyter-notebooks)
5. [Quick Reference Commands](#5-quick-reference-commands)
6. [Troubleshooting](#6-troubleshooting)

---

## 1. Installing Conda

### Option A: Miniconda (Recommended - Lightweight)

Miniconda is a minimal installer that includes only Conda and Python.

#### macOS

```bash
# Download Miniconda installer
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh  # For Apple Silicon (M1/M2/M3)
# OR
curl -O https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh  # For Intel Macs

# Run the installer
bash Miniconda3-latest-MacOSX-*.sh

# Follow the prompts:
# - Press ENTER to review the license
# - Type 'yes' to accept the license
# - Press ENTER to confirm the installation location
# - Type 'yes' to initialize Miniconda

# Restart your terminal or run:
source ~/.bashrc  # or ~/.zshrc for zsh users
```

#### Linux

```bash
# Download Miniconda installer
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# Run the installer
bash Miniconda3-latest-Linux-x86_64.sh

# Follow the prompts and restart terminal
source ~/.bashrc
```

#### Windows

1. Download the installer from: https://docs.conda.io/en/latest/miniconda.html
2. Run the `.exe` installer
3. Follow the installation wizard
4. Open "Anaconda Prompt" from the Start Menu

### Option B: Anaconda (Full Distribution)

Anaconda includes Conda, Python, and 250+ pre-installed scientific packages.

Download from: https://www.anaconda.com/download

### Verify Installation

```bash
conda --version
# Should output something like: conda 24.x.x
```

---

## 2. Creating the Environment

### Method 1: Using the Provided `environment.yml` File (Recommended)

```bash
# Navigate to the repository directory
cd /path/to/MetachromePaperCodeFigure

# Create the environment from the yml file
conda env create -f environment.yml

# This will create an environment named 'metachrome'
```

### Method 2: Manual Creation

If you prefer to create the environment manually:

```bash
# Create a new environment with Python 3.9
conda create -n metachrome python=3.9 -y

# Activate the environment
conda activate metachrome

# Install required packages
conda install -c conda-forge numpy pandas matplotlib scikit-image scipy tifffile jupyterlab -y

# Optional: Install additional useful packages
conda install -c conda-forge ipywidgets seaborn -y
```

---

## 3. Activating the Environment

Every time you open a new terminal and want to work with these notebooks, you need to activate the environment:

```bash
# Activate the environment
conda activate metachrome

# Your terminal prompt should change to show (metachrome) at the beginning
# Example: (metachrome) user@computer:~$
```

### Deactivating the Environment

When you're done working:

```bash
conda deactivate
```

---

## 4. Running Jupyter Notebooks

### Option A: JupyterLab (Recommended - Modern Interface)

```bash
# Make sure the environment is activated
conda activate metachrome

# Navigate to the repository
cd /path/to/MetachromePaperCodeFigure

# Start JupyterLab
jupyter lab
```

This will open JupyterLab in your default web browser at `http://localhost:8888`.

### Option B: Classic Jupyter Notebook

```bash
# Make sure the environment is activated
conda activate metachrome

# Navigate to the repository
cd /path/to/MetachromePaperCodeFigure

# Start Jupyter Notebook
jupyter notebook
```

### Option C: VS Code

1. Install the "Jupyter" extension in VS Code
2. Open a `.ipynb` file
3. Click "Select Kernel" in the top-right corner
4. Choose `metachrome` from the list of available kernels

### Option D: Cursor

1. Open a `.ipynb` file in Cursor
2. Select the `metachrome` kernel when prompted

---

## 5. Quick Reference Commands

```bash
# List all conda environments
conda env list

# Activate environment
conda activate metachrome

# Deactivate environment
conda deactivate

# List installed packages in current environment
conda list

# Update all packages in environment
conda update --all

# Remove the environment (if needed)
conda env remove -n metachrome

# Export environment to yml file
conda env export > environment.yml

# Check which Python is being used
which python  # macOS/Linux
where python  # Windows
```

---

## 6. Troubleshooting

### Issue: `conda: command not found`

**Solution:** Conda was not added to your PATH during installation.

```bash
# For bash users
echo 'export PATH="$HOME/miniconda3/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc

# For zsh users (default on newer macOS)
echo 'export PATH="$HOME/miniconda3/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### Issue: Environment not showing in Jupyter kernel list

**Solution:** Register the environment as a Jupyter kernel:

```bash
conda activate metachrome
python -m ipykernel install --user --name metachrome --display-name "Python (metachrome)"
```

### Issue: Package conflicts during installation

**Solution:** Try using mamba (faster and better at resolving conflicts):

```bash
# Install mamba
conda install -c conda-forge mamba -y

# Use mamba instead of conda to install packages
mamba install -c conda-forge numpy pandas matplotlib scikit-image scipy -y
```

### Issue: Slow package resolution

**Solution:** Use libmamba solver:

```bash
conda install -n base conda-libmamba-solver
conda config --set solver libmamba
```

### Issue: Permission errors on Windows

**Solution:** Run Anaconda Prompt as Administrator, or check that your user has write permissions to the conda installation directory.

### Issue: SSL certificate errors

**Solution:**

```bash
conda config --set ssl_verify false  # Not recommended for production
# OR update certificates
conda update ca-certificates
```

---

## Required Packages Summary

| Package | Purpose |
|---------|---------|
| `numpy` | Numerical operations and array handling |
| `pandas` | Data manipulation and analysis |
| `matplotlib` | Plotting and visualization |
| `scikit-image` | Image processing (skimage) |
| `scipy` | Scientific computing, optimization algorithms |
| `tifffile` | Reading/writing TIFF image files |
| `jupyterlab` | Interactive notebook environment |

---

## Notebooks Overview

| Notebook | Description |
|----------|-------------|
| `analysis_notebook.ipynb` | General data analysis and visualization |
| `CENPC_Intensity_Analysis.ipynb` | CENP-C intensity analysis across timepoints |
| `Centromere_intensity.ipynb` | Centromere intensity measurements |
| `Colocalization_Analysis.ipynb` | CENP-C and DNA-FISH colocalization analysis |
| `Model_Performance_Evaluation.ipynb` | Segmentation model performance metrics |
| `XOR_Visualization.ipynb` | Ground truth vs prediction comparison |

---

## Support

If you encounter issues not covered here, please:

1. Check the [Conda documentation](https://docs.conda.io/)
2. Search [Stack Overflow](https://stackoverflow.com/questions/tagged/conda)
3. Open an issue in this repository

---

*Last updated: December 2025*

