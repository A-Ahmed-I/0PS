# AI Tool Classification (MLOps Project)

**Short description:**
A reproducible MLOps project that analyzes AI tool adoption using feature engineering, clustering, and a neural-network classifier. The repository demonstrates modular code, experiment tracking with MLflow, and data versioning with DVC.

---

## Badges

- **License:** `LICENSE`
- **Python:** Compatible with Python 3.8+

> Add CI / coverage badges here when available (GitHub Actions, Codecov, etc.).

---

## Quick Start — get running in ~5 minutes

### Prerequisites

- Python 3.8+ (recommended using a virtualenv or venv)
- pip
- DVC (optional but recommended for reproducibility)
- MLflow (for experiment tracking)

### Install (recommended)

```bash
# create a venv and activate
python -m venv .venv
source .venv/bin/activate

# install requirements
pip install -r requirements.txt
```

### Retrieve data (if using DVC remote)

```bash
# Pull data artifacts tracked by DVC (requires configured remote)
dvc pull
```

If you do not use DVC remote, ensure `data/raw/ai_adoption_dataset.csv` is present.

### Start MLflow UI (optional)

```bash
mlflow ui --port 5000
# open http://localhost:5000 to view runs and metrics
```

### Run the pipeline

```bash
python src/pipeline/main.py
```

This runs the end-to-end pipeline that:

- loads and validates data,
- engineers features and creates clusters,
- prepares training data,
- trains and evaluates a Keras classifier,
- logs parameters/metrics/artifacts to MLflow,
- saves models under `models/`.

### Run notebooks

Open any notebook in `notebooks/` (e.g., `EDA.ipynb`, `experiments.ipynb`) with Jupyter Lab/Notebook for interactive EDA and prototyping:

```bash
jupyter lab notebooks/
```

---

## Project Overview & Features

- **Modular pipeline**: clear separation of data loading, preprocessing, feature engineering, clustering, and model training.
- **ML models**: TensorFlow/Keras-based neural classifier and clustering for segmentation.
- **MLOps tools**: experiment tracking with MLflow, data/model versioning with DVC.
- **Reproducibility**: pipeline designed to be repeatable and auditable.
- **Visualization**: notebooks and plotting utilities for EDA and results.

---

## Repository Layout

```
.
├── data/
│   ├── raw/                # Raw datasets (e.g., ai_adoption_dataset.csv)
│   └── processed/          # Processed datasets after cleaning/feature engineering
├── log/
│   └── logging.log         # Pipeline and application logs
├── models/                 # Saved models (e.g., model.keras, scaler.joblib)
├── notebooks/
│   ├── EDA.ipynb           # Exploratory Data Analysis notebook
│   ├── experiments.ipynb   # Experiment tracking notebook
│   └── exploratory.ipynb   # Main exploratory notebook
├── reports/
│   └── report_1.txt        # Generated data analysis/model reports
├── src/
│   ├── constant/           # Project-wide constants and configuration
│   ├── data/               # Data loading and validation utilities
│   ├── feature_engineering/# Feature engineering and transformation scripts
│   ├── model/              # Deep learning and ML model definitions
│   ├── pipeline/           # Pipeline orchestration and main scripts
│   ├── preprocessing/      # Data preprocessing and encoding scripts
│   ├── utils/              # Helper functions (saving/loading, splitting, scaling)
│   └── visualization/      # Visualization scripts
├── .dvcignore              # DVC ignore file
├── .gitignore              # Git ignore file
├── LICENSE                 # License file
├── requirements.txt        # Python dependencies
├── setup.py                # Python package setup
└── README.md               # Project documentation
```

Refer to `src/pipeline/pipeline.py` for the main pipeline flow and `src/model/` for model definitions.

---

## Usage Examples

- Run a local training experiment and view metrics in MLflow:

```bash
# (1) Optional: run mlflow ui in another terminal
mlflow ui
# (2) Run the pipeline
python src/pipeline/main.py
# (3) Open MLflow UI and inspect the latest run
```

- To reproduce results using DVC (if dvc pipeline files are present):

```bash
# fetch remote data
dvc pull
# reproduce pipeline (if configured)
dvc repro
```

---

## Development & Contributing

Contributions are welcome. Please:

1. Open an issue to discuss larger changes.
2. Create a branch for your feature/fix.
3. Open a pull request with tests and a clear description.

Style guidelines:

- Keep functions small and well-tested
- Add docstrings to public functions and classes
- Follow PEP8 (use black / flake8 if available)

---

## Tests

There are no automated tests yet. Contributions adding tests (pytest) are highly appreciated.

---

## Troubleshooting & Tips

- If MLflow does not show runs, ensure you're running the UI in the repository root, and that runs are logged to the default `mlruns/` folder.
- If data files are missing, verify `data/raw/ai_adoption_dataset.csv` or run `dvc pull` if you use DVC remotes.

---

## License & Contact

This project is released under the terms in `LICENSE`.

If you have questions or want to collaborate, open an issue or contact the repository owner.
