# 🍽️ Tips Prediction ML Model

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?style=for-the-badge&logo=python&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

**A machine learning application that predicts restaurant tip amounts based on customer and meal features — powered by Scikit-Learn and deployed via Streamlit.**

[🚀 Live Demo](#) · [📊 Dataset Info](#dataset) · [⚙️ Installation](#installation) · [📖 Documentation](#model-overview)

</div>

---

## 📌 Table of Contents

- [Overview](#overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Model Overview](#model-overview)
- [Installation](#installation)
- [Usage](#usage)
- [Streamlit App](#streamlit-app)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

---

## 🧠 Overview

This project builds a **regression-based machine learning model** to predict the tip amount a customer will leave at a restaurant. It leverages the classic **Tips dataset** from the Seaborn library, performs exploratory data analysis (EDA), feature engineering, model training, and evaluation — all wrapped in an interactive **Streamlit web app**.

### Key Highlights

- 📈 End-to-end ML pipeline from raw data to deployment
- 🔍 Exploratory Data Analysis (EDA) with visualizations
- 🤖 Multiple regression models compared and evaluated
- 🌐 Interactive Streamlit web app for real-time predictions
- 📦 Clean, modular, and reproducible codebase

---

## 📊 Dataset

The **Tips Dataset** is a well-known dataset that records information about restaurant bills and tips.

| Feature | Type | Description |
|---|---|---|
| `total_bill` | float | Total bill amount (USD) |
| `tip` | float | Tip amount (USD) — **Target Variable** |
| `sex` | categorical | Gender of bill payer (Male/Female) |
| `smoker` | categorical | Whether the table had smokers (Yes/No) |
| `day` | categorical | Day of the week (Thur/Fri/Sat/Sun) |
| `time` | categorical | Meal time (Lunch/Dinner) |
| `size` | int | Number of people at the table |

- **Total Records:** 244 rows
- **Source:** `seaborn.load_dataset('tips')`

---

## 📁 Project Structure

```
tips-prediction/
│
├── 📂 data/
│   └── tips.csv                  # Raw dataset
│
├── 📂 notebooks/
│   └── EDA_and_Modeling.ipynb    # Jupyter notebook for exploration
│
├── 📂 models/
│   └── tips_model.pkl            # Saved trained model
│
├── 📂 src/
│   ├── data_preprocessing.py     # Data cleaning & feature engineering
│   ├── model_training.py         # Model training & evaluation
│   └── predict.py                # Prediction utilities
│
├── app.py                        # Streamlit web application
├── requirements.txt              # Python dependencies
├── .gitignore                    # Git ignore rules
└── README.md                     # Project documentation
```

---

## 🤖 Model Overview

### Pipeline

```
Raw Data → Preprocessing → Feature Engineering → Model Training → Evaluation → Deployment
```

### Preprocessing Steps

1. **Encoding** — Label/One-Hot encoding for categorical variables (`sex`, `smoker`, `day`, `time`)
2. **Feature Scaling** — StandardScaler applied to numerical features
3. **Train-Test Split** — 80% training / 20% testing

### Models Evaluated

| Model | MAE | RMSE | R² Score |
|---|---|---|---|
| Linear Regression | ~0.81 | ~1.02 | ~0.45 |
| Random Forest Regressor | ~0.68 | ~0.89 | ~0.58 |
| Gradient Boosting | ~0.71 | ~0.91 | ~0.56 |
| **Best Model ✅** | **TBD** | **TBD** | **TBD** |

> 📝 Metrics are updated after final training. Run `src/model_training.py` to reproduce results.

---

## ⚙️ Installation

### Prerequisites

- Python 3.8 or higher
- pip / conda

### Clone the Repository

```bash
git clone https://github.com/your-username/tips-prediction.git
cd tips-prediction
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### `requirements.txt` includes:

```
pandas
numpy
scikit-learn
seaborn
matplotlib
streamlit
joblib
plotly
```

---

## 🚀 Usage

### 1. Run EDA & Model Training

```bash
# Train the model and save it
python src/model_training.py
```

### 2. Make a Prediction

```python
from src.predict import predict_tip

result = predict_tip(
    total_bill=25.50,
    sex="Male",
    smoker="No",
    day="Sat",
    time="Dinner",
    size=3
)

print(f"Predicted Tip: ${result:.2f}")
```

---

## 🌐 Streamlit App

### Run Locally

```bash
streamlit run app.py
```

The app will open in your browser at `http://localhost:8501`

### App Features

- 🎛️ **Interactive Sliders & Dropdowns** — Input meal details in real time
- 📊 **Live Prediction** — Instantly see the predicted tip amount
- 📉 **Data Visualizations** — Explore correlations, distributions, and trends
- 📋 **Model Performance Summary** — View key metrics at a glance

### Deployed App

> 🔗 [Click here to access the live Streamlit app](#)
>
> *(Replace `#` with your Streamlit Community Cloud URL after deployment)*

### Deploy to Streamlit Community Cloud

1. Push your code to GitHub
2. Go to [streamlit.io/cloud](https://streamlit.io/cloud) and sign in
3. Click **"New App"** → Select your repository
4. Set **Main file path** to `app.py`
5. Click **Deploy** 🚀

---

## 📈 Results

### Feature Importance

The most impactful features for predicting tip amount:

1. `total_bill` — Strongest predictor of tip
2. `size` — Larger tables tend to leave higher tips
3. `time` — Dinner tips are generally higher than lunch
4. `day` — Weekend dining correlates with higher tips

### Sample Predictions

| Total Bill | Size | Day | Predicted Tip |
|---|---|---|---|
| $15.00 | 2 | Friday | ~$2.20 |
| $35.00 | 4 | Saturday | ~$5.10 |
| $50.00 | 6 | Sunday | ~$7.80 |

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/your-feature-name`
3. **Commit** your changes: `git commit -m "Add: your feature description"`
4. **Push** to the branch: `git push origin feature/your-feature-name`
5. **Open** a Pull Request

Please follow the [Contributor Covenant](https://www.contributor-covenant.org/) code of conduct.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Your Name**

[![GitHub](https://img.shields.io/badge/GitHub-100000?style=flat&logo=github&logoColor=white)](https://github.com/your-username)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/your-profile)
[![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=flat&logo=kaggle&logoColor=white)](https://kaggle.com/your-profile)

---

<div align="center">

⭐ **If you found this project useful, please give it a star!** ⭐

Made with ❤️ and Python

</div>