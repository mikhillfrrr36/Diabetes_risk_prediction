# DiaCare — Healthcare Risk Prediction for Diabetes

A responsive, healthcare-themed web app that predicts diabetes risk from medical attributes.
Everything runs in the browser (HTML + CSS + JavaScript) — no installation or server needed.

## Objective
Develop a predictive model that identifies diabetic patients using medical attributes such as
glucose, BMI, blood pressure, insulin, age and family history (pedigree function).

## Features
- **Dataset options:** built-in sample data (768 patients, Pima-style, synthetic) or **upload your own CSV**
- **Patient ID & Name** columns are detected automatically and shown in the table
- **Three algorithms:** Logistic Regression, K-Nearest Neighbours (k=7), Gaussian Naive Bayes
- **Adjustable train/test split** (10–50%)
- **Evaluation:** Accuracy, Precision, Recall, F1 Score, ROC-AUC, Confusion Matrix, ROC Curve
- **Key risk factors** chart (standardized difference between diabetic and non-diabetic patients)
- **Patient Risk Checker:** adjust values with sliders and see a live risk percentage (Low / Moderate / High)
- **Patient Predictions table** with search, filters and CSV download
- Fully responsive, with light and dark mode

## How to run
Open `index.html` in any modern browser (double-click it). To host it online, upload the
folder to GitHub Pages, Netlify or Render (static site).

## CSV format for upload
- One row per patient, with a header row
- Numeric feature columns (e.g. Pregnancies, Glucose, BloodPressure, SkinThickness, Insulin, BMI,
  DiabetesPedigreeFunction, Age)
- A binary outcome column (0 = non-diabetic, 1 = diabetic). If no column is named
  `Outcome`/`Class`/`Target`/`Label`, the last column is used
- Optional `ID` / `Name` columns
- See `sample_diabetes.csv` for an example

## Methodology
1. **Cleaning:** impossible zeros in Glucose, BloodPressure, SkinThickness, Insulin and BMI are treated
   as missing and replaced with the column median
2. **Split:** random train/test split with a fixed seed
3. **Scaling:** features are standardized using training-set mean and standard deviation
4. **Training:** the chosen model is fitted on the training set
5. **Evaluation:** metrics are computed on the held-out test set (threshold 0.5)
6. **Scoring:** every patient receives a risk probability and a risk level

## Project structure
```
diabetes-risk-prediction/
├── index.html           # complete application (HTML, CSS, JS)
├── sample_diabetes.csv  # sample dataset for testing the upload option
└── README.md
```

## Limitations
- The built-in sample data is **synthetic**; use the real Pima Indians Diabetes dataset for real results
- Models run in the browser and are simple by design
- Results are **not a medical diagnosis** — this is an educational project

## Tech stack
HTML5, CSS3, vanilla JavaScript (no external libraries)
