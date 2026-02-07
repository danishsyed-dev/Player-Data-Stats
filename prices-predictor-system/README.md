# Prices Predictor System

An End-to-End Machine Learning pipeline for price prediction, built using [ZenML](https://zenml.io/) and [MLflow](https://mlflow.org/).

## Project Structure

This project is organized into a modular structure:

- **src/**: Source code for individual steps of the ML pipeline (data ingestion, cleaning, training, evaluation).
- **steps/**: ZenML steps that wrap the source code logic.
- **pipelines/**: Defines the connections between steps to form the complete ML pipeline.
- **data/**: Contains the raw data (e.g., `archive.zip`).
- **tests/**: Unit tests for the codebase.

## Prerequisites

- Python 3.8+
- [ZenML](https://zenml.io/)
- [MLflow](https://mlflow.org/)

## Installation

1. Clone the repository (if you haven't already).
2. Install the required Python packages:

   ```bash
   pip install -r requirements.txt
   ```

3. Install the required ZenML integrations:

   ```bash
   zenml integration install mlflow -y
   ```

## Usage

### 1. Training Pipeline

To run the standard training pipeline (ingestion -> cleaning -> training -> evaluation):

```bash
python run_pipeline.py
```

This will execute the pipeline and log the experiment runs to MLflow.

### 2. Continuous Deployment

To run the continuous deployment pipeline, which trains the model and deploys it if it meets the evaluation criteria:

```bash
python run_deployment.py
```

### 3. Inference

To make predictions using the deployed model (sample script):

```bash
python sample_predict.py
```

## MLflow UI

To inspect your experiment runs and models, start the MLflow UI:

```bash
mlflow ui
```

Then open your browser at `http://127.0.0.1:5000`.

## Features

- **Data Ingestion**: Handles data extraction from zip files.
- **Data Cleaning**: Processes raw data and handles missing values.
- **Feature Engineering**: Transforms raw data into features suitable for training.
- **Model Training**: Trains a regression model (e.g., Linear Regression) using Scikit-Learn.
- **Model Evaluation**: Evaluates the model using R2 score and MSE.
- **MLflow Tracking**: Logs parameters, metrics, and artifacts for every run.
- **Deployment**: Deploys the best model using MLflow Model Deployer.

## License

[MIT](LICENSE)
