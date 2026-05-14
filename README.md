# Dynamic Model Selection Ensemble Learning for Energy Disaggregation in Agricultural Systems

This repository accompanies the manuscript *Dynamic Model Selection Ensemble Learning for Energy Disaggregation in Agricultural Systems* (Khaleghy, Clifford, Mason, 2026, PLOS ONE).

It contains the analysis notebook used in the paper and a subset of the input data on which the experiments are run.

## Repository layout

```
.
├── notebook.ipynb              Analysis notebook: training, evaluation, ensemble.
├── data/
│   ├── pv-battery/             SAM photovoltaic plus battery output for the
│   │                           13 simulated farms in Scenario 3, hourly
│   │                           resolution, one CSV per farm
│   │                           (pv-bat1.csv ... pv-bat13.csv).
│   └── dairy-farm-pvs/         SAM photovoltaic output for the 13 simulated
│                               farms with heterogeneous PV capacities used
│                               in Scenario 2, one CSV per farm
│                               (PV1.csv ... PV14.csv).
├── LICENSE                     MIT for code, CC BY 4.0 for data.
└── README.md                   This file.
```

## Contents

- `notebook.ipynb` implements the four base learners (GBRT, 1D CNN, CNN BiLSTM and Transformer) and the dynamic hour wise ensemble selection scheme described in the paper. It also computes the leave one out ablation on the model pool and the statistical validation reported in Section 5.
- `data/pv-battery/` provides the SAM derived photovoltaic plus battery time series for the 13 simulated farms used in Scenario 3 of the paper, the heterogeneous PV with battery storage scenario.
- `data/dairy-farm-pvs/` provides the SAM derived photovoltaic time series for the 13 simulated farms used in Scenario 2, the heterogeneous PV scenario.

## How to use

Open `notebook.ipynb` in JupyterLab or any compatible environment, point the data paths in the data loading cells to the `data/pv-battery/` and `data/dairy-farm-pvs/` directories, and run the notebook end to end. The notebook trains the four base learners, evaluates them, builds the dynamic ensemble, and produces the tables and figures used in the manuscript.

## License

- Code: MIT.
- Data: CC BY 4.0. When reusing the data, please cite the manuscript.

## Citing this repository

If you use the contents of this repository, please cite the manuscript.

> Khaleghy, H., Clifford, E., Mason, K. (2026). Dynamic Model Selection Ensemble Learning for Energy Disaggregation in Agricultural Systems. PLOS ONE.
