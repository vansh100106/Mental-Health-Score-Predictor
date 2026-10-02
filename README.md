# 🧠 Mental Health Score Predictor

A machine learning-based web application that predicts a **Mental Health Score** based on demographic, academic, social-media, lifestyle, and stress-related factors.

The project uses a **Random Forest Regressor** for prediction, with a **Scikit-learn preprocessing pipeline**, **FastAPI** backend, and an interactive **HTML, CSS, and JavaScript** frontend.

> **Disclaimer:** This project is developed for educational and informational purposes only. It is not a medical diagnostic or clinical assessment tool.

---

## 📌 About the Project

The **Mental Health Score Predictor** analyzes different aspects of a student's daily routine and digital habits to estimate their mental health score.

Users provide information such as age, academic level, social-media usage, study hours, physical activity, sleep duration, and perceived stress level. This information is processed by the trained machine learning model, which generates a predicted score.

The prediction is displayed through an interactive web interface with a score gauge and signal category.

---

## ✨ Features

* Predicts mental health score on a **0–10 scale**
* Machine learning-based prediction using **Random Forest Regression**
* FastAPI REST API for model inference
* Interactive web-based user interface
* Client-side and server-side input validation
* Numerical and categorical feature preprocessing
* Automatic country grouping for less frequent countries
* Visual score gauge for prediction results
* Loading, error, and reset states
* Saved trained model using Joblib
* Responsive frontend design

---

## 🛠️ Technologies Used

### Machine Learning

* Python
* Pandas
* NumPy
* Scikit-learn
* Joblib

### Backend

* FastAPI
* Pydantic
* Uvicorn

### Frontend

* HTML5
* CSS3
* JavaScript
* SVG

---

## 📊 Dataset

The project uses the **Student Social Media And Mental Health Impact** dataset.

The model uses the following features:

* Age
* Gender
* Country
* Academic Level
* Most Used Platform
* Purpose of Use
* Average Daily Usage Hours
* Daily Phone Unlocks
* Study Hours
* Physical Activity Hours
* Sleep Hours Per Night
* Stress Level

### Target Variable

```text
Mental_Health_Score
```

The target is used to train the regression model and generate the predicted mental health score.

---

## 🤖 Machine Learning Model

The primary model used in the project is:

**Random Forest Regressor**

```python
RandomForestRegressor(random_state=42)
```

The model is implemented together with a preprocessing pipeline so that the same transformations are applied during both training and prediction.

### Preprocessing

Different preprocessing techniques are applied according to the feature type.

**Numerical features**

Standardized using `StandardScaler`:

* Age
* Average Daily Usage Hours
* Daily Unlocks
* Physical Activity Hours
* Sleep Hours Per Night

**Study Hours**

Study hours are processed using:

```text
Log Transformation → Standard Scaling
```

**Stress Level**

Stress level is treated as an ordinal feature:

```text
Low → Medium → High → Very High
```

and encoded using `OrdinalEncoder`.

**Categorical features**

The following features are encoded using `OneHotEncoder`:

* Gender
* Academic Level
* Most Used Platform
* Purpose of Use
* Grouped Country

Unknown categorical values are handled using:

```python
OneHotEncoder(handle_unknown="ignore")
```

---

## 📈 Model Performance

The project evaluates multiple regression approaches, including Linear Regression and Random Forest Regression.

The Random Forest model achieved approximately:

```text
R² Score : 0.88
MAE      : 0.35
RMSE     : 0.46
```

on the test data used during model evaluation.

The project also includes hyperparameter tuning using `RandomizedSearchCV` with cross-validation.

---

## 🔄 Machine Learning Workflow

```text
Dataset
   ↓
Data Preprocessing
   ↓
Feature Engineering
   ↓
Train-Test Split
   ↓
Feature Transformation
   ↓
Model Training
   ↓
Model Evaluation
   ↓
Model Serialization
   ↓
FastAPI Backend
   ↓
Web Interface
   ↓
Prediction
```

The trained preprocessing pipeline and Random Forest model are saved using **Joblib**.

---

## 🌐 FastAPI Backend

The backend is developed using **FastAPI** and provides endpoints for interacting with the machine learning model.

### API Endpoints

| Method | Endpoint   | Description                                |
| ------ | ---------- | ------------------------------------------ |
| GET    | `/`        | Returns API welcome message                |
| GET    | `/health`  | Checks API status                          |
| POST   | `/predict` | Generates a mental health score prediction |

### Prediction Endpoint

The `/predict` endpoint accepts student information and returns the predicted mental health score.

Example response:

```json
{
    "predicted_mental_health_score": 6.82
}
```

The prediction is rounded to two decimal places before being returned.

---

## 🖥️ Frontend

The frontend is built using HTML, CSS, and JavaScript.

The interface collects the required information in three sections:

### Profile

* Age
* Gender
* Country

### Academic & Digital Habits

* Academic Level
* Most Used Platform
* Primary Purpose
* Average Daily Screen Time
* Daily Phone Unlocks

### Lifestyle & Stress

* Study Hours
* Physical Activity
* Sleep Duration
* Perceived Stress Level

After submission, JavaScript sends the data to the FastAPI `/predict` endpoint and displays the returned prediction.

---

## 📂 Project Structure

```text
Mental-Health-Score-Predictor/
│
├── index.html
├── style.css
├── script.js
├── main.py
│
├── Mental_Health_Model.pkl
├── Student Social Media And Mental Health Impact.csv
├── Mental_Health_Score_Predictor.ipynb
│
└── README.md
```

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/mental-health-score-predictor.git
```

### 2. Navigate to the project

```bash
cd mental-health-score-predictor
```

### 3. Install dependencies

```bash
pip install fastapi uvicorn pandas numpy scikit-learn joblib pydantic
```

---

## ▶️ Running the Project

Start the FastAPI backend:

```bash
uvicorn main:app --port 2200
```

The API will run at:

```text
http://127.0.0.1:2200
```

Then open `index.html` in your browser.

The frontend communicates with the backend through:

```text
POST http://127.0.0.1:2200/predict
```

---

## 🔐 Input Validation

The application validates user inputs on both the frontend and backend.

Examples include:

* Age: 10–100
* Daily usage hours: 0–24
* Study hours: 0–24
* Physical activity: 0–24
* Sleep hours: 0–24
* Daily unlocks: 0 or more
* Required categorical fields
* Required stress level

FastAPI and Pydantic provide server-side validation, while JavaScript performs additional validation before sending the request.

---

## 📓 Jupyter Notebook

The project includes a Jupyter Notebook containing the machine learning development process, including:

* Dataset analysis
* Data preprocessing
* Feature transformation
* Train-test splitting
* Model training
* Linear Regression
* Random Forest Regression
* Hyperparameter tuning
* Model evaluation
* Model comparison
* Model saving

---

## 🔮 Future Improvements

* Deploy the application online
* Add additional machine learning models
* Improve hyperparameter optimization
* Add feature-importance analysis
* Add model explainability
* Add prediction history
* Improve accessibility and UI
* Add automated model monitoring

---

## ⚠️ Disclaimer

The predicted score is generated by a machine learning model based on the provided dataset and user inputs.

It should **not be interpreted as a medical diagnosis, psychological evaluation, or clinical assessment**. Mental health is complex and cannot be fully determined from the factors used by this application.

---

## 👨‍💻 Author

**Vansh**
B.Tech Information Technology Student
