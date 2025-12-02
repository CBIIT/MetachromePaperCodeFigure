# MetachromePaperCodeFigure

Code and analysis notebooks for generating figures in the Metachrome paper.

## Notebooks

| Notebook | Description |
|----------|-------------|
| `CENPC_Intensity_Analysis.ipynb` | CENP-C intensity analysis across 72h and 96h timepoints |
| `Centromere_intensity.ipynb` | Centromere intensity measurements across experimental groups |
| `Colocalization_Analysis.ipynb` | CENP-C and DNA-FISH colocalization ratio analysis |
| `Model_Performance_Evaluation.ipynb` | Segmentation model performance (precision, recall, F1) |
| `XOR_Visualization.ipynb` | Ground truth vs prediction comparison visualization |
| `analysis_notebook.ipynb` | General data analysis and visualization |

## Quick Start

```bash
# Clone the repository
git clone https://github.com/CBIIT/MetachromePaperCodeFigure.git
cd MetachromePaperCodeFigure

# Create conda environment
conda env create -f environment.yml

# Activate and run
conda activate metachrome
jupyter lab
```

## Requirements

- Python 3.9+
- NumPy, Pandas, Matplotlib
- scikit-image, SciPy, tifffile
- JupyterLab

See [ENVIRONMENT_SETUP.md](ENVIRONMENT_SETUP.md) for detailed installation instructions.

## License

This project is maintained by CBIIT.

