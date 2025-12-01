Delivery Mode Prediction – Flask App

A simple Flask web application that predicts the Mode of Delivery (Standard, Express, Economy, etc.) using a trained RandomForestClassifier machine-learning model.
The model analyzes Region, Package Weight, Delivery Cost, and Distance to determine the best delivery mode.

Features

Predict delivery mode using a trained RandomForestClassifier

Takes Region, Weight, Cost, and Distance as input

Flask-based web interface for easy interaction

Saves the trained model as a .pkl file

Simple and clean HTML front-end

Easy to extend with real logistics datasets

Project Structure
delivery-mode-prediction/
│
├── app.py                 # Flask web app
├── model_train.py         # Training script for RandomForest model
├── requirements.txt       # App dependencies
│
├── model/
│   └── delivery_rf_model.pkl   # Saved ML model
│
└── templates/
    └── index.html         # Front-end form UI

Installation
1. Clone the Repository
git clone https://github.com/your-username/delivery-mode-prediction.git
cd delivery-mode-prediction

2. Install Dependencies
pip install -r requirements.txt

3. (Optional) Train the Model
python model_train.py


This will generate delivery_rf_model.pkl inside the model/ directory.

Running the Application

Run the Flask app:

python app.py


Visit in browser:

http://127.0.0.1:5000


Enter the package details and click Predict Mode to view the result.

Model Training

The model is a RandomForestClassifier trained on custom logistic parameters:

model = RandomForestClassifier()
model.fit(X, y)
pickle.dump(model, open("model/delivery_rf_model.pkl", "wb"))


Replace the sample dataset with your own logistics dataset for improved accuracy.

Technologies Used

Python 3

Flask

Scikit-learn

Pandas

HTML / CSS
