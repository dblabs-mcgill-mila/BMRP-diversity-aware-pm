
#  Diversity-aware Population Modeling (BMRP) Project

# Authors: Nicole Osayande, Danilo Bzdok

This project implements Bayesian Multilevel Regression and Poststratification (BMRP) using PyMC3, with the aim of capturing subgroup-specific differences and making predictions for underrepresented subgroups. The code and data used in this project are based on the Adolescent Brain Cognitive Development (ABCD) study.

## Dependencies

All dependencies required for running the project are listed in the `bmrp_requirements.txt` file. To install them, see the installation instructions below.

## Installation

1. **Set up a Python environment** (recommended to use a virtual environment or `conda`):
   - Using `venv`:
     ```bash
     python3 -m venv bmrp_env
     source bmrp_env/bin/activate   # On Windows, use bmrp_env\Scripts\activate
     ```
   - Using `conda`:
     ```bash
     conda create --name bmrp_env python=3.8
     conda activate bmrp_env
     ```

2. **Install the required dependencies**:
   ```bash
   pip install -r bmrp_requirements.txt
   ```

## Running the Model

The main script to run the BMRP analysis is `model.py`. It includes data preparation, model definition using PyMC3, posterior sampling, and saving the results.

To run the model, use:
```bash
python model.py # replace with specifc filename for 1 of the 14 models 
```

Make sure that the dataset (e.g., `your_dataset.csv`) is available in the `data/` directory or modify the path in the script accordingly.

## Overview of the Workflow

1. **Data Preparation**: The model file will load and preprocess the dataset, including encoding categorical variables, binarizing input variables and unskewing & standardizing the outcome variables.
2. **Model Specification**: Define the Bayesian multilevel model using varying intercepts and slopes for subgroup-specific effects.
3. **Posterior Sampling**: We used Markov Chain Monte Carlo (MCMC) methods to sample from the posterior distribution, please see the Methods section for more details.
4. **Post-Processing**: The posterior samples are saved to generate basic visualizations of the model fit (e.g., trace plots).
5. **Poststratification**: After fitting the model we incorporated US Census SDI data, re-sampled the posterior distribution, then re-weighted the estimates for each subgroup.

## Results

The results of the model (posterior samples) will be saved in the `results/` directory as a NetCDF file (e.g., `bmrp_trace.nc`). Visualization outputs such as trace plots will also be saved in this directory.

## Troubleshooting

- Make sure all dependencies are installed by following the installation steps.
- If using `conda`, ensure the environment is activated with `conda activate bmrp_env` before running the script.
- For any issues with PyMC3 or other dependencies, check the documentation: https://www.pymc.io/projects/docs/en/stable/installation.html.

## License

This project is provided under an open-source license. Feel free to modify and distribute as needed.
