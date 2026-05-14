# Dynamic Model Selection Ensemble Learning for Energy Disaggregation in Agricultural Systems

This repository accompanies the manuscript *Dynamic Model Selection Ensemble Learning for Energy Disaggregation in Agricultural Systems* (Khaleghy, Clifford, Mason, PLOS ONE, under review).

It contains the analysis notebook used in the paper and the photovoltaic inputs for two of the three scenarios in the manuscript.

## Repository layout

```
.
├── notebook.ipynb              Analysis notebook: training, evaluation, ensemble.
├── data/
│   ├── consumption.csv         Hourly farm electricity consumption from the
│   │                           agent based model for the 13 simulated
│   │                           farms, with a timestamp column, a uniform
│   │                           PV reference signal used in Scenario 1, and
│   │                           per farm consumption and net load columns.
│   ├── pv-battery/             SAM photovoltaic plus battery output for the
│   │                           13 simulated farms in Scenario 3, hourly
│   │                           resolution, one CSV per farm
│   │                           (pv-bat1.csv ... pv-bat13.csv).
│   └── dairy-farm-pvs/         SAM photovoltaic output for the 13 simulated
│                               farms with heterogeneous PV capacities used
│                               in Scenario 2, one CSV per farm
│                               (PV1.csv ... PV13.csv).
├── requirements.txt            Python package requirements.
├── CITATION.cff                Machine readable citation.
├── LICENSE                     MIT license for code.
├── LICENSE-DATA                CC BY 4.0 license for data.
└── README.md                   This file.
```

## Contents

- `notebook.ipynb` implements the four base learners (GBRT, 1D CNN, CNN BiLSTM and Transformer) and the dynamic hour wise ensemble selection scheme described in the paper. It also computes the leave one out ablation on the model pool and the statistical validation reported in Section 5 of the manuscript.
- `data/consumption.csv` provides the agent based hourly electricity consumption time series for the 13 simulated dairy farms. It also includes a uniform photovoltaic reference signal used as the generation side in Scenario 1, and per farm net load columns for that scenario.
- `data/pv-battery/` provides the SAM derived photovoltaic plus battery time series for the 13 simulated farms used in Scenario 3 of the paper, the heterogeneous PV with battery storage scenario.
- `data/dairy-farm-pvs/` provides the SAM derived photovoltaic time series for the 13 simulated farms used in Scenario 2, the heterogeneous PV scenario.

## Reproducibility

- Python: tested with Python 3.11.
- Package versions: see `requirements.txt`. Install with `pip install -r requirements.txt` in a fresh environment.
- Hardware: the notebook runs on a CPU only workstation. A GPU is not required. The deep models (1D CNN, CNN BiLSTM, Transformer) each fit in approximately one to two minutes on a recent laptop class CPU, and GBRT in well under a minute.
- Approximate end to end runtime on a CPU only workstation: 10 to 20 minutes for the full notebook including Optuna hyperparameter search (30 trials per model), and under 5 minutes if the Optuna cells are skipped and the hyperparameters reported in Table 4 of the manuscript are used directly.
- Random seed: the notebook fixes a single seed (42) before training so that runs on the same machine are reproducible up to small numerical differences. Cross machine reproducibility of deep learning runs depends on the TensorFlow build and is not guaranteed bit for bit.

## How to use

Open `notebook.ipynb` in JupyterLab, Kaggle, Colab or any compatible environment, point the data loading cells to the `data/pv-battery/` and `data/dairy-farm-pvs/` directories, and run the notebook end to end. The notebook trains the four base learners, evaluates them, builds the dynamic ensemble, and produces the tables and figures used in the manuscript.

## License

- Code: MIT (see `LICENSE`).
- Data: CC BY 4.0 (see `LICENSE-DATA`). When reusing the data, please cite the manuscript.

## Citing this repository

If you use the contents of this repository, please cite the manuscript.

> Khaleghy, H., Clifford, E., Mason, K. Dynamic Model Selection Ensemble Learning for Energy Disaggregation in Agricultural Systems. PLOS ONE (under review).

A machine readable citation is provided in `CITATION.cff` and will appear in the "Cite this repository" button on GitHub.
