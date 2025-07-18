# 🧠 Student Exam Performance Predictor

A full-stack Machine Learning project to **predict student math scores** based on demographic and test performance features. This project includes **data analysis, preprocessing, model training with hyperparameter tuning, a Flask web interface**, and **deployment on AWS**.

---

## 📂 Project Structure

```
.
├── src/
│   ├── components/           # Data ingestion, transformation, model trainer
│   ├── pipeline/             # Prediction pipeline and custom input handler
│   ├── exceptions.py         # Custom exception handler
│   ├── logger.py             # Logging setup
│   └── utils.py              # Utilities for saving/loading objects, model evaluation
├── templates/                # HTML templates (index.html, home.html)
├── static/                   # CSS (styles.css)
├── artifacts/                # Model, preprocessor, and data artifacts
├── logs/                     # Log files
├── .ebextensions/            # AWS deployment configs
├── application.py            # Flask app entry point
├── requirements.txt          # Dependencies
├── setup.py                  # Package setup
├── .gitignore
└── README.md                 # Project documentation
```

---

## 🧪 Dataset Used

- **File**: `stud.csv`
- **Records**: 1001 students
- **Features**:
  - `gender`
  - `race/ethnicity`
  - `parental level of education`
  - `lunch`
  - `test preparation course`
  - `reading score`
  - `writing score`
  - **Target**: `math score`

---

## 📊 Exploratory Data Analysis (EDA)

Performed using **Seaborn** and **Matplotlib** on key categorical features.

- 📈 **Bar plots** for categorical distributions
- 🎯 **Pie charts** to show percentage split by category
- 🎻 **Violin plots** to visualize score distributions across categories
- 🔍 **Regplots** to inspect relationships between reading/writing and math scores

EDA covered:
- `parental level of education`
- `race/ethnicity`
- `lunch`
- `test preparation course`
- `gender`

---

## ⚙️ Pipeline Overview

### ✅ 1. **Data Ingestion**
- Loads data from CSV
- Splits into train and test sets
- Saves raw, train, and test data in `artifacts/`

### ✅ 2. **Data Transformation**
- Preprocessing with:
  - `SimpleImputer`
  - `OneHotEncoder`
  - `StandardScaler`
- Saves the preprocessor object (`preprocessor.pkl`)

### ✅ 3. **Model Training**
- Algorithms used:
  - **Linear Regression**
  - **Lasso**
  - **Ridge**
  - **ElasticNet**
  - **K-Nearest Neighbors**
  - **Decision Tree**
  - **Random Forest**
  - **AdaBoost**
  - **Gradient Boosting**
  - **XGBoost**
  - **CatBoost**

- All models were hyperparameter tuned using `RandomizedSearchCV`.

- Best model is selected based on **R² score**.

- Saved as `model.pkl` in the `artifacts/` directory.

---

## 🧠 Prediction Pipeline

- Flask-based web interface for user input.
- Uses `CustomData` class to collect form data and convert it to a Pandas DataFrame.
- `PredictPipeline` loads the preprocessor and model, transforms the input, and returns the prediction.

---

## 🛡️ Error Handling and Logging

- **CustomException Class**:
  - Captures detailed error tracebacks
  - Shows file name and line number
  - Wraps all try/except blocks in custom errors

- **Logger Utility**:
  - Logs all events using Python’s `logging` module
  - Log files are saved in the `logs/` directory
  - Includes timestamps, line numbers, and messages

---

## 🌐 Deployment

✅ Successfully **deployed on AWS Elastic Beanstalk**  
(Terminated afterward to avoid charges)  
Supports `.ebextensions` for environment configuration.

---

## 🚀 How to Run Locally

```bash
# Clone the repository
git clone https://github.com/your-username/student-exam-predictor.git
cd student-exam-predictor

# Create a virtual environment and activate it
conda create -p ./venv python=3.10 -y
conda activate .\venv  # or venv\Scripts\activate on Windows

# Install dependencies
pip install -r requirements.txt

# Run the Flask app
python application.py
```

---

## 🧰 Tech Stack

| Layer              | Technology Used                             |
|--------------------|---------------------------------------------|
| Programming Lang   | Python                                      |
| Libraries/Packages | Pandas, NumPy, Scikit-learn, CatBoost, XGBoost, Dill |
| Visualization      | Matplotlib, Seaborn                         |
| Web Framework      | Flask                                       |
| Deployment         | AWS Elastic Beanstalk                       |
| Environment        | Virtualenv                                  |

---

## 🏆 Highlight Features

- ✅ **Clean ML pipeline**: Data ingestion → preprocessing → training → prediction
- ✅ **Custom Exception Handling**: with detailed traceback info
- ✅ **Logging**: All operations are logged with timestamps and severity
- ✅ **Hyperparameter Tuning**: All models tuned using `RandomizedSearchCV`
- ✅ **Modular Codebase**: Easily maintainable and scalable
- ✅ **Web UI**: User-friendly interface for making predictions
- ✅ **Deployment Ready**: Supports cloud deployment with `.ebextensions`

---
