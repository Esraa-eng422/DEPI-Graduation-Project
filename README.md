Depi Sales Forecasting Project
Overview

This project is a sales forecasting system using multiple ML and time series models.
It predicts future sales from historical sales and engineered features.

Features:

Data preprocessing & feature engineering

Model training & evaluation (Random Forest, Gradient Boosting, ARIMA, ETS, LSTM)

MLOps & Deployment with FastAPI & Streamlit

Monitoring & Retraining strategy

Project Structure
depi_sales_forecasting/
│
├── data/
│   ├── sales_train_validation.csv
│   └── sales_enhanced_features.csv
│
├── models/
│   └── final_sales_model.pkl
│
├── notebooks/
│   └── depi_project_notebook_updated.ipynb
│
├── api/
│   └── main.py          # FastAPI app for predictions
│
├── dashboard/
│   └── app.py           # Streamlit dashboard
│
├── monitoring/
│   └── monitoring.json  # Logs prediction errors
│
├── requirements.txt
└── README.md

Installation
# 1. Clone the repository
git clone <REPO_LINK>
cd depi_sales_forecasting

# 2. Create a virtual environment
python -m venv mlops_env

# 3. Activate environment
# Windows
mlops_env\Scripts\activate
# Linux / Mac
source mlops_env/bin/activate

# 4. Install dependencies
pip install -r requirements.txt

Milestone 4: Deployment & MLOps Steps
1. FastAPI API

Navigate to the api/ folder

cd api
uvicorn main:app --reload


Test predictions using POST requests:

{
  "feature1": 23,
  "feature2": 0.5,
  "feature3": 1
}


The API will return predicted sales from the saved ML model.

2. Streamlit Dashboard

Navigate to the dashboard/ folder

cd dashboard
streamlit run app.py


Dashboard shows:

Predicted sales

Upload JSON files for batch predictions

Visualize errors

3. Monitoring

Errors between predicted vs actual are logged in monitoring/monitoring.json:

[
  {"date": "2025-12-01", "actual": 120, "predicted": 115, "error": 5},
  {"date": "2025-12-02", "actual": 80, "predicted": 90, "error": 10}
]


This allows tracking model performance and detecting drift over time.

4. Retraining Strategy

Add new sales data to data/

Run retraining notebook:

jupyter notebook notebooks/depi_project_notebook_updated.ipynb


Save the new model in models/final_sales_model.pkl

Replace the old model in API for updated predictions.

Dependencies

Python 3.11+

pandas, numpy, scikit-learn, tensorflow, statsmodels

joblib

fastapi, uvicorn, streamlit

matplotlib, seaborn

Notes

Ensure JSON input matches feature names used during training

For large datasets, only select features used by the model to avoid errors

Milestone 4 focuses on API, dashboard, monitoring & retraining
