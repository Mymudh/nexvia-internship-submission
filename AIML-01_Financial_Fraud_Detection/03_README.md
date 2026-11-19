# Financial Fraud Detection Platform

## Overview
A transaction-risk analysis prototype that combines a React dashboard, FastAPI service and machine-learning workflow. The repository includes XGBoost/scikit-learn training and prediction code, feature engineering, monitoring artifacts and supporting integration modules.

## Links
- GitHub: https://github.com/Mymudh/financial-fraud-detection
- Frontend: https://financial-fraud-detection-nu.vercel.app/
- Dataset reference: https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
- API: Confirm the public Render service URL in the Render service settings. The Render dashboard-management URL is not an API URL.

## Technology
Python, XGBoost/scikit-learn, FastAPI, React, Vite, Kafka, Feast, MLflow, PyTorch Geometric, Evidently, Docker and Kubernetes manifests. External services must be independently configured and tested.

## Main modules
- Transaction prediction API (`backend/main.py`)
- Training and feature engineering (`ml/`)
- React dashboard (`frontend/`)
- Feature store (`feature_store/`)
- Kafka producer/consumer (`backend/`)
- Drift monitoring and retraining scripts (`ml/`)
- Evaluation artifacts (`artifacts/`)

## Recorded model evaluation
The repository artifact reports 227,845 training rows and 56,962 test rows, 30 input features, ROC-AUC 0.9807536, average precision 0.8741371, accuracy 0.9993329, fraud precision 0.7727, recall 0.8673 and F1 0.8173 at threshold 0.50. These are saved artifact values, not a fresh production benchmark.

## Run locally
Use Python 3.11 if compatible with the pinned dependencies. From the repository root:
```powershell
python -m venv .venv
.venv\Scripts\activate
python -m pip install -r requirements.txt
```
Start the API using the command specified by the repository configuration (commonly `uvicorn backend.main:app --reload`). In a second terminal:
```powershell
cd frontend
npm install
npm run dev
```
Check `backend/main.py`, `.env.example` and the root README for exact environment variables and service dependencies. Do not commit `.env`, API keys or credentials.

## API
FastAPI routes include GET `/`, GET `/health`, GET `/features/{transaction_id}`, POST `/predict`, and POST `/predict/{transaction_id}`. Open `/docs` locally after starting the API.

## Important verification status
The supplied UI screenshots include a Model Information panel showing the model as **Unavailable**. Confirm `artifacts/fraud_model.joblib` exists and loads, then test `/health` and `/predict`. Kafka, Feast, MLflow, GNN, drift monitoring, Docker and Kubernetes require separate end-to-end verification. Do not describe them as production-operational without evidence.

## Evidence
See `08_Testing_Screenshots/`, `09_Demo_Video/`, and the PDF reports in this submission folder. Screenshots show UI states only; they do not independently prove live inference.
