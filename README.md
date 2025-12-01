# Delivery Mode Predictor

A Machine Learning-based application for predicting the most suitable delivery mode for a shipment based on key features: region, package weight, package cost, and distance in kilometers. The model outputs recommended delivery mode among: standard, express, same day, or two days.

---

## Project Overview

Delivery Mode Predictor leverages machine learning algorithms to recommend the optimal delivery mode for each shipment:

- **Standard**
- **Express**
- **Same Day**
- **Two Days**

Predictions are based on the following input features:
- **Region:** `east`, `west`, `north`, `south`, `central`
- **Package Weight:** (in kg)
- **Package Cost:** (in currency units)
- **Distance:** (in kilometers)
  
---

## Features

- Predict delivery mode for a given shipment
- Modular and scalable codebase
- REST API & CLI interface
- Training and evaluation scripts
- Logs & monitoring

---

## Installation

### Requirements

- Python 3.8+
- pip
- [See `requirements.txt`](requirements.txt) for dependencies

### Setup

Clone the repository:

```bash
git clone https://github.com/kisharji1/Delivery-Mode-Predictor.git
cd Delivery-Mode-Predictor
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

---

## Usage

### 1. Train a new model

```bash
python train.py --data data/train.csv --model models/model.pkl
```

### 2. Make Predictions (CLI)

```bash
python predict.py --model models/model.pkl --input data/sample_input.csv --output results/predictions.csv
```

### 3. Run API server

```bash
uvicorn app:app --reload
```

#### Example API Request

```bash
curl -X POST "http://localhost:8000/predict" \
     -H "Content-Type: application/json" \
     -d '{
           "region": "east",
           "package_weight": 5.6,
           "package_cost": 1200,
           "distance": 400
         }'
```

---

## Input Data Format

| Feature         | Type   | Description                                 |
|-----------------|--------|---------------------------------------------|
| region          | string | Shipment region: east, west, north, south, central |
| package_weight  | float  | Package weight in kilograms                 |
| package_cost    | float  | Package cost in currency units              |
| distance        | float  | Shipping distance in kilometers             |

---

## Model Details

- Type: Classification (Multi-class)
- Output classes: `standard`, `express`, `same day`, `two days`
- Algorithms: RandomForest, XGBoost, Logistic Regression (configurable)
- Metrics: Accuracy, Precision, Recall, F1-score
- Data: [Describe your dataset]

You can retrain the model with your data using provided scripts.

---

## API Reference

### `POST /predict`

- **Description:** Returns predicted delivery mode for a shipment.
- **Request Body:**
  ```json
  {
    "region": "east",
    "package_weight": 5.6,
    "package_cost": 1200,
    "distance": 400
  }
  ```
- **Response:**
  ```json
  {
    "delivery_mode": "express"
  }
  ```

---

## Example Predictions

| Region  | Package Weight | Package Cost | Distance | Predicted Mode    |
|---------|---------------|--------------|----------|-------------------|
| east    | 5.6           | 1200         | 400      | express           |
| north   | 2.3           | 350          | 25       | same day          |
| west    | 20            | 2200         | 1400     | two days          |
| south   | 1.2           | 100          | 5        | same day          |
| central | 4.5           | 980          | 300      | standard          |

---

_This project is maintained by kisharji1._
