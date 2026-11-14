Bike_Rental_Predict
# 🚲 Bike Rental Prediction Using Machine Learning

## 📌 Project Overview

This project focuses on predicting daily bike rental demand using Machine Learning regression algorithms. The objective is to understand how environmental conditions, seasonal variations, and calendar-related factors influence bike rental demand.

Exploratory Data Analysis (EDA), data preprocessing, feature engineering, model training, cross-validation, and hyperparameter tuning are performed to develop and evaluate predictive models.

## 🎯 Project Objectives

- Perform Exploratory Data Analysis (EDA) to understand bike rental patterns.
- Identify missing values, duplicate records, and outliers.
- Analyze relationships between bike rentals and environmental factors.
- Perform feature selection and feature engineering.
- Apply appropriate data preprocessing techniques.
- Build and compare multiple Machine Learning regression models.
- Evaluate models using MAE, RMSE, and R².
- Perform time-series cross-validation.
- Optimize model hyperparameters using RandomizedSearchCV.
- Select and evaluate a final candidate model.

## 📂 Dataset Description

The project uses two datasets:

- `day.csv` – Daily bike rental records.
- `hour.csv` – Hourly bike rental records.

The main prediction task uses the daily dataset.

**Target Variable:**
- `cnt` – Total number of bike rentals per day.

**Input Features:**

| Feature | Description |
|---|---|
| season | Season of the year |
| yr | Year |
| mnth | Month |
| holiday | Whether the day is a holiday |
| weekday | Day of the week |
| workingday | Whether the day is a working day |
| weathersit | Weather condition |
| temp | Temperature |
| atemp | Feeling temperature |
| hum | Humidity |
| windspeed | Wind speed |
| day_of_month | Day of the month |
| day_of_year | Day of the year |

The `casual` and `registered` columns were excluded from the input features because they are directly related to the target variable `cnt`.

## 🛠️ Technologies and Libraries

- **Programming Language:** Python
- **Data Manipulation:** Pandas, NumPy
- **Data Visualization:** Matplotlib, Seaborn
- **Machine Learning:** Scikit-learn
- **Development Environment:** Jupyter Notebook

## 🔍 Exploratory Data Analysis

The following analyses were performed:

- Dataset structure and statistical summaries.
- Missing value and duplicate record analysis.
- Target variable distribution.
- Numerical and categorical feature distributions.
- Seasonal and monthly rental patterns.
- Working day and holiday comparisons.
- Weather condition analysis.
- Temperature, humidity, and wind speed relationships with bike rentals.
- Hourly rental demand patterns.
- Correlation heatmap and feature relationship analysis.

## ⚙️ Data Preprocessing

The following preprocessing techniques were implemented:

**Numerical Features:**
- Missing value imputation using Median.
- Feature scaling using StandardScaler.

**Categorical Features:**
- Missing value imputation using Most Frequent.
- One-Hot Encoding using OneHotEncoder.

**Additional Processing:**
- ColumnTransformer for applying different preprocessing operations to numerical and categorical features.
- Pipeline to combine preprocessing and model training.
- Chronological train-test split (80% training and 20% testing).

## 🤖 Machine Learning Algorithms

The following regression algorithms were implemented and compared:

1. Dummy Regressor – Baseline model.
2. Linear Regression.
3. Decision Tree Regressor.
4. Random Forest Regressor.
5. Gradient Boosting Regressor.

## 📊 Model Evaluation Metrics

The models were evaluated using:

- **MAE (Mean Absolute Error):** Measures the average absolute difference between actual and predicted values.
- **RMSE (Root Mean Squared Error):** Measures prediction error while penalizing larger errors more heavily.
- **R² Score:** Measures how much variation in the target variable is explained by the model.

A lower MAE and RMSE and a higher R² score are generally preferred.

## 🔄 Cross-Validation and Hyperparameter Tuning

- Implemented `TimeSeriesSplit` with 5 splits to preserve chronological order during validation.
- Used `cross_validate()` to compare candidate models using MAE, RMSE, and R².
- Applied `RandomizedSearchCV` to optimize Random Forest hyperparameters.
- Compared the tuned Random Forest with the other candidate models.
- Selected the final candidate based on cross-validation RMSE.

## 🏆 Final Model Results

The final cross-validation comparison selected **Linear Regression**.

Its chronological holdout test performance was:

| Evaluation Metric | Result |
|---|---:|
| MAE | 786.21 |
| RMSE | 1106.35 |
| R² Score | 0.6517 |

### Model Comparison on the Test Dataset

| Model | MAE | RMSE | R² Score |
|---|---:|---:|---:|
| Gradient Boosting | 757.91 | 943.69 | 0.7466 |
| Linear Regression | 786.21 | 1106.35 | 0.6517 |
| Tuned Random Forest | 914.61 | 1121.33 | 0.6422 |
| Decision Tree | 1265.44 | 1635.15 | 0.2392 |

**Note:** Linear Regression was selected based on the lowest average cross-validation RMSE. Gradient Boosting achieved better results on the particular chronological holdout test set. This difference highlights the importance of checking model stability across different time periods before deployment.

## 🚀 Prediction Function

A custom Python function, `predict_daily_rentals()`, was developed to predict daily bike rental demand using:

- Date
- Season
- Holiday
- Working day
- Weather situation
- Temperature
- Feeling temperature
- Humidity
- Wind speed

The function generates a predicted daily bike rental count using the trained final model.

## 📁 Project Structure

```text
Bike-Rental-Prediction/
│
├── Bike_Rental.ipynb
├── day.csv
├── hour.csv
└── README.md
```

## ▶️ How to Run the Project

**1. Clone the repository**

```bash
git clone https://github.com/your-username/Bike-Rental-Prediction.git
```

**2. Navigate to the project directory**

```bash
cd Bike-Rental-Prediction
```

**3. Install the required libraries**

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

**4. Launch Jupyter Notebook**

```bash
jupyter notebook
```

**5. Open and execute `Bike_Rental.ipynb`**

Make sure `day.csv` and `hour.csv` are available in the project directory.

## 💡 Key Learnings

- Understanding real-world regression problems.
- Performing Exploratory Data Analysis.
- Handling numerical and categorical features.
- Preventing target leakage.
- Building Scikit-learn preprocessing pipelines.
- Comparing multiple regression algorithms.
- Implementing time-series cross-validation.
- Performing hyperparameter optimization.
- Evaluating model performance on unseen data.
- Developing a reusable prediction function.

## 🔮 Future Improvements

- Incorporate additional historical rental data.
- Integrate real-time and weather forecast information.
- Explore additional time-series forecasting approaches.
- Perform external validation on more recent data.
- Develop a user-friendly prediction application.
- Implement model monitoring and periodic retraining.

## 👨‍💻 Author

**Shaik Mahammad Rizwan**

B.Tech – Computer Science and Engineering (AIML)

GitHub: [Add your GitHub Profile Link](https://github.com/)

---

*This project demonstrates an end-to-end Machine Learning regression workflow for estimating daily bike rental demand.*
