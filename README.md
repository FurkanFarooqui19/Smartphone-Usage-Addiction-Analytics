# Smartphone Usage & Addiction Analytics 📱📊

An end-to-end **Python data analytics and machine learning project** analyzing smartphone usage patterns, screen-time behavior, and addiction tendencies across **7,500 users**.

The project explores how smartphone usage relates to behavioral factors such as social media activity, gaming, notifications, sleep, stress, and academic/work impact. It combines **exploratory data analysis, statistical analysis, feature engineering, regression, classification, and preprocessing** to identify important behavioral patterns and risk indicators.

---

## 📌 Project Overview

Smartphone usage has become an important part of everyday life, but excessive usage can potentially affect sleep, stress, productivity, and academic or work performance.

This project investigates:

* How much time users spend on their smartphones
* The relationship between daily and weekend screen time
* Social media and gaming usage patterns
* Smartphone notification and app-opening behavior
* The relationship between smartphone usage and sleep
* Stress levels across different user groups
* Factors associated with addiction tendencies
* Whether smartphone usage can be predicted using other behavioral variables
* Which features are most important when predicting addiction tendencies

The analysis was performed using a dataset containing **7,500 users aged 18–35**.

---

## 🎯 Project Objectives

The main objectives were to:

1. Explore smartphone usage patterns across different demographics.
2. Clean and prepare the dataset for analysis.
3. Identify relationships between screen time, sleep, stress, and other behavioral indicators.
4. Detect unusual or extreme screen-time patterns.
5. Create derived indicators for specific usage behaviors.
6. Build a regression model to predict daily screen time.
7. Build a classification model to predict addiction tendency.
8. Identify the features that contribute most to addiction prediction.
9. Generate actionable insights and recommendations from the analysis.

---

## 📊 Dataset

The dataset contains **7,500 records and 16 original variables**.

### Dataset Characteristics

| Attribute          | Description              |
| ------------------ | ------------------------ |
| Records            | 7,500 users              |
| Age Range          | 18–35 years              |
| Average Age        | 26.57 years              |
| Gender Categories  | Male, Female, Other      |
| Original Variables | 16                       |
| Missing Values     | 819 in `addiction_level` |

### Key Variables

**Demographics**

* `age`
* `gender`

**Smartphone Usage**

* `daily_screen_time_hours`
* `social_media_hours`
* `gaming_hours`
* `work_study_hours`
* `weekend_screen_time`

**Behavioral Activity**

* `notifications_per_day`
* `app_opens_per_day`

**Impact Indicators**

* `sleep_hours`
* `stress_level`
* `academic_work_impact`
* `addiction_level`
* `addicted_label`

---

## 🛠️ Technologies & Tools

### Programming Language

* Python 3

### Data Analysis

* Pandas
* NumPy


### Machine Learning

* Scikit-learn

### Development Environment


* Google Colab


---

## 🔄 Project Workflow

```text
Dataset
   ↓
Data Inspection
   ↓
Data Cleaning
   ↓
Feature Engineering
   ↓
Exploratory Data Analysis
   ↓
Statistical Analysis
   ↓
Regression & Classification
   ↓
Model Evaluation
   ↓
Insights & Recommendations
```

---

## 🔍 Analysis Performed

### 1. Data Exploration

The dataset was initially inspected to understand its structure, variables, data types, and overall characteristics.

Key exploration included:

* Viewing the first and last records
* Checking dataset dimensions
* Calculating average age
* Calculating average daily screen time
* Examining gender distribution
* Filtering users based on social media usage
* Identifying missing values

### Initial Findings

* The average user age was **26.57 years**.
* Average daily smartphone screen time was approximately **7.50 hours**.
* The dataset contained a relatively balanced distribution across gender categories:

  * Male: **2,553**
  * Other: **2,486**
  * Female: **2,461**
* **819 missing values** were identified in `addiction_level`.
* **1,397 users** spent more than 5 hours per day on social media.

---

## 🧹 2. Data Cleaning & Feature Engineering

The missing values in `addiction_level` were handled by replacing them with `"Unknown"`.

A new feature called:

```python
total_app_activity
```

was created by combining:

```text
notifications_per_day + app_opens_per_day
```

Another derived indicator, `weekend_heavy_user`, was created to identify users whose weekend screen time was at least **3 hours higher** than their daily screen time.

### Result

* **11 users** were classified as weekend-heavy users based on the defined rule.

---

## 📈 3. Exploratory Data Analysis

Several relationships between smartphone usage variables were investigated.

### Screen Time & Weekend Usage

A very strong positive correlation was found between:

* `daily_screen_time_hours`
* `weekend_screen_time`

**Correlation: 0.964**

This indicates that users with higher daily screen time also tended to have higher weekend screen time.

### Stress & Screen Time

Average daily screen time was compared across gender and stress-level combinations.

The highest average daily screen time was observed among **male users with high stress**, at approximately:

**7.63 hours per day**

### Stress & Sleep

Average sleep duration was also examined across stress levels:

| Stress Level | Average Sleep |
| ------------ | ------------: |
| High         |    6.70 hours |
| Low          |    6.76 hours |
| Medium       |    6.76 hours |

The differences in average sleep duration across stress groups were relatively small in this dataset.

---

## 🤖 4. Machine Learning

### A. Daily Screen Time Prediction

A **Linear Regression** model was developed to predict `daily_screen_time_hours`.

#### Features Used

* `social_media_hours`
* `gaming_hours`
* `work_study_hours`
* `sleep_hours`
* `notifications_per_day`
* `app_opens_per_day`
* `weekend_screen_time`

#### Result

**R² Score: 0.9273**

The model explained approximately **92.73% of the variation** in daily screen time within the test data.

This indicates a strong predictive relationship between the selected behavioral variables and daily smartphone screen time.

---

### B. Addiction Classification

A **Decision Tree Classifier** was developed to predict the `addicted_label`.

#### Features Used

* `age`
* `daily_screen_time_hours`
* `sleep_hours`

The dataset was divided into:

* **80% training data**
* **20% testing data**

The classifier used a maximum tree depth of 5 to keep the model relatively simple and reduce the risk of overfitting.

#### Result

**Model Accuracy: 79.87%**

The model correctly classified approximately **79.87%** of the test observations.

---

## ⭐ Feature Importance

The Decision Tree model identified the following feature importance scores:

| Feature                   | Importance |
| ------------------------- | ---------: |
| `daily_screen_time_hours` | **97.23%** |
| `sleep_hours`             |      1.87% |
| `age`                     |      0.90% |

### Key Finding

`daily_screen_time_hours` was by far the most influential feature in the classification model, accounting for approximately **97.23% of the model's feature importance**.

This suggests that daily screen time was substantially more informative than age or sleep hours for predicting the addiction label within this dataset.

---

## 🚨 5. Outlier Analysis

The Interquartile Range (IQR) method was used to investigate unusually high or low daily screen-time values.

### Results

* Q1: **5.22 hours**
* Q3: **9.81 hours**
* IQR: **4.59 hours**
* Lower Bound: **-1.67 hours**
* Upper Bound: **16.70 hours**
* Maximum observed daily screen time: **12.00 hours**

### Finding

No statistical outliers were identified in `daily_screen_time_hours` using the IQR method.

Although some users recorded relatively high screen time, the values remained within the calculated IQR boundaries.

---

## 📊 6. Logical Filtering & Behavioral Segmentation

Rule-based filtering was used to identify specific user groups.

One analysis identified users who:

* Had **High stress**
* Had **more than 7 hours of sleep**

### Result

**1,077 users** met both conditions.

This demonstrates how combining multiple behavioral conditions can be used to segment users for deeper analysis.

---

## 📉 7. Weekend Screen-Time Regression

A second Linear Regression model was developed to predict:

```text
weekend_screen_time
```

using:

* `daily_screen_time_hours`
* `age`

### Result

The model produced a:

**Mean Absolute Error (MAE) of 0.64 hours**

This means that the model's predictions were approximately **0.64 hours away from the actual weekend screen-time values on average**.

---

## ⚙️ 8. Data Preprocessing

`StandardScaler` was used to standardize the following numerical variables:

* `age`
* `daily_screen_time_hours`
* `sleep_hours`

The preprocessing step transformed the variables to a standardized scale suitable for machine-learning workflows.

---

# 💡 Key Findings

The analysis produced several important findings:

### 1. Smartphone usage was high

Users spent an average of approximately **7.50 hours per day** on their smartphones.

### 2. Daily and weekend screen time were strongly connected

A correlation of **0.964** was observed between daily and weekend screen time.

### 3. Social media usage was substantial

**1,397 users** spent more than **5 hours per day** on social media.

### 4. Daily screen time was the strongest addiction predictor

The Decision Tree model assigned approximately **97.23% feature importance** to daily screen time.

### 5. Addiction classification achieved 79.87% accuracy

The Decision Tree classifier achieved an accuracy of **79.87%** using age, daily screen time, and sleep hours.

### 6. Daily screen time was highly predictable

The Linear Regression model achieved an **R² score of 0.9273** when predicting daily screen time from other behavioral variables.

### 7. Weekend-heavy usage was relatively uncommon

Only **11 users** had weekend screen time at least 3 hours higher than their daily screen time.

### 8. No statistical outliers were detected

The IQR analysis found no outliers in daily screen time despite some users recording up to **12 hours per day**.

---

# 📌 Business & Practical Insights

Although this is an analytical dataset rather than a business dataset, the findings demonstrate how behavioral data can be converted into actionable insights.

Potential applications include:

* Identifying users with potentially excessive smartphone usage.
* Designing digital wellness interventions.
* Developing screen-time monitoring systems.
* Creating personalized usage recommendations.
* Identifying behavioral patterns associated with addiction tendencies.
* Supporting research into the relationship between technology usage and lifestyle factors.

---

# 💭 Recommendations

Based on the analysis, the following areas could be explored further:

1. **Investigate additional factors affecting sleep quality** beyond total smartphone screen time.

2. **Develop strategies for reducing excessive daily screen time**, particularly for users with high usage patterns.

3. **Explore additional predictors of addiction**, including social media usage, gaming, notifications, app openings, stress, and academic/work impact.

4. **Develop more targeted user segments** based on combinations of screen time, sleep, stress, and social media usage.

5. **Experiment with additional machine-learning algorithms** to determine whether addiction classification accuracy can be improved.

6. **Evaluate the models using additional metrics**, such as precision, recall, F1-score, and confusion matrices.

---



---

# ▶️ How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/smartphone-usage-analytics.git
cd smartphone-usage-analytics
```

### 2. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

Or, if a `requirements.txt` file is included:

```bash
pip install -r requirements.txt
```

### 3. Launch the Notebook

Open:

```text
Smartphone_Usage_Analytics.ipynb
```

You can run the notebook using:

* Jupyter Notebook
* JupyterLab
* VS Code
* Google Colab

### 4. Dataset

Ensure the dataset file:

```text
Smartphone_Usage_And_Addiction_Analysis_7500_Rows.csv
```

is located in the appropriate project directory before running the notebook.

---

# 📚 Skills Demonstrated

This project demonstrates practical experience in:

* Python for Data Analysis
* Pandas
* NumPy
* Data Cleaning
* Exploratory Data Analysis
* Statistical Analysis
* Data Aggregation
* Feature Engineering
* Correlation Analysis
* Outlier Detection
* Data Filtering
* Linear Regression
* Decision Tree Classification
* Feature Importance
* Model Evaluation
* Standardization & Preprocessing
* Data-driven Insight Generation

---

# 👨‍💻 Author

**Destiny Kevin Linus**
**Candace Chijoke-Mba**

Data Analyst | Python | SQL | Power BI | Excel

---

## ⭐ Project Highlights

| Metric                                   |          Result |
| ---------------------------------------- | --------------: |
| Dataset Size                             | **7,500 users** |
| Average Age                              | **26.57 years** |
| Average Daily Screen Time                |  **7.50 hours** |
| Daily vs Weekend Screen Time Correlation |       **0.964** |
| Daily Screen Time Regression R²          |      **0.9273** |
| Addiction Classification Accuracy        |      **79.87%** |
| Daily Screen Time Feature Importance     |      **97.23%** |
| Weekend Screen-Time Regression MAE       |  **0.64 hours** |
| Weekend-Heavy Users                      |          **11** |
| Daily Screen-Time Outliers               |  **0 detected** |

---
