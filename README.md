# 📊 Credit Risk Prediction System

A production-ready machine learning application that predicts credit
risk and serves predictions via a RESTful Flask API.

------------------------------------------------------------------------

## 📌 Overview

This project delivers an end-to-end pipeline:

-   Data preprocessing & feature engineering\
-   Model training and evaluation\
-   Model serialization (`.bin`)\
-   REST API for real-time inference\
-   Modular utilities for reuse

------------------------------------------------------------------------

## 🏗️ Architecture

    Client (Postman / App)
            │
            ▼
       Flask API (app.py)
            │
            ▼
     Data Preprocessing (utils/)
            │
            ▼
      Trained Model (.bin)
            │
            ▼
     Prediction Output (JSON)

------------------------------------------------------------------------

## 📂 Project Structure

    KM_CreditRisk_Prediction/
    ├── KM_Flask.ipynb                                        # Flask API
    ├── KM_model_CreditRisk=1.0.bin                           # Serialized model
    │── Khosara_Smey_Project_CreditRiskPrediction.ipynb       # notebooks
    |── KM_Client.ipynb                                       # Result
    |── README.md

------------------------------------------------------------------------

## 🧰 Prerequisites

-   Python 3.8+
-   pip
-   virtualenv / venv

------------------------------------------------------------------------

## ⚙️ Installation

``` bash
git clone <your-repo-url>
cd KM_CreditRisk_Prediction

python -m venv venv
source venv/bin/activate   # Windows: venv\Scripts\activate

pip install -r requirements.txt
```

------------------------------------------------------------------------

## 🚀 Running the Application

``` bash
python app.py
```

Server runs at:

    http://127.0.0.1:5000/

------------------------------------------------------------------------

## 🔌 API Endpoints

### 1. Health Check

    GET /ping

**Response**

``` json
"pong"
```

------------------------------------------------------------------------

### 2. Predict Credit Risk

    POST /predict

**Request Example**

``` json
{
  "age": 35,
  "income": 5000,
  "loan_amount": 20000
}
```

**Response Example**

``` json
{
  "credit_risk": "low",
  "probability": 0.87
}
```

------------------------------------------------------------------------

## 🧪 Testing

### Using cURL

``` bash
curl -X POST http://127.0.0.1:5000/predict \
-H "Content-Type: application/json" \
-d '{"age": 35, "income": 5000, "loan_amount": 20000}'
```

### Using Postman

1.  Set method to **POST**
2.  URL: `http://127.0.0.1:5000/predict`
3.  Body → JSON
4.  Send request

------------------------------------------------------------------------

## 📊 Model Details

-   Algorithm: (e.g., Logistic Regression / Random Forest)
-   Input: Customer financial features\
-   Output: Risk classification + probability

------------------------------------------------------------------------

## 🔄 Updating the Model

Replace model file:

    KM_model_CreditRisk=1.0.bin

Ensure compatibility:

``` python
dv, model = pickle.load(f)
```

Restart server after updating.

------------------------------------------------------------------------

## 🛠️ Troubleshooting

  Issue               Solution
  ------------------- ---------------------
  Module not found    Install via pip
  Model not loading   Check file path
  Flask not running   Check port / env
  Import errors       Verify utils folder

------------------------------------------------------------------------

## 📦 Deployment

### Gunicorn

``` bash
pip install gunicorn
gunicorn app:app
```

------------------------------------------------------------------------

### Docker (Optional)

``` dockerfile
FROM python:3.10
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
```

------------------------------------------------------------------------

## 🚀 Future Improvements

-   Add frontend UI\
-   Deploy to cloud (AWS / GCP / Azure)\
-   Add model monitoring\
-   Improve feature engineering

------------------------------------------------------------------------

## 🤝 Contributing

Pull requests are welcome. For major changes, open an issue first.

------------------------------------------------------------------------

## 📬 Contact

For support or questions, reach out to the project maintainer.
